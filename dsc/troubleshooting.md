# Résolution des problèmes liés à DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cette rubrique décrit des méthodes pour que vos scripts de configuration d’état souhaité (DSC) s’exécutent sans erreur. Si vous utilisez les journaux de manière efficace pour détecter les erreurs et que vous comprenez comment recycler le cache pour afficher les résultats immédiats des modifications que vous apportez aux ressources, vous pouvez résoudre plus efficacement les problèmes liés à DSC. Ces techniques sont présentées dans deux sections :

* Mon script ne s’exécute pas : **utilisation des journaux DSC pour diagnostiquer les erreurs de script**
* Mes ressources ne sont pas mises à jour : **comment réinitialiser le cache**

## Mon script ne s’exécute pas : utilisation des journaux DSC pour diagnostiquer les erreurs de script

Comme tous les logiciels Windows, DSC enregistre les erreurs et les événements dans des [journaux](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) qui peuvent être consultés dans l’[Observateur d’événements](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). L’examen de ces journaux peut vous aider à comprendre pourquoi une opération particulière a échoué et comment éviter que cela se reproduise. L’écriture de scripts de configuration peut être compliquée. Ainsi, pour faciliter le suivi des erreurs pendant le processus de création, utilisez la ressource Log dans DSC pour suivre la progression de votre configuration dans le journal des événements d’analyse DSC.

## Où se trouvent les journaux des événements DSC ?

Dans l’Observateur d’événements, les événements DSC se trouvent dans : **Journaux des applications et des services/Microsoft/Windows/Desired State Configuration**

L’applet de commande PowerShell correspondante [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx) peut également être exécutée pour afficher les journaux des événements :

```
PS C:\Users> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Comme indiqué ci-dessus, le nom du journal DSC principal est **Microsoft->Windows->DSC** (les autres noms de journal sous Windows ne sont pas cités ici, par souci de concision). Le nom principal est ajouté au nom du canal pour créer le nom complet du journal. Le moteur DSC écrit principalement dans trois types de journaux : [journaux des opérations, d’analyse et de débogage](https://technet.microsoft.com/library/cc722404.aspx). Les journaux d’analyse et de débogage étant désactivés par défaut, vous devez les activer dans l’Observateur d’événements. Pour ce faire, ouvrez l’Observateur d’événements en tapant eventvwr dans Windows PowerShell ou cliquez sur le bouton **Démarrer**, sur **Panneau de configuration**, **Outils d’administration**, puis **Observateur d’événements**. Dans le menu **Affichage** de l’Observateur d’événements, cliquez sur **Afficher les journaux d’analyse et de débogage**. Le nom du journal du canal d’analyse est **Microsoft-Windows-Dsc/Analytic** et celui du canal de débogage est **Microsoft-Windows-Dsc/Debug**. Vous pouvez également utiliser l’utilitaire [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) pour activer les journaux, comme l’illustre l’exemple suivant.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## Que contiennent les journaux DSC ?

Les journaux DSC sont répartis sur les trois canaux de journal en fonction de l’importance du message. Le journal des opérations dans DSC contient tous les messages d’erreur et peut être utilisé pour identifier un problème. Le journal d’analyse contient un plus grand volume d’événements et peut identifier où se sont produites les erreurs. Ce canal contient également des messages détaillés (le cas échéant). Le journal de débogage contient des journaux qui peuvent vous aider à comprendre comment les erreurs se sont produites. Les messages d’événement DSC sont structurés de telle sorte que chaque message d’événement commence par un ID de tâche représentant de façon unique une opération DSC. L’exemple ci-dessous tente d’obtenir le message du premier événement enregistré dans le journal des opérations DSC.

```powershell
PS C:\Users> $AllDscOpEvents=get-winevent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\Users> $FirstOperationalEvent=$AllDscOpEvents[0]
PS C:\Users> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

Les événements DSC sont enregistrés dans une structure particulière qui permet à l’utilisateur de regrouper les événements d’une seule tâche DSC. La structure est la suivante :

**ID de tâche : \<Guid\>**
**\<Event Message\>**

## Collecte des événements d’une seule opération DSC

