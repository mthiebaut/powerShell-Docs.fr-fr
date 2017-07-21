---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 9c56f09ac186b0c3a64cce6700740ca1ba6abd06
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="66bb6-103">Aide sur la ligne de commande PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="66bb6-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="66bb6-104">Démarre une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="66bb6-105">Vous pouvez utiliser PowerShell.exe pour démarrer une session Windows PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande Windows PowerShell pour démarrer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="66bb6-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="66bb6-106">Utilisez les paramètres pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="66bb6-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="66bb6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66bb6-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="66bb6-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66bb6-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="66bb6-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="66bb6-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="66bb6-110">Accepte une version de chaîne codée en base 64 d’une commande.</span><span class="sxs-lookup"><span data-stu-id="66bb6-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="66bb6-111">Utilisez ce paramètre pour envoyer à Windows PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.</span><span class="sxs-lookup"><span data-stu-id="66bb6-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="66bb6-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="66bb6-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="66bb6-113">Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="66bb6-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="66bb6-114">Ce paramètre ne modifie pas la stratégie d’exécution Windows PowerShell qui est définie dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="66bb6-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="66bb6-115">Pour plus d’informations sur les stratégies d’exécution Windows PowerShell, notamment une liste de valeurs valides, voir about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="66bb6-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="66bb6-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="66bb6-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="66bb6-117">Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="66bb6-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="66bb6-118">Entrez le chemin d’accès au fichier de script et les paramètres éventuels.</span><span class="sxs-lookup"><span data-stu-id="66bb6-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="66bb6-119">**File** doit être le dernier paramètre de la commande, car tous les caractères tapés après le nom de paramètre **File** sont interprétés comme étant le chemin d’accès au fichier de script, suivi des paramètres de script et de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="66bb6-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="66bb6-120">Vous pouvez inclure les paramètres d’un script et des valeurs de paramètre dans la valeur du paramètre **File**.</span><span class="sxs-lookup"><span data-stu-id="66bb6-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="66bb6-121">Par exemple : `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="66bb6-121">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="66bb6-122">En règle générale, les paramètres de commutateur d’un script sont inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="66bb6-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="66bb6-123">Par exemple, la commande suivante utilise le paramètre **All** du fichier de script Get-Script.ps1 : `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="66bb6-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="66bb6-124">Dans de rares cas, vous pouvez être amené à fournir une valeur booléenne pour un paramètre de commutateur.</span><span class="sxs-lookup"><span data-stu-id="66bb6-124">In rare cases, you might need to provide a Boolean value for a switch parameter.</span></span> <span data-ttu-id="66bb6-125">Pour fournir une valeur booléenne pour un paramètre de commutateur dans la valeur du paramètre **File**, placez le nom et la valeur de celui-ci entre accolades, comme suit : `-File .\Get-Script.ps1 {-All:$False}`</span><span class="sxs-lookup"><span data-stu-id="66bb6-125">To provide a Boolean value for a switch parameter in the value of the **File** parameter, enclose the parameter name and value in curly braces, such as the following: `-File .\Get-Script.ps1 {-All:$False}`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="66bb6-126">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="66bb6-126">-InputFormat {Text | XML}</span></span>
<span data-ttu-id="66bb6-127">Décrit le format des données envoyées à Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-127">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="66bb6-128">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="66bb6-128">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="66bb6-129">-Mta</span><span class="sxs-lookup"><span data-stu-id="66bb6-129">-Mta</span></span>
<span data-ttu-id="66bb6-130">Démarre Windows PowerShell à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="66bb6-130">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="66bb6-131">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="66bb6-131">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="66bb6-132">Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="66bb6-132">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="66bb6-133">Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="66bb6-133">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="66bb6-134">-NoExit</span><span class="sxs-lookup"><span data-stu-id="66bb6-134">-NoExit</span></span>
<span data-ttu-id="66bb6-135">Ne quitte pas après l’exécution de commandes de démarrage.</span><span class="sxs-lookup"><span data-stu-id="66bb6-135">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="66bb6-136">-Nologo</span><span class="sxs-lookup"><span data-stu-id="66bb6-136">-NoLogo</span></span>
<span data-ttu-id="66bb6-137">Masque la bannière de copyright au démarrage.</span><span class="sxs-lookup"><span data-stu-id="66bb6-137">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="66bb6-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="66bb6-138">-NonInteractive</span></span>
<span data-ttu-id="66bb6-139">Ne présente pas d’invite interactive à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66bb6-139">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="66bb6-140">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="66bb6-140">-NoProfile</span></span>
<span data-ttu-id="66bb6-141">Ne charge pas le profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-141">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="66bb6-142">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="66bb6-142">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="66bb6-143">Détermine la mise en forme de la sortie de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-143">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="66bb6-144">Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).</span><span class="sxs-lookup"><span data-stu-id="66bb6-144">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="66bb6-145">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="66bb6-145">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="66bb6-146">Charge le fichier de console Windows PowerShell spécifié.</span><span class="sxs-lookup"><span data-stu-id="66bb6-146">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="66bb6-147">Entrez le chemin d’accès et le nom du fichier de console.</span><span class="sxs-lookup"><span data-stu-id="66bb6-147">Enter the path and name of the console file.</span></span> <span data-ttu-id="66bb6-148">Pour créer un fichier de console, utilisez l’applet de commande [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-148">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="66bb6-149">-Sta</span><span class="sxs-lookup"><span data-stu-id="66bb6-149">-Sta</span></span>
<span data-ttu-id="66bb6-150">Démarre Windows PowerShell à l’aide d’un cloisonnement monothread.</span><span class="sxs-lookup"><span data-stu-id="66bb6-150">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="66bb6-151">Dans Windows PowerShell 3.0, le cloisonnement par défaut est monothread (STA).</span><span class="sxs-lookup"><span data-stu-id="66bb6-151">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="66bb6-152">Dans Windows PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).</span><span class="sxs-lookup"><span data-stu-id="66bb6-152">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="66bb6-153">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="66bb6-153">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="66bb6-154">Démarre la version spécifiée de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-154">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="66bb6-155">La version que vous spécifiez doit être installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="66bb6-155">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="66bb6-156">Si Windows PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="66bb6-156">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="66bb6-157">La valeur par défaut est « 3.0 ».</span><span class="sxs-lookup"><span data-stu-id="66bb6-157">The default value is "3.0".</span></span>

