---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: b2236decb3295ee5b543f72f083e516c91fa4b5f
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="powershellexe-command-line-help"></a>Aide sur la ligne de commande PowerShell.exe
Démarre une session Windows PowerShell. Vous pouvez utiliser PowerShell.exe pour démarrer une session Windows PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande Windows PowerShell pour démarrer une nouvelle session. Utilisez les paramètres pour personnaliser la session.

## <a name="syntax"></a>Syntaxe

```syntax
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

## <a name="parameters"></a>Paramètres

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>
Accepte une version de chaîne codée en base 64 d’une commande. Utilisez ce paramètre pour envoyer à Windows PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>
Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference. Ce paramètre ne modifie pas la stratégie d’exécution Windows PowerShell qui est définie dans le Registre. Pour plus d’informations sur les stratégies d’exécution Windows PowerShell, notamment une liste de valeurs valides, voir about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]
Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active. Entrez le chemin d’accès au fichier de script et les paramètres éventuels. **File** doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom de paramètre **File** sont interprétés comme étant le chemin d’accès au fichier de script, suivi des paramètres de script et de leurs valeurs.

Vous pouvez inclure les paramètres d’un script et des valeurs de paramètre dans la valeur du paramètre **File**. Par exemple : `-File .\Get-Script.ps1 -Domain Central` Notez que les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).
Par exemple, si vous êtes dans cmd.exe et que vous souhaitez passer une valeur de variable d’environnement, vous utilisez la syntaxe de cmd.exe : `powershell -File .\test.ps1 -Sample %windir%` Si vous deviez utiliser la syntaxe de PowerShell, votre script recevrait le littéral « $env:windir » dans cet exemple, et non la valeur de cette variable d’environnement : `powershell -File .\test.ps1 -Sample $env:windir`

En règle générale, les paramètres de commutateur d’un script sont inclus ou omis. Par exemple, la commande suivante utilise le paramètre **All** du fichier de script Get-Script.ps1 : `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}
Décrit le format des données envoyées à Windows PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### <a name="-mta"></a>-Mta
Démarre Windows PowerShell à l’aide d’un cloisonnement multithread. Ce paramètre est introduit dans Windows PowerShell 3.0. Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA). Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).

### <a name="-noexit"></a>-NoExit
Ne quitte pas après l’exécution de commandes de démarrage.

### <a name="-nologo"></a>-Nologo
Masque la bannière de copyright au démarrage.

### <a name="-noninteractive"></a>-NonInteractive
Ne présente pas d’invite interactive à l’utilisateur.

### <a name="-noprofile"></a>-NoProfile
Ne charge pas le profil Windows PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
Détermine la mise en forme de la sortie de Windows PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>
Charge le fichier de console Windows PowerShell spécifié. Entrez le chemin d’accès et le nom du fichier de console. Pour créer un fichier de console, utilisez l’applet de commande [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) dans Windows PowerShell.

### <a name="-sta"></a>-Sta
Démarre Windows PowerShell à l’aide d’un cloisonnement monothread. Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA). Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).

### <a name="-version-windows-powershell-version"></a>-Version <Windows PowerShell Version>
Démarre la version spécifiée de Windows PowerShell. La version que vous spécifiez doit être installée sur le système. Si Windows PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ». La valeur par défaut est « 3.0 ».

Si Windows PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ». Les autres valeurs sont ignorées.

Pour plus d’informations, voir « Installation de Windows PowerShell » dans [Prise en main de Windows PowerShell [ancien MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>
Définit le style de fenêtre pour la session. Les valeurs valides sont Normal, Hidden, Minimized et Maximized.

### <a name="-command"></a>-Command
Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes Windows PowerShell, puis quitte, sauf si le paramètre NoExit est spécifié.
Pour l’essentiel, tout le texte qui suit `-Command` est envoyé sous la forme d’une ligne de commande PowerShell (ce qui diffère de la façon dont `-File` gère les paramètres envoyés à un script).

La valeur de Command peut être « - », une chaîne ou un bloc de script. Si la valeur de Command est « - », le texte de commande est lu à partir de l’entrée standard.

Les blocs de script doivent être entourés d’accolades ({}). Vous pouvez spécifier un bloc de script uniquement lors de l’exécution de PowerShell.exe dans Windows PowerShell. Les résultats du script sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.

Si la valeur de Command est une chaîne, **Command** doit être le dernier paramètre de la commande, car les caractères tapés après la commande sont interprétés comme étant des arguments de la commande.

Pour écrire une chaîne exécutant une commande Windows PowerShell, utilisez le format suivant :

```
"& {<command>}"
```

où les guillemets indiquent une chaîne et l’opérateur d’appel (&) déclenche l’exécution de la commande.

### <a name="-help---"></a>-Help, -?, /?
Affiche ce message. Si vous tapez une commande PowerShell.exe dans Windows PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/). Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.

> [!NOTE]
> Remarque sur la résolution de problèmes : dans Windows PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.

## <a name="examples"></a>EXEMPLES

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

