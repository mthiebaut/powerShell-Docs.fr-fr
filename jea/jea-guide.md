# Just Enough Administration (JEA) : introduction

## Table des matières
Après avoir lu ce document, vous serez en mesure de créer, déployer, utiliser, gérer et auditer un déploiement Just Enough Administration (JEA).
Voici les sujets abordés dans ce guide préliminaire :

1.  [Introduction](#introduction) : à propos de l’importance de JEA

2.  [Conditions préalables](#prerequisites) : configurer votre environnement

3.  [Utilisation de JEA](#using-jea) : commencer par comprendre l’expérience opérateur dans l’utilisation de JEA

4.  [Refaire la démo](#remake-the-demo-endpoint) : créer une configuration de session JEA ex nihilo

5.  [Capacités de rôle](#role-capabilities) : découvrir comment personnaliser les fonctionnalités JEA avec des fichiers de capacités de rôle

6.  [De bout en bout - Active Directory](#end-to-end---active-directory) : créer un tout nouveau point de terminaison pour la gestion d’Active Directory

7.  [Déploiement et maintenance de plusieurs ordinateurs](#multi-machine-deployment-and-maintenance) : découvrir comment le déploiement et la création évoluent avec l’échelle

8.  [Création de rapports sur JEA](#reporting-on-jea) : découvrir comment auditer et créer des rapports sur toutes les actions et l’infrastructure JEA

9.  [Annexe](#appendix) : compétences et sujets de discussion importants

## Introduction

### Motivation
Quand vous accordez à une personne un accès privilégié à vos systèmes, vous étendez votre confiance à cette personne.
Ce n’est pas sans risque, car les administrateurs sont une surface d’attaque.
Les attaques internes et les informations d’identification volées sont à la fois réelles et courantes.

Ce problème n’est pas nouveau.
Vous connaissez probablement déjà le principe du privilège minimum et vous utilisez peut-être une forme de contrôle d’accès en fonction du rôle (RBAC) avec les applications qui le proposent.
Toutefois, l’efficacité et la facilité de gestion de ces solutions sont souvent limitées par leur large étendue et leur imprécision.
De plus, il existe des lacunes dans la couverture RBAC.
Par exemple, dans Windows, un accès privilégié correspond largement à un commutateur binaire, ce qui vous oblige à accorder des autorisations inutiles lors de l’ajout d’utilisateurs au groupe Administrateurs.

Just Enough Administration (JEA) fournit une plateforme RBAC via la communication à distance de PowerShell.
*Elle permet à des utilisateurs spécifiques d’effectuer des tâches administratives spécifiques sur des serveurs sans leur octroyer de droits d’administrateur.*
Cela vous permet de combler les lacunes de vos solutions RBAC existantes et de simplifier la gestion de ces paramètres.

## Conditions préalables

### État initial
Avant d’entamer cette section, vérifiez les points suivants :

1. JEA est disponible sur votre système. Consultez le fichier [LISEZMOI](./README.md) pour connaître les systèmes d’exploitation actuellement pris en charge et les téléchargements requis.
2. Vous possédez des droits d’administrateur sur l’ordinateur sur lequel vous testez JEA.
3. L’ordinateur est joint à un domaine.
Consultez la section [Création d’un contrôleur de domaine](#creating-a-domain-controller) pour configurer rapidement un nouveau domaine sur un serveur si vous n’en avez pas déjà un.

### Activer la communication à distance de PowerShell
La gestion avec JEA s’effectue via la communication à distance de PowerShell.
Exécutez la commande suivante dans une fenêtre PowerShell de l’administrateur pour vous assurer qu’elle est activée et correctement configurée :

```PowerShell
Enable-PSRemoting 
```

Si vous ne connaissez pas bien la communication à distance de PowerShell, n’hésitez pas à exécuter `Get-Help about_Remote` pour en savoir plus sur cet important concept fondamental.

### Identifier vos utilisateurs ou groupes
Pour voir JEA en action, vous devez identifier les utilisateurs et groupes non-administrateurs que vous aller utiliser tout au long de ce guide.
  
Si vous utilisez un domaine existant, identifiez ou créez quelques utilisateurs ou groupes non privilégiés.
Vous donnerez à ces non-administrateurs un accès à JEA.
Chaque fois que vous voyez la variable `$NonAdministrator` en haut d’un script, attribuez-la à vos utilisateurs ou groupes non-administrateurs. 

Si vous avez créé un domaine ex nihilo, cette tâche est beaucoup plus facile.
Utilisez la section [Configurer des utilisateurs et des groupes](#set-up-users-and-groups) en annexe pour créer des utilisateurs et groupes non-administrateurs.
Les valeurs par défaut de `$NonAdministrator` vont correspondre aux groupes créés dans cette section.

### Configurer le fichier de capacité de rôle de maintenance
Exécutez les commandes suivantes dans PowerShell pour créer le fichier de capacité de rôle démonstration que nous allons utiliser pour la section suivante.
Plus loin dans ce guide, vous allez découvrir à quoi sert ce fichier.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions = 
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory 

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams 
```
  
### Créer et inscrire le fichier de configuration de session de démonstration
Exécutez les commandes suivantes pour créer et inscrire le fichier de configuration de session de démonstration que nous allons utiliser pour la section suivante.
Plus loin dans ce guide, vous allez découvrir à quoi sert ce fichier.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```
 
### Activer l’enregistrement des modules PowerShell (facultatif)
Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système.
Vous n’êtes pas obligé de l’activer pour que JEA fonctionne, mais elle s’avérera utile dans la section [Création de rapports sur JEA](#reporting-on-jea).

1. Ouvrez l'éditeur de stratégie de groupe locale
2. Accédez à « Configuration de l’ordinateur\Modèles d’administration\Composants Windows\Windows PowerShell ».
3. Double cliquez sur « Activer l’enregistrement des modules ».
4. Cliquez sur « Activé ».
5. Dans la section Options, cliquez sur « Afficher » en regard des noms de module.
6. Tapez « * » dans la fenêtre contextuelle. Ainsi, PowerShell enregistre les commandes de tous les modules.
7. Cliquez sur OK et appliquez la stratégie.

Remarque : Vous pouvez également activer la transcription PowerShell à l’échelle du système via la stratégie de groupe.

**Bravo ! Vous avez à présent configuré votre ordinateur avec le point de terminaison de démonstration et vous êtes prêt à découvrir JEA.**

## Utilisation de JEA
Cette section se concentre sur l’expérience de l’utilisateur final lors de *l’utilisation de JEA*.
Dans la section Conditions préalables, vous avez créé un point de terminaison JEA de démonstration.
Nous allons utiliser cette démonstration pour voir JEA en action.
Dans les sections ultérieures, le guide reviendra en arrière en présentant les actions et fichiers qui ont rendu possible cette expérience de l’utilisateur final.

### Utilisation de JEA en tant que non-administrateur
Pour voir JEA en action, vous devez utiliser la communication à distance de PowerShell comme si vous étiez un utilisateur non-administrateur.
Dans une nouvelle fenêtre PowerShell, exécutez la commande suivante :   

```PowerShell
$NonAdminCred = Get-Credential
```

Entrez les informations d’identification de votre compte de non-administrateur quand vous y êtes invité.
Si vous avez suivi la section [Configurer des utilisateurs et des groupes](#set-up-users-and-groups), celles-ci sont les suivantes :
-   Nom d’utilisateur = « OperatorUser »
-   Mot de passe = « pa$$w0rd »

Ensuite, exécutez la commande suivante pour vous connecter au point de terminaison de démonstration à l’aide des informations d’identification que vous avez fournies :

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

Vous avez maintenant démarré une session PowerShell à distance interactive sur l’ordinateur local. En utilisant le paramètre « Credential », vous vous êtes connecté *comme si vous étiez* OperatorUser (ou le compte que vous avez utilisé).
La modification de l’invite par `[localhost]: PS>` indique que vous travaillez sur une session à distance.  

Exécutez la commande suivante dans votre invite de commandes à distance pour afficher les commandes disponibles :

```PowerShell
Get-Command 
```

Comme vous pouvez le voir, il s’agit d’une toute petite partie des commandes disponibles dans une fenêtre PowerShell normale (qui peut souvent en inclure plusieurs milliers).
Plus précisément, seules figurent les 7 applets de commande JEA par défaut (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object) et les deux commandes explicitement incluses dans le fichier de capacité de rôle de maintenance.

Ensuite, intéressons-nous au contexte utilisateur dans lequel fonctionne cette session en appelant la fonction personnalisée incluse dans le fichier de capacité de rôle de maintenance :

```PowerShell
Get-UserInfo
```
 
La sortie de cette fonction indique le « ConnectedUser » et le « RunAsUser ».
L’utilisateur connecté est le compte connecté à la session à distance (par exemple, votre compte).
Il n’a pas besoin de privilèges d’administrateur.
Le compte « d’identification » est le compte qui effectue réellement les actions privilégiées.
La connexion en tant qu’utilisateur et l’exécution en tant qu’utilisateur privilégié nous permettent d’autoriser des utilisateurs non privilégiés à effectuer des tâches administratives spécifiques sans leur octroyer des droits d’administration.

À titre d’illustration, exécutez la commande suivante :

```PowerShell
Restart-Service -Name Spooler -Verbose
```

Normalement, Restart-Service exige des privilèges d’administrateur pour s’exécuter.
Mais avec le compte virtuel JEA, nous sommes en mesure de l’exécuter à l’aide d’informations d’identification non privilégiées.

Ainsi, JEA vous permet de réaliser vos tâches en utilisant les commandes que vous utilisez déjà.
Mais qu’en est-il des commandes que vous *ne devriez pas* être autorisé à utiliser ?
Essayez d’exécuter une commande différente dans la session JEA, comme `Restart-Computer`, puis remarquez que JEA empêche l’exécution de ces commandes.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

Enfin, pour quitter le point de terminaison JEA contraint, exécutez la commande suivante :

```PowerShell
Exit-PSSession
```

Vous vous déconnectez ainsi de la session PowerShell à distance.

## Refaire le point de terminaison de démonstration
Dans cette section, vous allez apprendre à générer un réplica exact du point de terminaison de démonstration que vous avez utilisé dans la section ci-dessus.
Des concepts essentiels à la compréhension de JEA vont ainsi être présentés, notamment les configurations de session PowerShell et les capacités de rôle. 

### Configurations de session PowerShell
Quand vous avez utilisé JEA dans la section ci-dessus, vous avez démarré en exécutant la commande suivante :

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Même si les noms des paramètres sont explicites, le paramètre *ConfigurationName* peut sembler déroutant dans un premier temps.
Ce paramètre spécifiait la configuration de session PowerShell à laquelle vous vous connectiez. 

Une *configuration de session PowerShell* est une locution technique qui désigne un point de terminaison PowerShell.
Métaphoriquement, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.
Selon la façon dont vous paramétrez une configuration de session, elle peut fournir des fonctionnalités différentes aux utilisateurs qui se connectent.
Pour JEA, nous utilisons des configurations de session afin de restreindre PowerShell à un ensemble limité de fonctionnalités et pour une exécution en tant que compte virtuel privilégié.

Vous avez déjà plusieurs configurations de session PowerShell inscrites sur votre ordinateur, chacune étant configurée de façon légèrement différente.
La plupart d’entre elles sont fournies avec Windows, mais la configuration de session « JEA_Demo » a été configurée pendant la section [Conditions préalables](#prerequisites).
Vous pouvez voir toutes les configurations de session inscrites en exécutant la commande suivante depuis une invite PowerShell d’administrateur :

```PowerShell
Get-PSSessionConfiguration
```

### Fichiers de configuration de session PowerShell
Vous pouvez créer des configurations de session en inscrivant de nouveaux *fichiers de configuration de session PowerShell*.
Les fichiers de configuration de session portent une extension de fichier « .pssc ».
Vous pouvez générer des fichiers de configuration de session avec l’applet de commande New-PSSessionConfigurationFile.

Ensuite, vous allez créer et inscrire une configuration de session pour JEA. 

### Générer et modifier votre configuration de session PowerShell
Exécutez la commande suivante pour générer un fichier « squelette » de configuration de session PowerShell.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **Conseil :** Seuls les paramètres de configuration les plus courants sont inclus dans le fichier squelette par défaut.
> Utilisez le paramètre `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.

Ouvrez le fichier dans PowerShell ISE ou votre éditeur de texte favori.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc" 
```

Mettez à jour les champs suivants dans le fichier à l’aide des valeurs ci-dessous (pensez à les remplacer dans votre propre groupe de sécurité non-administrateur) : 

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Voici la signification de chacune de ces entrées :

1.  Le champ *SessionType* définit des paramètres prédéfinis par défaut à utiliser avec ce point de terminaison.
*RestrictedRemoteServer* définit les paramètres minimum nécessaires à la gestion à distance. Par défaut, un point de terminaison *RestrictedRemoteServer* expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host et Out-Default.
Il définit *ExecutionPolicy* sur *RemoteSigned* et *LanguageMode* sur *NoLanguage*.
L’effet net de ces paramètres est un point de départ sécurisé et minimal pour la configuration de votre point de terminaison.

2.  Le champ *RoleDefinitions* affecte des capacités de rôle à des groupes spécifiques.
Il définit qui peut faire quoi en tant que compte privilégié.
Avec ce champ, vous pouvez spécifier les capacités disponibles pour tout utilisateur qui tente d’établir une connexion en fonction de son appartenance à un groupe.
Là est l’essence de la fonctionnalité RBAC de JEA.
Dans cet exemple, vous exposez le champ RoleCapability « Demo » prédéfini aux membres du groupe « Contoso\JEA_NonAdmin_Operator ».

3.  Le champ *RunAsVirtualAccount* indique que PowerShell doit « s’exécuter en tant que » compte virtuel sur ce point de terminaison.
Par défaut, le compte virtuel est membre du groupe Administrateurs prédéfini.
Sur un contrôleur de domaine, il est également membre du groupe Administrateurs du domaine par défaut.
Plus loin dans ce guide, vous allez apprendre à personnaliser les privilèges du compte virtuel.

4.  Le champ *TranscriptDirectory* définit l’emplacement auquel sont enregistrées les transcriptions PowerShell « de procuration de privilège » après chaque session à distance.
Ces transcriptions vous permettent d’inspecter les actions effectuées dans chaque session de façon lisible.
Pour plus d’informations sur les transcriptions PowerShell, consultez ce [billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Remarque : Windows Eventing capture également des informations sur ce que chaque utilisateur a exécuté avec PowerShell.
Les transcriptions sont juste un peu plus faciles à lire.

Enfin, enregistrez vos modifications dans *JEADemo2.pssc*.

### Appliquer la configuration de session PowerShell 

Pour créer un point de terminaison à partir d’un fichier de configuration de session, vous devez inscrire ce fichier.
Quelques éléments d’information sont alors nécessaires :

1. Le chemin du fichier de configuration de session.
2. Le nom de votre configuration de session inscrite. Il s’agit du même nom que celui que les utilisateurs fournissent pour le paramètre « ConfigurationName » quand ils se connectent à votre point de terminaison avec `Enter-PSSession` ou `New-PSSession`.

Pour inscrire la configuration de session sur votre ordinateur local, exécutez la commande suivante :

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Félicitations ! Vous avez configuré votre point de terminaison JEA.

### Tester votre point de terminaison
Réexécutez les étapes répertoriées dans la section [Utilisation de JEA](#using-jea) pour votre nouveau point de terminaison afin de vérifier qu’il fonctionne comme prévu.
Veillez à utiliser le nouveau nom de point de terminaison (JEADemo2) quand vous indiquez le nom de la configuration dans l’applet de commande Enter-PSSession.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### Concepts clés
**Configuration de session PowerShell** : parfois appelée *point de terminaison PowerShell*, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.
Vous pouvez répertorier les configurations de session inscrites sur votre système en exécutant `Get-PSSessionConfiguration`.
Paramétrée de manière spécifique, une configuration de session PowerShell peut être appelée *point de terminaison JEA*.

**Fichier de configuration de session PowerShell (.pssc)** : fichier qui, une fois inscrit, définit les paramètres d’une configuration de session PowerShell.
Il contient des spécifications pour les rôles d’utilisateurs qui peuvent se connecter au point de terminaison, le compte d’identification virtuel, etc.     

**Définitions de rôles** : champ dans un fichier de configuration de session qui définit les capacités de rôle accordées aux utilisateurs qui tentent d’établir une connexion.
Ce champ définit *qui* peut faire *quoi* en tant que compte privilégié.
Là est l’essence des fonctionnalités RBAC de JEA.

**SessionType** : champ dans un fichier de configuration de session qui représente les paramètres par défaut d’une configuration de session.
Pour les points de terminaison JEA, ce champ doit avoir la valeur RestrictedRemoteServer.

**Transcription PowerShell** : fichier contenant une vue par procuration de privilège d’une session PowerShell.
Vous pouvez définir PowerShell de sorte à générer des transcriptions pour les sessions JEA à l’aide du champ TranscriptDirectory.
Pour plus d’informations sur les transcriptions, consultez ce [billet de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).

## Capacités de rôle

### Vue d’ensemble
Dans la section ci-dessus, vous avez appris que le champ « RoleDefinitions » définit quels groupes ont accès à quelles capacités de rôle.
Vous vous êtes peut-être demandé : « Que sont les capacités de rôle ? »
Cette section va répondre à cette question.  

## Présentation des capacités de rôle PowerShell
Les capacités de rôle PowerShell définissent « ce » qu’un utilisateur peut faire sur un point de terminaison JEA.
Elles dressent la liste des éléments comme les commandes visibles, les applications visibles, etc.
Les capacités de rôle sont définies par des fichiers portant une extension « .psrc ».

## Contenu des capacités de rôle
Nous allons commencer en examinant et en modifiant le fichier de capacité de rôle de démonstration que vous avez utilisé précédemment.
Imaginez que vous avez déployé votre configuration de session sur votre environnement, mais que vous avez reçu des commentaires vous invitant à modifier les capacités exposées aux utilisateurs.
Les opérateurs ont besoin de pouvoir redémarrer les ordinateurs et aussi d’être en mesure d’obtenir des informations sur les paramètres réseau.
L’équipe de sécurité vous a également dit que qu’il ne faut pas permettre aux utilisateurs d’exécuter « Restart-Service » sans aucune restriction.
Vous devez restreindre les services que les opérateurs peuvent redémarrer.

Pour apporter ces modifications, commencez par exécuter PowerShell ISE en tant qu’administrateur et ouvrir le fichier suivant :

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Maintenant recherchez et mettez à jour les lignes suivantes dans le fichier : 

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Ce fichier contient quelques exemples intéressants :

1.  Vous avez restreint Restart-Service de sorte que les opérateurs puissent uniquement l’utiliser avec le paramètre -Name et qu’ils soient uniquement autorisés à spécifier « Spooler » en tant qu’argument pour ce paramètre.
Si vous le voulez, vous pouvez également restreindre les arguments en utilisant une expression régulière qui utilise « ValidatePattern » au lieu de « ValidateSet ».

2.  Vous avez exposé toutes les commandes avec le verbe « Get » à partir du module NetTCPIP.
Étant donné que les commandes « Get » ne modifient généralement pas l’état du système, cette action est relativement sûre.
Ceci dit, il est fortement conseillé d’examiner de près chaque commande que vous exposez par le biais de JEA.

3.  Vous avez exposé un exécutable (ipconfig) en utilisant VisibleExternalCommands.
Vous pouvez également exposer des scripts PowerShell complets avec ce champ.
Il est important de toujours fournir le chemin complet des commandes externes pour veiller à ce qu’aucun programme portant le même nom (et potentiellement malveillant) placé dans le chemin de l’utilisateur ne soit exécuté à la place.

Enregistrez le fichier et reconnectez-vous au point de terminaison de démonstration pour vérifier que les modifications ont fonctionné.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Étant donné que vous avez modifié uniquement le fichier de capacité de rôle, il est inutile réinscrire la configuration de session.
PowerShell recherche automatiquement votre capacité de rôle mise à jour quand un utilisateur se connecte.
Dans la mesure où les capacités de rôle sont chargées au démarrage de la session, les sessions existantes ne sont pas affectées par les mises à jour apportées aux fichiers de capacités de rôle.

Maintenant, vérifiez que vous pouvez redémarrer l’ordinateur en exécutant Restart-Computer avec le paramètre -WhatIf (sauf si vous souhaitez réellement redémarrer l’ordinateur).

```PowerShell
Restart-Computer -WhatIf 
```

Vérifiez que vous pouvez exécuter « ipconfig ».

```PowerShell
ipconfig
```

Enfin, vérifiez que Restart-Service ne fonctionne que pour le service Spooler.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail 
```

Quittez la session quand vous avez terminé.

```PowerShell
Exit-PSSession 
```

### Création de capacités de rôle
Dans la section suivante, vous allez créer un point de terminaison JEA pour les utilisateurs du support technique AD.
À titre de préparation, nous allons créer un fichier de capacité de rôle vierge à remplir pendant cette section.
Les capacités de rôle doivent être créées dans un dossier « RoleCapabilities » à l’intérieur d’un module PowerShell valide afin de pouvoir être résolues lorsqu’une session démarre.

Les modules PowerShell sont essentiellement des packages de fonctionnalités PowerShell.
Ils peuvent contenir des fonctions, applets de commandes, ressources DSC, capacités de rôle PowerShell, etc.
Pour plus d’informations sur les modules, exécutez `Get-Help about_Modules` dans une console PowerShell.

Pour créer un module PowerShell avec un fichier de capacité de rôle vierge, exécutez les commandes suivantes :  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File 

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

Félicitations ! Vous avez créé un fichier de capacité de rôle vierge.
Il servira dans la section suivante.

### Concepts clés
**Capacité de rôle (.psrc)** : fichier qui définit « ce » qu’un utilisateur peut faire sur un point de terminaison JEA.
Elle dresse la liste des éléments comme les commandes visibles, les applications de console visibles, etc.
Pour que PowerShell détecte les capacités de rôle, vous devez les placer dans un dossier « RoleCapabilities » dans un module PowerShell valide.

**Module PowerShell** : package de fonctionnalités PowerShell.
Il peut contenir des fonctions, applets de commandes, ressources DSC, capacités de rôle PowerShell, etc.
Pour être chargés automatiquement, les modules PowerShell doivent se trouver sous un chemin dans `$env:PSModulePath`. 

## De bout en bout - Active Directory
Imaginez que l’étendue de votre programme s’est accrue.
Vous êtes maintenant chargé d’ajouter JEA à des contrôleurs de domaine pour effectuer des actions Active Directory.
Le personnel du support technique va utiliser JEA pour déverrouiller des comptes, réinitialiser des mots de passe et effectuer d’autres actions similaires.

Vous devez exposer un tout nouvel ensemble de commandes vers un autre groupe de personnes.
En plus de cela, vous avez un ensemble de scripts Active Directory existants que vous devez aussi exposer.
Cette section va vous guider tout au long de la création d’une configuration de session et d’une capacité de rôle pour cette tâche.

### Conditions préalables
Pour suivre cette section pas à pas, vous devez utiliser un contrôleur de domaine.
Si vous n’avez pas accès à votre contrôleur de domaine, ne vous inquiétez pas.
Essayez de suivre en travaillant sur un autre scénario ou rôle que vous connaissez bien.
Pour configurer rapidement un nouveau contrôleur de domaine, consultez la section [Création d’un contrôleur de domaine](#creating-a-domain-controller) en annexe.

### Étapes de création d’une capacité de rôle et d’une configuration de session

Créer une capacité de rôle peut sembler décourageant au premier abord, mais cette procédure peut être divisée en plusieurs étapes relativement simples :

1.  Identifier les tâches que vous devez activer
2.  Restreindre ces tâches selon les besoins
3.  Vérifier qu’elles fonctionnent avec JEA
4.  Les placer dans un fichier de capacité de rôle
5.  Inscrire une configuration de session qui expose cette capacité de rôle

### Étape 1 : Identifier ce qui doit être exposé
Avant de créer une capacité de rôle ou une configuration de session, vous devez identifier toutes les actions que les utilisateurs devront effectuer par le biais du point de terminaison JEA, ainsi que la manière de les effectuer par le biais de PowerShell.
Cette identification implique un gros travail de collecte et de recherche de spécifications.
Votre manière de procéder va dépendre de votre organisation et de vos objectifs.
Il est important d’intégrer la collecte et la recherche de spécifications comme un élément essentiel du processus réel.
Il pourra même s’agir de l’étape la plus difficile dans le processus d’adoption de JEA.

#### Trouver des ressources
Voici un ensemble de ressources en ligne qui peuvent émerger au cours de votre recherche sur la création d’un point de terminaison de gestion Active Directory :
-   [Vue d’ensemble d’Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [Guide CMD vers PowerShell pour Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### Dresser la liste
Voici l’ensemble des dix actions à partir desquelles vous allez travailler pendant le reste de cette section.
Gardez à l’esprit qu’il s’agit simplement d’un exemple. Les besoins de vos organisations peuvent être différents :

|Action                                                         |Commande PowerShell                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Déverrouillage de compte                                                 |`Unlock-ADAccount`                                             |
|Réinitialisation de mot de passe                                                 |`Set-ADAccountPassword` et `Set-ADUser -ChangePasswordAtLogon`|
|Modifier le titre d’un utilisateur                                          |`Set-ADUser -Title`                                            |  
|Rechercher des comptes AD verrouillés, désactivés, inactifs, etc. |`Search-ADAccount`                                             | 
|Ajouter un utilisateur au groupe                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        | 
|Supprimer un utilisateur du groupe                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     | 
|Activer un compte d’utilisateur                                          |`Enable-ADAccount`                                             |
|Désactiver un compte d’utilisateur                                         |`Disable-ADAccount`                                            |

### Étape 2 : Restreindre les tâches selon les besoins

Maintenant que vous avez votre liste d’actions, vous devez réfléchir aux capacités de chaque commande.
Il existe deux raisons importantes à cela :

1.  Vous pouvez facilement donner aux utilisateurs plus de capacités que vous ne le voulez.
Par exemple, `Set-ADUser` est une commande incroyablement puissante et flexible.
Vous pouvez ne pas souhaiter exposer tout ce dont elle est capable aux utilisateurs du support technique.  

2.  Pire encore, il est possible d’exposer des commandes qui permettent aux utilisateurs d’échapper aux restrictions de JEA.
Le cas échéant, JEA cesse de fonctionner comme une limite de sécurité.
Alors soyez prudent lors de la sélection des commandes.
Par exemple, Invoke-Expression permet aux utilisateurs d’exécuter du code non restreint.
Pour plus d’informations à ce sujet, consultez la section Éléments à prendre en compte lors de la restriction des commandes.

Après avoir examiné chaque commande, vous décidez de restreindre les suivantes :

1.  `Set-ADUser` doit uniquement s’exécuter avec le paramètre « -Title » 

2.  `Add-ADGroupMember` et `Remove-ADGroupMember` doit uniquement fonctionner avec certains groupes

### Étape 3 : Vérifier que les tâches fonctionnent avec JEA
En fait, l’utilisation de ces applets de commande risque de ne pas être très simple dans l’environnement JEA restreint.
JEA s’exécute en mode *sans langage* qui, entre autres choses, empêche les utilisateurs d’utiliser des variables.
Pour garantir une expérience sans heurts aux utilisateurs, il est important de vérifier quelques points.

Par exemple, intéressons-nous à `Set-ADAccountPassword`.
Le paramètre « -NewPassword » exige une chaîne sécurisée.
Souvent, les utilisateurs créent une chaîne sécurisée et la transmettent en tant que variable (comme indiqué ci-dessous) :

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

Toutefois, le mode sans langage empêche l’utilisation de variables.
Vous pouvez contourner cette restriction de deux manières :

1.  Vous pouvez exiger que les utilisateurs exécutent la commande sans affecter de variables.
Cette option est facile à configurer, mais peut s’avérer contraignante pour les opérateurs qui utilisent le point de terminaison.
Qui voudrait taper cette commande à chaque réinitialisation de mot de passe ?
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  Vous pouvez encapsuler la complexité dans un script ou une fonction que vous exposez aux utilisateurs finaux.
Les scripts et fonctions que vous exposez s’exécutent dans un contexte non restreint ; vous pouvez écrire des fonctions qui utilisent des variables et appellent d’autres commandes sans rencontrer aucun problème.
Cette approche simplifie l’expérience de l’utilisateur final, empêche les erreurs, réduit les connaissances PowerShell requises et réduit l’exposition involontaire d’un excès de fonctionnalités.
Le seul inconvénient réside dans le coût de création et de maintenance de la fonction.

#### Aparté : Ajout d’une fonction à votre module
En choisissant l’approche n° 2, vous allez écrire une fonction PowerShell appelée `Reset-ContosoUserPassword`.
Cette fonction va faire tout ce qui doit se produire lorsque vous réinitialisez le mot de passe d’un utilisateur.
Dans votre organisation, cette opération peut impliquer des tâches compliquées.
Comme il s’agit tout simplement d’un exemple, votre commande va juste réinitialiser le mot de passe et exiger que l’utilisateur change de mot de passe lors de la connexion.
Nous la placerons dans le module Contoso_AD_Module que vous avez créé au cours de la dernière section.

1. Dans PowerShell ISE, ouvrez « Contoso_AD_Module.psm1 ».
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' 
```

2. Appuyez sur Ctrl+J pour ouvrir le menu des extraits de code.

3. Faites défiler vers le bas jusqu'à ce que vous trouviez « fonction » et appuyez sur Entrée.
Un squelette super basique de fonction apparaît.

4. Renommez la fonction « Reset-ContosoUserPassword ».  

5. Renommez un des paramètres « Identité » et supprimez le deuxième.

6. Copiez ce qui suit dans le corps de la fonction.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Enregistrez le fichier.
Vous devez obtenir quelque chose qui ressemble à ceci :
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
} 
```
À présent, vos utilisateurs peuvent simplement appeler `Reset-ContosoUserPassword` sans avoir à mémoriser la syntaxe pour créer une chaîne sécurisée intégrée.

### Étape 4 : Modifier le fichier de capacité de rôle
Dans la section [Création de capacité de rôle](#role-capability-creation), vous avez créé un fichier de capacité de rôle vierge.
Dans cette section, vous allez renseigner les valeurs dans ce fichier.

Commencez par ouvrir le fichier de capacité de rôle dans ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```
Mettez à jour le fichier avec les modifications suivantes :
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters = 
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}
  
# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }   
VisibleFunctions = 'Reset-ContosoUserPassword'
```

Il est bon de noter quelques points sur ce qui précède :
1.  PowerShell va tenter de charger automatiquement les modules nécessaires à votre capacité de rôle.
Vous devrez peut-être répertorier explicitement les noms de module dans le champ « ModulesToImport » si vous rencontrez des problèmes avec un module qui ne se charge pas automatiquement.

2.  Si vous ne savez pas si une commande est une applet de commande ou une fonction, exécutez `Get-Command` et examinez « CommandType ».

3.  ValidatePattern vous permet d’utiliser une expression régulière pour restreindre des arguments de paramètre s’il n’est pas facile de définir un ensemble de valeurs autorisées.
Vous ne pouvez pas définir à la fois ValidatePattern et ValidateSet pour un seul paramètre.

### Étape 5 : Inscrire une nouvelle configuration de session
Ensuite, vous allez créer un fichier de configuration de session qui va exposer votre capacité de rôle aux membres du groupe AD « JEA_NonAdmin_HelpDesk ». 

Commencez par créer et ouvrir un nouveau fichier de configuration de session vierge dans PowerShell ISE.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Modifiez les champs suivants dans le fichier PSSC.
Si vous travaillez dans votre propre environnement, vous devez remplacer « CONTOSO\JEA_NonAdmins_Helpdesk » par votre propre utilisateur ou groupe non-administrateur.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.' 

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }} 
```
Enregistrer et inscrire la configuration de session
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc" 
```
### Faites le test !
Obtenez vos informations d’identification d’utilisateur non-administrateur :
```PowerShell
$HelpDeskCred = Get-Credential
```
Si vous avez suivi la section Configurer des utilisateurs et des groupes, celles-ci sont les suivantes :
-   Nom d’utilisateur = « HelpDeskUser »
-   Mot de passe = « pa$$w0rd »

Accédez à distance au point de terminaison du support technique AD à l’aide des informations d’identification de non-administrateur :
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred 
```
Utilisez Set-ADUser pour réinitialiser le titre d’un utilisateur.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer 
```
Vérifiez que le titre a changé.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title 
```
À présent, utilisez Add-ADGroupMember pour ajouter un utilisateur à TestGroup.
Remarque : Vérifiez que vous avez créé TestGroup au préalable.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose 
```
Quittez la session :
```PowerShell
Exit-PSSession
```
### Concepts clés
**Mode NoLanguage** : quand PowerShell est en mode « NoLanguage », les utilisateurs peuvent uniquement exécuter des commandes ; ils ne peuvent pas utiliser des éléments de langage.
Pour plus d’informations, exécuter `Get-Help about_Language_Modes`.

**Fonctions PowerShell** : les fonctions PowerShell sont des morceaux de code PowerShell que vous pouvez appeler par leur nom.
Pour plus d’informations, exécuter `Get-Help about_Functions`.

**ValidateSet/ValidatePattern** : lors de l’exposition d’une commande, vous pouvez restreindre les arguments valides de paramètres spécifiques.
ValidateSet correspond à la liste spécifique des commandes valides.
ValidatePattern est une expression régulière à laquelle doivent correspondre les arguments de ce paramètre.

## Déploiement et maintenance de plusieurs ordinateurs
À ce stade, vous avez plusieurs fois déployé JEA sur des systèmes locaux.
Étant donné que votre environnement de production comprend probablement plusieurs ordinateurs, il est important de parcourir les étapes critiques du processus de déploiement qui doivent être répétées sur chaque ordinateur.

### Étapes générales :
1.  Copiez vos modules (avec des capacités de rôle) sur chaque nœud.
2.  Copiez vos fichiers de configuration de session sur chaque nœud.
3.  Exécutez `Register-PSSessionConfiguration` avec votre configuration de session.
4.  Conservez une copie de votre configuration de session et de vos kits de ressources à un emplacement sécurisé.
Pendant que vous apportez des modifications, il est toujours intéressant de disposer d’une « seule source de vérité ».

### Exemple de script
Voici un exemple de script de déploiement.
Pour l’utiliser dans votre environnement, vous devrez utiliser les noms/chemins de partages de fichiers et modules réels.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### Modification des capacités
Quand vous vous occupez d’un grand nombre d’ordinateurs, il est important que les modifications soient introduites de façon cohérente.
Une fois que JEA a une ressource DSC, votre environnement est synchronisé.
En attendant, nous vous recommandons vivement de conserver une copie principale de vos configurations de session et de redéployer chaque fois que vous apportez une modification.

### Suppression de capacités
Pour supprimer votre configuration JEA de vos systèmes, utilisez la commande suivante sur chaque ordinateur :
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## Création de rapports sur JEA
Étant donné que JEA permet à des utilisateurs non privilégiés de s’exécuter dans un contexte privilégié, la journalisation et l’audit sont extrêmement importants.
Dans cette section, nous allons passer en revue les outils que vous pouvez utiliser pour la journalisation et la création de rapports.

### Création de rapports sur les actions JEA
#### Transcription de procuration de privilège
Un des moyens les plus rapides d’obtenir un résumé de ce qui se passe au cours d’une session PowerShell consiste à observer une personne qui tape au clavier.
Vous voyez ses commandes, la sortie de ces commandes et tout va bien.
Ou pas, mais au moins vous savez.
La transcription PowerShell a pour but de vous donner un aperçu similaire après coup.

Quand vous utilisez le champ « TranscriptDirectory » dans votre configuration de session, PowerShell enregistre automatiquement une transcription de toutes les actions effectuées au cours d’une session donnée.
Vous pouvez trouver des transcriptions de vos sessions dans ce document : « $env:ProgramData\JEAConfiguration\Transcripts ».

Comme vous pouvez le voir, la transcription enregistre des informations sur l’utilisateur « connecté », l’utilisateur « du compte d’identification », les commandes exécutées pendant la session et bien plus encore.
Pour plus d’informations sur la transcription PowerShell, consultez [ce billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

#### Journaux des événements PowerShell
Quand l’enregistrement des modules est activé, toutes les actions PowerShell sont également enregistrées dans les journaux des événements Windows standard.
Ces journaux sont un peu plus délicats à gérer par rapport aux transcriptions, mais le niveau de détail qu’ils donnent peut vous être utile.

Dans le journal des opérations « PowerShell », l’ID d’événement 4104 enregistre chaque commande appelée si vous avez activé l’enregistrement des modules.

#### Autres journaux des événements
Contrairement aux journaux et transcriptions PowerShell, les autres mécanismes de journalisation ne capturent pas « l’utilisateur connecté ».
Vous devrez effectuer une corrélation entre les autres journaux et les journaux PowerShell pour faire correspondre les actions effectuées.

Dans le journal des opérations « Windows Remote Management », l’ID d’événement 193 enregistre le SID et le nom de l’utilisateur, ainsi que le SID du compte virtuel d’identification pour faciliter cette corrélation.
Vous avez peut-être également remarqué que le nom du compte virtuel d’identification inclut à la fin le domaine et le nom de l’utilisateur qui tente d’établir une connexion.

### Création de rapports sur la configuration JEA
#### Get-PSSessionConfiguration
Pour créer des rapports précis sur l’état de votre environnement, il est important de connaître le nombre de points de terminaison JEA que vous avez configurés sur votre ordinateur.
`Get-PSSessionConfiguration` permet exactement de le déterminer.
 
#### Get-PSSessionCapability
Créer manuellement des rapports sur les capacités d’un utilisateur donné par le biais d’un point de terminaison JEA peut s’avérer assez complexe.
Vous devez probablement inspecter plusieurs capacités de rôle.
Heureusement, l’applet de commande « Get-PSSessionCapability » permet de le faire.

Pour tester, exécutez la commande suivante à partir d’une invite PowerShell d’administrateur :
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## Conclusion 
À l’issue de ce guide, vous devez avoir les outils et le vocabulaire nécessaires pour créer votre propre point de terminaison JEA. Merci de votre attention !

## Annexe

## Concepts clés utilisés dans ce guide
**Communication à distance de PowerShell** : la communication à distance de PowerShell vous permet d’exécuter des commandes PowerShell sur des ordinateurs à distance.
Vous pouvez travailler sur un ou plusieurs ordinateurs et utiliser des connexions temporaires ou permanentes.
Dans cette démonstration, vous avez accédé à distance à votre ordinateur local avec une session interactive.
JEA restreint les fonctionnalités disponibles par le biais de la communication à distance de PowerShell.
Pour plus d'informations sur la communication à distance de PowerShell, exécutez `Get-Help about_Remote`.

**Utilisateur « d’identification » ** : quand vous utilisez JEA, un non-administrateur « s’exécute en tant que » « compte virtuel » privilégié.
Le compte virtuel dure uniquement le temps de la session à distance.
Autrement dit, il est créé lorsqu’un utilisateur se connecte au point de terminaison, puis détruit lorsque l’utilisateur met fin à la session.
Par défaut, le compte virtuel est membre du groupe Administrateurs local.
Sur un contrôleur de domaine, il est membre du groupe Admins du domaine.
Les comptes virtuels sont locaux pour l’ordinateur sur lequel ils sont créés et n’ont pas d’autorisations en dehors de cet ordinateur.
Cela signifie qu’ils ne sont pas inscrits dans Active Directory (aucun RID n’est attribué).
En outre, si un script/une commande autorisé(e) tente d’accéder à des ressources en dehors de l’ordinateur local, il ou elle accède à ces ressources sous l’identité de l’ordinateur, et non pas l’identité du compte virtuel.

**« Utilisateur connecté »** : utilisateur non-administrateur qui se connecte au point de terminaison JEA et auquel des rôles sont attribués.
Toutes les commandes que cet utilisateur exécute sont exécutées dans le contexte de l’utilisateur d’identification ou compte virtuel.


### Création d’un contrôleur de domaine

Ce document part du principe que votre ordinateur est joint à un domaine.
Si vous n’avez pas de domaine à rejoindre, cette section peut vous aider à rapidement mettre en place un contrôleur de domaine à l’aide de DSC.

#### Conditions préalables

1.  L’ordinateur se trouve sur un réseau interne.
2.  L’ordinateur n’est pas joint à un domaine existant.
3.  L’ordinateur exécute Windows Server 2016 ou WMF 5.0 y est installé.

#### Installer xActiveDirectory
Si votre ordinateur a une connexion Internet active, exécutez la commande suivante dans une fenêtre PowerShell avec élévation de privilèges :
```PowerShell
Install-Module xActiveDirectory -Force 
```
Si vous n’avez pas de connexion Internet, installez xActiveDirectory sur un autre ordinateur, puis copiez le dossier xActiveDirectory dans le dossier « C:\Program Files\WindowsPowerShell\Modules » sur votre ordinateur.

Pour confirmer la réussite de l’installation, exécutez la commande suivante :
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### Configurer un domaine avec DSC
Copiez le script suivant dans PowerShell pour que votre ordinateur devienne un contrôleur de domaine dans un nouveau domaine.
**NOTE DE L’AUTEUR : IL EXISTE UN PROBLÈME CONNU LIÉ AUX INFORMATIONS D’IDENTIFICATION FOURNIES QUI NE SONT PAS UTILISÉES.  POUR PLUS DE SÉCURITÉ, N’OUBLIEZ PAS VOTRE MOT DE PASSE D’ADMINISTRATEUR LOCAL.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
Votre ordinateur va redémarrer plusieurs fois.
Vous savez que le processus est terminé une fois que vous voyez un fichier appelé « C:\temp.txt » indiquant que le domaine a été créé. 

#### Configurer des utilisateurs et groupes
Les commandes suivantes configurent un groupe Opérateur et support technique dans votre domaine et un utilisateur non-administrateur correspondant qui est membre de ce groupe.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### À propos de l’inscription sur liste noire
Maintenant que vous avez manipulé JEA, vous vous demandez peut-être s’il est possible d’inscrire des commandes sur liste rouge.
Cette demande est compréhensible, mais elle n’est pas actuellement prévue pour JEA pour les raisons suivantes :

1.  Nous avons conçu JEA pour limiter les opérateurs aux actions qu’ils ont besoin d’effectuer.
Une liste rouge fait le contraire.

2.  Les auteurs des commandes PowerShell n’ont pas conçu des commandes PowerShell avec JEA à l’esprit.
Dans une nouvelle installation de Windows Server 2016, environ 1 520 commandes sont disponibles tout de suite.
Les modèles de menace définis pour ces commandes ne comprenaient pas la possibilité qu’un utilisateur les exécutent en tant que compte plus privilégié.
Par exemple, certaines commandes permettent l’injection de code par conception (par exemple, Add-Type et Invoke-Command dans le module PowerShell principal).
JEA peut vous avertir quand vous exposez les commandes spécifiques que nous connaissons, mais nous n’avons pas réévalué toutes les autres commandes dans Windows au regard du nouveau modèle de menace.
Vous devez comprendre les capacités des commandes que vous exposez par le biais de JEA.  

3.  De plus, même si JEA a bloqué toutes les commandes comportant des vulnérabilités d’injection de code, il n’existe aucune garantie qu’un utilisateur malveillant ne serait pas capable d’exécuter une action inscrite sur liste rouge avec une autre commande connexe.
Sauf si vous comprenez toutes les commandes que vous exposez, il vous est impossible de garantir qu’une certaine action n’est pas possible.
Il vous incombe de comprendre les commandes que vous exposez, qu’elles utilisent une liste verte ou une liste rouge.
Le nombre de commandes qu’exposerait une liste rouge serait difficile à gérer, c’est pourquoi JEA est plutôt implémenté avec des listes vertes.

### Éléments à prendre en considération lors de la limitation des commandes
Un point important concerne cette étape.
Il est essentiel que toutes les capacités exposées par le biais de JEA se trouvent dans des zones limitées à l’administrateur.
Les utilisateurs non-administrateurs ne doivent pas avoir la possibilité de modifier les scripts utilisés par le biais des points de terminaison JEA.

Par ailleurs, il est essentiel de ne pas donner aux utilisateurs JEA la possibilité de remplacer des configurations JEA et des scripts inscrits sur liste verte pendant leurs sessions JEA.
Faites très attention quand vous exposez des commandes telles que `Copy-Item` !

### Pièges liés aux capacités de rôle
Vous pouvez tomber dans quelques pièges courants en suivant vous-même ce processus.
Voici un guide rapide qui explique comment identifier et corriger ces problèmes lors de la modification ou la création d’un point de terminaison :

#### Fonctions et applets de commande
Les commandes PowerShell écrites dans PowerShell sont des fonctions PowerShell.
Les commandes PowerShell écrites comme classes .NET spécialisées sont des applets de commande PowerShell.
Vous pouvez déterminer le type de commande en exécutant `Get-Command`.

#### VisibleProviders 
Vous devez exposer tous les fournisseurs dont vos commandes ont besoin.
Le plus courant est le fournisseur FileSystem, mais vous aurez peut-être besoin d’en exposer d’autres comme le fournisseur Registry.
Pour une présentation des fournisseurs, consultez le [billet de blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Soyez prudent quand vous exposez des fournisseurs. Souvent, il est préférable de définir votre propre fonction qui utilise les fournisseurs sous-jacents plutôt que d’exposer directement le fournisseur dans une session JEA.
Ainsi, vous pouvez quand même autoriser des utilisateurs à travailler avec des fichiers, des clés de Registre, etc., tout en continuant à déterminer **quels* fichiers et clés de Registre ils peuvent utiliser à l’aide d’une logique de validation personnalisée.

<!--HONumber=Jun16_HO1-->


