---
title: Aide sur la ligne de commande PowerShell.exe
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
---
# Aide sur la ligne de commande PowerShell.exe
Démarre une session Windows PowerShell. Vous pouvez utiliser PowerShell.exe pour démarrer une session Windows PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande de Windows PowerShell pour démarrer une nouvelle session. Utilisez les paramètres pour personnaliser la session.

## Syntaxe

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## Paramètres

### -EncodedCommand <Base64EncodedCommand>
Accepte une version de chaîne codée en base 64 d’une commande. Utilisez ce paramètre pour envoyer à Windows PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.

### -ExecutionPolicy <ExecutionPolicy>
Définit la stratégie d’exécution par défaut pour la session en cours et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference. Ce paramètre ne modifie pas la stratégie d’exécution de Windows PowerShell qui est définie dans le Registre. Pour plus d’informations sur les stratégies d’exécution de Windows PowerShell, notamment une liste de valeurs valides, voir about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### -File <FilePath> [<Parameters>]
Exécute le script spécifié dans l’étendue locale (avec source de point), afin que les fonctions et variables que le script crée soient disponibles dans la session en cours. Entrez le chemin d’accès au fichier de script et tous paramètres. **File** doit être le dernier paramètre de la commande, car tous les caractères saisis après le nom de paramètre **File** sont interprétés comme étant le chemin d’accès au fichier de script, suivi par les paramètres de script et leurs valeurs.

Vous pouvez inclure les paramètres d’un script et des valeurs de paramètre dans la valeur du paramètre **File**. Par exemple : `-File .\Get-Script.ps1 -Domain Central`

En règle générale, les paramètres booléens d’un script sont inclus ou omis. Par exemple, la commande suivante utilise le paramètre **All** du fichier de script Get-Script.ps1 : `-File .\Get-Script.ps1 -All`

Dans de rares cas, il se peut que vous deviez fournir une valeur booléenne pour un paramètre booléen. Pour fournir une valeur booléenne pour un paramètre booléen dans la valeur du paramètre **File**, placez le nom et la valeur de celui-ci entre accolades, comme suit : `-File .\Get-Script.ps1 {-All:$False}`

### -InputFormat {Text | XML}
Décrit le format des données envoyées à Windows PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### -Mta
Démarre Windows PowerShell à l’aide d’un cloisonnement multithread. [!INCLUDE[ps_sdk_paramintrodps3](../Token/ps_sdk_paramintrodps3_md.md)] Dans [!INCLUDE[psversion3](../Token/psversion3_md.md)], le cloisonnement par défaut est monothread (STA). Dans [!INCLUDE[psversion2](../Token/psversion2_md.md)], le cloisonnement par défaut est multithread (MTA).

### -NoExit
Ne quitte pas après l’exécution de commandes de démarrage.

### -Nologo
Masque la bannière de copyright au démarrage.

### -NonInteractive
Ne présente pas d’invite interactive à l’utilisateur.

### -NoProfile
Ne charge pas le profil Windows PowerShell.

### -OutputFormat {Text | XML}
Détermine la mise en forme de la sortie de Windows PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### -PSConsoleFile <FilePath>
Charge le fichier de console Windows PowerShell spécifié. Entrez le chemin d’accès et le nom du fichier de console. Pour créer un fichier de console, utilisez l’applet de commande [Export-Console](assetId:///4bab1c02-9e61-4aaf-9957-11d1934ef4ef) dans Windows PowerShell.

### -Sta
Démarre Windows PowerShell à l’aide d’un cloisonnement monothread. Dans [!INCLUDE[psversion3](../Token/psversion3_md.md)], le cloisonnement par défaut est monothread (STA). Dans [!INCLUDE[psversion2](../Token/psversion2_md.md)], le cloisonnement par défaut est multithread (MTA).

### -Version <Windows PowerShell Version>
Démarre la version spécifiée de Windows PowerShell. La version que vous spécifiez doit être installée sur le système. Si [!INCLUDE[psversion3](../Token/psversion3_md.md)] est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ». La valeur par défaut est « 3.0 ».

Si [!INCLUDE[psversion3](../Token/psversion3_md.md)] n’est pas installé, la seule valeur valide est « 2.0 ». Les autres valeurs sont ignorées.

Pour plus d’informations, voir « Installation de Windows PowerShell » dans [Prise en main de Windows PowerShell [ancien MSDN]](assetId:///69555d95-b481-43e1-86e7-b46d68b3e2dd).

### -WindowStyle <Window style>
Définit le style de fenêtre pour la session. Les valeurs valides sont Normal, Hidden, Minimized et Maximized.

### -Command
Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes de Windows PowerShell, puis quitte, sauf si le paramètre NoExit est spécifié.

La valeur de la commande peut être « - », une chaîne, ou un bloc de script. Si la valeur de la commande est « - », le texte de commande est lu à partir de l’entrée standard.

Les blocs de script doivent être entourés d’accolades ({}). Vous pouvez spécifier un bloc de script uniquement lors de l’exécution de PowerShell.exe dans Windows PowerShell. Les résultats du script sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.

Si la valeur de Command est une chaîne, **Command** doit être le dernier paramètre de la commande, car les caractères tapés après la commande sont interprétés comme étant des arguments de la commande.

Pour écrire une chaîne exécutant une commande Windows PowerShell, utilisez le format suivant :

```
"& {<command>}"
```

où les guillemets indiquent une chaîne et l’opérateur d’appel (&) déclenche l’exécution de la commande.

### -Help, -?, /?
Affiche ce message. Si vous tapez une commande PowerShell.exe dans Windows PowerShell, ajoutez les paramètres devant la commande, en les séparant à l’aide d’un trait d’union (-), pas d’une barre oblique (/). Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.

> [!NOTE]
> Remarque sur la résolution de problèmes : dans Windows PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.

## EXEMPLES

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```



<!--HONumber=Apr16_HO1-->