<span data-ttu-id="66bb6-158">Si Windows PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ».</span><span class="sxs-lookup"><span data-stu-id="66bb6-158">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="66bb6-159">Les autres valeurs sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="66bb6-159">Other values are ignored.</span></span>

<span data-ttu-id="66bb6-160">Pour plus d’informations, voir « Installation de Windows PowerShell » dans [Prise en main de Windows PowerShell [ancien MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="66bb6-160">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="66bb6-161">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="66bb6-161">-WindowStyle <Window style></span></span>
<span data-ttu-id="66bb6-162">Définit le style de fenêtre pour la session.</span><span class="sxs-lookup"><span data-stu-id="66bb6-162">Sets the window style for the session.</span></span> <span data-ttu-id="66bb6-163">Les valeurs valides sont Normal, Hidden, Minimized et Maximized.</span><span class="sxs-lookup"><span data-stu-id="66bb6-163">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="66bb6-164">-Command</span><span class="sxs-lookup"><span data-stu-id="66bb6-164">-Command</span></span>
<span data-ttu-id="66bb6-165">Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes Windows PowerShell, puis quitte, sauf si le paramètre NoExit est spécifié.</span><span class="sxs-lookup"><span data-stu-id="66bb6-165">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>

<span data-ttu-id="66bb6-166">La valeur de Command peut être « - », une chaîne</span><span class="sxs-lookup"><span data-stu-id="66bb6-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="66bb6-167">ou un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="66bb6-167">or a script block.</span></span> <span data-ttu-id="66bb6-168">Si la valeur de Command est « - », le texte de commande est lu à partir de l’entrée standard.</span><span class="sxs-lookup"><span data-stu-id="66bb6-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="66bb6-169">Les blocs de script doivent être entourés d’accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="66bb6-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="66bb6-170">Vous pouvez spécifier un bloc de script uniquement lors de l’exécution de PowerShell.exe dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66bb6-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="66bb6-171">Les résultats du script sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, et non en tant qu’objets actifs.</span><span class="sxs-lookup"><span data-stu-id="66bb6-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="66bb6-172">Si la valeur de Command est une chaîne, **Command** doit être le dernier paramètre de la commande, car les caractères tapés après la commande sont interprétés comme étant des arguments de la commande.</span><span class="sxs-lookup"><span data-stu-id="66bb6-172">If the value of Command is a string, **Command** must be the last parameter in the command , because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="66bb6-173">Pour écrire une chaîne exécutant une commande Windows PowerShell, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="66bb6-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="66bb6-174">où les guillemets indiquent une chaîne et l’opérateur d’appel (&) déclenche l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="66bb6-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="66bb6-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="66bb6-175">-Help, -?, /?</span></span>
<span data-ttu-id="66bb6-176">Affiche ce message.</span><span class="sxs-lookup"><span data-stu-id="66bb6-176">Shows this message.</span></span> <span data-ttu-id="66bb6-177">Si vous tapez une commande PowerShell.exe dans Windows PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="66bb6-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="66bb6-178">Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="66bb6-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="66bb6-179">Remarque sur la résolution de problèmes : dans Windows PowerShell 2.0, le démarrage de certains programmes dans la console Windows PowerShell échoue en signalant un LastExitCode de 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="66bb6-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="66bb6-180">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="66bb6-180">EXAMPLES</span></span>

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

