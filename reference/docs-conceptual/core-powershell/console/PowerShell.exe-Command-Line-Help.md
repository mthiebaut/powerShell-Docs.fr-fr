---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="376b1-103">Aide sur la ligne de commande PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="376b1-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="376b1-104">une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-104">a Windows PowerShell session.</span></span> <span data-ttu-id="376b1-105">Vous pouvez utiliser PowerShell.exe pour démarrer une session PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande PowerShell pour démarrer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="376b1-105">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="376b1-106">Utilisez les paramètres pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="376b1-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="376b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="376b1-107">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="376b1-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="376b1-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="376b1-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="376b1-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="376b1-110">Accepte une version de chaîne codée en base 64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="376b1-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="376b1-111">Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.</span><span class="sxs-lookup"><span data-stu-id="376b1-111">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="376b1-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="376b1-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="376b1-113">Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="376b1-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="376b1-114">Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="376b1-114">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="376b1-115">Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="376b1-115">For information about PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="376b1-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="376b1-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="376b1-117">Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="376b1-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="376b1-118">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="376b1-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="376b1-119">**File** doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom de paramètre **File** sont interprétés comme étant le chemin d’accès au fichier de script, suivi des paramètres de script et de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="376b1-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="376b1-120">Vous pouvez inclure les paramètres d’un script et des valeurs de paramètre dans la valeur du paramètre **File**.</span><span class="sxs-lookup"><span data-stu-id="376b1-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="376b1-121">Par exemple : `-File .\Get-Script.ps1 -Domain Central` Notez que les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel).</span><span class="sxs-lookup"><span data-stu-id="376b1-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="376b1-122">Par exemple, si vous êtes dans cmd.exe et que vous souhaitez passer une valeur de variable d’environnement, vous utilisez la syntaxe de cmd.exe : `powershell -File .\test.ps1 -Sample %windir%` Si vous deviez utiliser la syntaxe de PowerShell, votre script recevrait le littéral « $env:windir » dans cet exemple, et non la valeur de cette variable d’environnement : `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="376b1-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="376b1-123">En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="376b1-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="376b1-124">Par exemple, la commande suivante utilise le paramètre **All** du fichier de script Get-Script.ps1 : `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="376b1-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="376b1-125">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="376b1-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="376b1-126">Décrit le format des données envoyées à PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-126">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="376b1-127">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="376b1-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="376b1-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="376b1-128">-Mta</span></span>
<span data-ttu-id="376b1-129">Démarre PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="376b1-129">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="376b1-130">Ce paramètre est introduit dans PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="376b1-130">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="376b1-131">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="376b1-131">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="376b1-132">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="376b1-132">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="376b1-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="376b1-133">-NoExit</span></span>
<span data-ttu-id="376b1-134">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="376b1-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="376b1-135">-Nologo</span><span class="sxs-lookup"><span data-stu-id="376b1-135">-NoLogo</span></span>
<span data-ttu-id="376b1-136">Masque la bannière de copyright au démarrage.</span><span class="sxs-lookup"><span data-stu-id="376b1-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="376b1-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="376b1-137">-NonInteractive</span></span>
<span data-ttu-id="376b1-138">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="376b1-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="376b1-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="376b1-139">-NoProfile</span></span>
<span data-ttu-id="376b1-140">Ne charge pas le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-140">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="376b1-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="376b1-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="376b1-142">Détermine la mise en forme de la sortie de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-142">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="376b1-143">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="376b1-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="376b1-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="376b1-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="376b1-145">Charge le fichier de console PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="376b1-145">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="376b1-146">Entrez le chemin d’accès et le nom du fichier de console.</span><span class="sxs-lookup"><span data-stu-id="376b1-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="376b1-147">Pour créer un fichier de console, utilisez l’applet de commande [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="376b1-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="376b1-148">-Sta</span></span>
<span data-ttu-id="376b1-149">Démarre PowerShell à l’aide d’un cloisonnement monothread.</span><span class="sxs-lookup"><span data-stu-id="376b1-149">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="376b1-150">Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="376b1-150">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="376b1-151">Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="376b1-151">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="376b1-152">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="376b1-152">-Version <PowerShell Version></span></span>
<span data-ttu-id="376b1-153">Démarre la version spécifiée de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-153">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="376b1-154">La version que vous spécifiez doit être installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="376b1-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="376b1-155">Si PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="376b1-155">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="376b1-156">La valeur par défaut est « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="376b1-156">The default value is "3.0".</span></span>

<span data-ttu-id="376b1-157">Si PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ».</span><span class="sxs-lookup"><span data-stu-id="376b1-157">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="376b1-158">Les autres valeurs sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="376b1-158">Other values are ignored.</span></span>

<span data-ttu-id="376b1-159">Pour plus d’informations, consultez « Installation de PowerShell » dans [Bien démarrer avec PowerShell [ancien MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="376b1-159">For more information, see "Installing PowerShell" in the [Getting Started with PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="376b1-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="376b1-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="376b1-161">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="376b1-161">Sets the window style for the session.</span></span> <span data-ttu-id="376b1-162">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="376b1-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="376b1-163">-Command</span><span class="sxs-lookup"><span data-stu-id="376b1-163">-Command</span></span>
<span data-ttu-id="376b1-164">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell, puis quitte, sauf si le paramètre NoExit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="376b1-164">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="376b1-165">Pour l’essentiel, tout le texte qui suit `-Command` est envoyé sous la forme d’une ligne de commande PowerShell (ce qui diffère de la façon dont `-File` gère les paramètres envoyés à un script).</span><span class="sxs-lookup"><span data-stu-id="376b1-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="376b1-166">La valeur de Command peut être « - », une chaîne</span><span class="sxs-lookup"><span data-stu-id="376b1-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="376b1-167">ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="376b1-167">or a script block.</span></span> <span data-ttu-id="376b1-168">Si la valeur de Command est « - », le texte de commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="376b1-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="376b1-169">Les blocs de script doivent être entourés d’accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="376b1-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="376b1-170">Vous pouvez spécifier un bloc de script uniquement lors de l’exécution de PowerShell.exe dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="376b1-170">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="376b1-171">Les résultats du script sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="376b1-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="376b1-172">Si la valeur de Command est une chaîne, **Command** doit être le dernier paramètre de la commande, car les caractères tapés après la commande sont interprétés comme étant des arguments de la commande.</span><span class="sxs-lookup"><span data-stu-id="376b1-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="376b1-173">Pour écrire une chaîne exécutant une commande PowerShell, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="376b1-173">To write a string that runs a PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="376b1-174">où les guillemets indiquent une chaîne et l’opérateur d’appel (&) déclenche l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="376b1-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="376b1-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="376b1-175">-Help, -?, /?</span></span>
<span data-ttu-id="376b1-176">Affiche ce message.</span><span class="sxs-lookup"><span data-stu-id="376b1-176">Shows this message.</span></span> <span data-ttu-id="376b1-177">Si vous tapez une commande PowerShell.exe dans PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="376b1-177">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="376b1-178">Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="376b1-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="376b1-179">Remarque sur la résolution de problèmes : dans PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="376b1-179">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="376b1-180">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="376b1-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