Les journaux des événements DSC contiennent des événements générés par diverses opérations DSC. Toutefois, vous êtes généralement intéressé par les détails d’une seule opération en particulier. Tous les journaux DSC peuvent être regroupés par la propriété d’ID de tâche, qui est unique pour chaque opération DSC. L’ID de tâche est affiché comme première valeur de propriété de tous les événements DSC. Les étapes suivantes décrivent comment regrouper tous les événements dans une structure de tableau groupée.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-windows-dsc/operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-Winevent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations=$DscEvents | Group {$_.Properties[0].value}  
```

Ici, la variable `$SeparateDscOperations` contient les journaux regroupés par ID de tâche. Chaque élément du tableau de cette variable représente un groupe d’événements enregistrés par une opération DSC différente, ce qui donne accès à davantage d’informations sur les journaux.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

Vous pouvez extraire les données de la variable `$SeparateDscOperations` à l’aide de [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Voici cinq scénarios dans lesquels vous pouvez extraire les données pour résoudre les problèmes liés à DSC :

### 1 : échecs d’opérations

Tous les événements sont associés à des [niveaux de gravité](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Ces informations peuvent être utilisées pour identifier les événements d’erreur :

```
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2 : détails des opérations exécutées au cours de la dernière demi-heure

`TimeCreated`, une propriété de chaque événement Windows, indique l’heure de création de l’événement. Vous pouvez comparer cette propriété avec un objet date/heure particulier pour filtrer tous les événements :

```powershell
PS C:\> $DateLatest=(Get-date).AddMinutes(-30)
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3 : messages de la dernière opération

La dernière opération est stockée dans le premier index du groupe de tableaux `$SeparateDscOperations`. L’interrogation des messages du groupe pour l’index 0 retourne tous les messages de la dernière opération :

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4 : messages d’erreur enregistrés pour les dernières opérations ayant échoué

`$SeparateDscOperations[0].Group` contient un ensemble d’événements pour la dernière opération. Exécutez l’applet de commande `Where-Object` pour filtrer les événements selon le nom d’affichage du niveau. Les résultats sont stockés dans la variable `$myFailedEvent`, qui peut être examinée pour obtenir le message d’événement :

```powershell
PS C:\> $myFailedEvent=($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5 : tous les événements générés pour un ID de tâche en particulier.

`$SeparateDscOperations` est un tableau de groupes, chacun d’eux a comme nom l’ID de tâche unique. En exécutant l’applet de commande `Where-Object`, vous pouvez extraire les groupes d’événements qui ont un ID de tâche particulier :

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## Utilisation de xDscDiagnostics pour analyser les journaux DSC

**xDscDiagnostics** est un module PowerShell qui se compose de deux opérations simples permettant d’analyser les échecs DSC sur votre ordinateur : `Get-xDscOperation` et `Trace-xDscOperation`. Ces fonctions peuvent vous aider à identifier tous les événements locaux des dernières opérations DSC ou les événements DSC sur des ordinateurs distants (avec des informations d’identification valides). Ici, le terme opération DSC est utilisé pour définir une exécution DSC unique du début à la fin. Par exemple, `Test-DscConfiguration` est une opération DSC à part entière. De même, chaque autre applet de commande dans DSC (telle que `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) peut être identifiée comme une opération DSC à part entière. Les deux applets de commande sont expliquées dans le module PowerShell [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) (Kit de ressources DSC) et plus en détail ci-dessous. Vous accédez à l’aide en exécutant `Get-Help <cmdlet name>`.

## Get-xDscOperation

Cette applet de commande vous permet de rechercher les résultats des opérations DSC qui s’exécutent sur un ou plusieurs ordinateurs, et retourne un objet qui contient la collection d’événements produits par chaque opération DSC. Par exemple, dans la sortie suivante, trois commandes ont été exécutées. La première a réussi et les deux autres ont échoué. Ces résultats sont résumés dans la sortie de `Get-xDscOperation`.

TODO: remplacer cette image pour afficher la sortie de Get-xDscOperation

### Paramètres

* **Newest** : accepte une valeur entière indiquant le nombre d’opérations à afficher. Par défaut, elle retourne les 10 dernières opérations. Par exemple,
  TODO: afficher Get-xDscOperation -Newest 5
* **ComputerName** : paramètre qui accepte un tableau de chaînes, chacune contenant le nom d’un ordinateur sur lequel vous voulez collecter des données de journal des événements DSC. Par défaut, il collecte les données de l’ordinateur hôte. Pour activer cette fonctionnalité, vous devez exécuter la commande suivante sur les ordinateurs distants en mode élevé pour autoriser la collecte d’événements
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Credential** : paramètre de type PSCredential, qui permet d’accéder aux ordinateurs spécifiés dans le paramètre ComputerName.

### Objet retourné

L’applet de commande retourne un tableau d’objets de type **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents**. Chaque objet du tableau se rapporte à une opération DSC différente. L’affichage par défaut de cet objet possède les propriétés suivantes
* **SequenceID** : spécifie le nombre incrémentiel associé à l’opération DSC basée sur l’heure. Par exemple, la dernière opération exécutée a une propriété SequenceID avec la valeur 1, l’avant-dernière avec la valeur 2, etc. Ce nombre est un autre identificateur pour chaque objet du tableau retourné.
* **TimeCreated** : une valeur DateTime qui indique quand l’opération DSC a commencé.
* **ComputerName** : le nom de l’ordinateur à partir duquel les résultats sont agrégés.
* **Result** : une chaîne avec la valeur **Failure** ou **Success** qui indique si l’opération DSC a rencontré une erreur ou non, respectivement.
* **AllEvents** : un objet qui représente une collection d’événements produits par l’opération DSC.

Par exemple, la sortie suivante montre les résultats de la dernière opération sur plusieurs ordinateurs :
  TODO: remplacer l’image pour que Get-xDscOperation affiche les journaux de l’ordinateur distant

## Trace-xDscOperation

Cette applet de commande retourne un objet qui contient une collection d’événements, leur type et la sortie de message générée à partir d’une opération DSC particulière. En règle générale, quand vous trouvez une erreur dans une opération à l’aide de `Get-xDscOperation`, vous tracez l’opération pour déterminer lequel des événements a entraîné un échec.

### Paramètres

* **SequenceID** : valeur entière affectée à une opération sur un ordinateur spécifique. Si vous spécifiez un ID de séquence égal à 4, la trace de la 4ème avant-dernière opération DSC est générée

Trace-xDscOperation avec l'ID de séquence spécifié
* **JobID** : valeur du GUID assignée par xDscOperation du gestionnaire de configuration local pour identifier de manière unique une opération. quand un JobID est spécifié, la trace de l’opération DSC correspondante est générée.
  TODO: remplacer l’image par Trace xDscOperation prenant JobID comme paramètre
* **ComputerName** et **Credential** : ces paramètres permettent de collecter la trace sur des ordinateurs distants :
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO: remplacer l’image par Trace-xDscOperation s’exécutant sur un autre ordinateur

Notez qu’étant donné que `Trace-xDscOperation` regroupe les événements des journaux d’analyse, de débogage et des opérations, vous êtes invité à activer ces journaux comme décrit ci-dessus.

### Objet retourné

L’applet de commande retourne un tableau d’objets, chacun de type `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`. Chaque objet du tableau contient les champs suivants :
* **ComputerName** : nom de l’ordinateur sur lequel les journaux sont collectés.
* **EventType** : il s’agit d’un champ de type d’énumérateur qui contient des informations sur le type d’événement. Ce peut être l’un des types d’énumérateur suivants :
  - *Operational* : l’événement figure dans le journal des opérations.
  - *Analytic* : l’événement figure dans le journal d’analyse.
  - *Debug* : l’événement figure dans le journal de débogage.
  - *Verbose* : la sortie des événements est un message détaillé pendant l’exécution. Les messages détaillés facilitent l’identification de la séquence des événements publiés.
  - *Error* : événements d’erreur. En recherchant les événements d’erreur, vous pouvez généralement rapidement trouver la raison de l’échec.
* **TimeCreated** : valeur DateTime qui indique le moment où l’événement a été enregistré par DSC.
* **Message** : message qui a été enregistré par DSC dans les journaux des événements.

Voici les champs de cet objet qui peuvent être utilisés pour obtenir plus d’informations sur l’événement, mais qui ne sont pas affichés par défaut :

* **JobID** : ID de tâche (format GUID) spécifique de cette opération DSC.
* **SequenceID** : ID de séquence unique pour cette opération DSC sur cet ordinateur.
* **Event** : événement réel enregistré par DSC, de type `System.Diagnostics.Eventing.Reader.EventLogRecord`. Il peut également être obtenu en exécutant l’applet de commande `Get-WinEvent`. Il contient plus d’informations comme la tâche, l’ID d’événement et le niveau de l’événement.

Vous pouvez aussi collecter des informations sur les événements en enregistrant la sortie de `Trace-xDscOperation` dans une variable. Vous pouvez utiliser la commande suivante pour afficher tous les événements d’une opération DSC particulière :

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

Cette commande génère les mêmes résultats que l’applet de commande `Get-WinEvent`, comme dans la sortie ci-dessous :
  TODO: quelle sortie ?

Idéalement, commencez par utiliser `Get-xDscOperations` pour répertorier les dernières exécutions de configuration DSC sur vos ordinateurs. Ensuite, vous pouvez examiner chaque opération (à l’aide de son ID de séquence ou de tâche) avec `Trace-xDscOperation` pour découvrir ce qu’elle a effectué en arrière-plan.

## Mes ressources ne sont pas mises à jour : comment réinitialiser le cache

Le moteur DSC met en cache les ressources implémentées comme module PowerShell pour des raisons d’efficacité. Toutefois, cela peut entraîner des problèmes quand vous créez et testez une ressource simultanément, car DSC charge la version mise en cache tant que le processus n’est pas redémarré. La seule façon pour que DSC charge la version la plus récente est d’arrêter explicitement le processus qui héberge le moteur DSC.

De même, quand vous exécutez `Start-DSCConfiguration`, une fois que vous avez ajouté et modifié une ressource personnalisée, la modification peut ne pas s’exécuter tant que l’ordinateur n’est pas redémarré. Ce comportement s’explique par le fait que DSC s’exécute dans le processus hôte du fournisseur WMI (WmiPrvSE) et qu’en général, il existe plusieurs instances de WmiPrvSE qui s’exécutent simultanément. Quand vous redémarrez, le processus hôte est redémarré et le cache est effacé.

Pour recycler la configuration et effacer le cache sans redémarrer l’ordinateur, vous devez arrêter, puis redémarrer le processus hôte. Vous pouvez le faire pour chaque instance : vous identifiez le processus, l’arrêtez et le redémarrez. Vous pouvez également utiliser `DebugMode`, comme illustré ci-dessous, pour recharger la ressource DSC PowerShell.

Pour identifier le processus qui héberge le moteur DSC et l’arrêter pour chaque instance, vous pouvez répertorier les ID de processus de WmiPrvSE, qui héberge le moteur DSC. Ensuite, pour mettre à jour le fournisseur, arrêtez le processus WmiPrvSE à l’aide des commandes ci-dessous, puis exécutez **Start-DscConfiguration** de nouveau.

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## Utilisation de DebugMode

Vous pouvez configurer le gestionnaire de configuration local DSC de façon à utiliser `DebugMode` pour toujours effacer le cache lors du redémarrage du processus hôte. Quand la valeur est **TRUE**, elle force le moteur à toujours recharger la ressource DSC PowerShell. Une fois que vous avez écrit votre ressource, vous pouvez la redéfinir avec la valeur **FALSE** pour que le moteur mette de nouveau en cache les modules.

La démonstration suivante explique comment `DebugMode` peut actualiser le cache de façon automatique. Tout d’abord, examinons la configuration par défaut :

```
PS C:\Users\WinVMAdmin\Desktop> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

Vous pouvez voir que `DebugMode` a la valeur **FALSE**.

Pour configurer la démonstration de `DebugMode`, utilisez la ressource PowerShell suivante :

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1"|Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

Maintenant, créez une configuration à l’aide de la ressource ci-dessus et appelez-la `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Le contenu du fichier : « **$env:SystemDrive\OutputFromTestProviderDebugMode.txt** » est **1**.

Ensuite, mettez à jour le code du fournisseur à l’aide du script suivant :

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput"|Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Ce script génère un nombre aléatoire et met à jour le fournisseur cade en conséquence. Quand `DebugMode` a la valeur false, le contenu du fichier « **$env:SystemDrive\OutputFromTestProviderDebugMode.txt** » est toujours le même.

À présent, définissez `DebugMode` avec la valeur **TRUE** dans votre script de configuration :

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Quand vous réexécutez le script ci-dessus, le contenu du fichier change à chaque fois. (Vous pouvez exécuter `Get-DscConfiguration` pour le vérifier.) Voici le résultat de deux exécutions supplémentaires (les résultats peuvent être différents quand vous exécutez le script) :

```powershell
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14 
```

## Voir aussi

### Référence
* [Ressource Log dans DSC](logResource.md)

### Concepts
* [Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell](authoringResource.md)

### Autres ressources
* [Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)
<!--HONumber=Feb16_HO4-->
