# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="5e14c-101">Utilisation de Visual Studio Code pour le développement PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e14c-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="5e14c-102">En plus de [PowerShell ISE][ise], PowerShell est également bien pris en charge dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5e14c-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="5e14c-103">De plus, l’environnement ISE n’est pas pris en charge avec PowerShell Core, alors que Visual Studio Code est pris en charge pour PowerShell Core sur toutes les plateformes (macOS, Windows et Linux)</span><span class="sxs-lookup"><span data-stu-id="5e14c-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="5e14c-104">Vous pouvez utiliser Visual Studio Code sur Windows avec PowerShell version 5 avec Windows 10 ou en installant [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) pour les systèmes d’exploitation Windows d’une version antérieure (par exemple Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="5e14c-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="5e14c-105">Avant de le démarrer, vérifiez que PowerShell est présent sur votre système.</span><span class="sxs-lookup"><span data-stu-id="5e14c-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="5e14c-106">Pour les charges de travail modernes sur Windows, macOS et Linux, consultez :</span><span class="sxs-lookup"><span data-stu-id="5e14c-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="5e14c-107">[Installation de PowerShell Core sur macOS et Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="5e14c-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="5e14c-108">[Installation de PowerShell Core sur Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="5e14c-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="5e14c-109">Pour les charges de travail Windows PowerShell classiques, consultez [Installation de Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="5e14c-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="5e14c-110">Édition avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="5e14c-111">1. Installation de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="5e14c-112">**Linux** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="5e14c-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="5e14c-113">**macOS** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="5e14c-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e14c-114">Sur macOS, vous devez installer OpenSSL pour que l’extension PowerShell fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="5e14c-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="5e14c-115">Le moyen le plus simple de le faire est d’installer [Homebrew](http://brew.sh/), puis d’exécuter `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="5e14c-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="5e14c-116">L’extension PowerShell peut maintenant se charger correctement.</span><span class="sxs-lookup"><span data-stu-id="5e14c-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="5e14c-117">**Windows** : suivez les instructions d’installation sur la page [Exécution de Visual Studio Code sur Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="5e14c-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="5e14c-118">2. Installation de l’extension PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e14c-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="5e14c-119">Lancez l’application Visual Studio Code comme suit :</span><span class="sxs-lookup"><span data-stu-id="5e14c-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="5e14c-120">**Windows** : en tapant `code` dans votre session PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e14c-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="5e14c-121">**Linux** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="5e14c-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="5e14c-122">**macOS** : en tapant `code` dans votre terminal</span><span class="sxs-lookup"><span data-stu-id="5e14c-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="5e14c-123">Lancez **Quick Open** en appuyant sur **Ctrl+P** (**Cmd+P** sur Mac).</span><span class="sxs-lookup"><span data-stu-id="5e14c-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="5e14c-124">Dans Quick Open, tapez `ext install powershell`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="5e14c-125">La vue **Extensions** s’ouvre dans la barre latérale.</span><span class="sxs-lookup"><span data-stu-id="5e14c-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="5e14c-126">Sélectionnez l’extension de PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e14c-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="5e14c-127">Vous voyez quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="5e14c-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="5e14c-129">Cliquez sur le bouton **Installer** sur l’extension PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e14c-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="5e14c-130">Après l’installation, vous voyez le bouton **Installer** se changer en **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="5e14c-131">Cliquez sur **Recharger**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-131">Click on **Reload**.</span></span>
- <span data-ttu-id="5e14c-132">Une fois Visual Studio Code rechargé, vous êtes prêt pour l’édition.</span><span class="sxs-lookup"><span data-stu-id="5e14c-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="5e14c-133">Par exemple, pour créer un fichier, cliquez sur **Fichier->Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="5e14c-134">Pour l’enregistrer, cliquez sur **Fichier->Enregistrer**, puis indiquez un nom de fichier, disons `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="5e14c-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="5e14c-135">Pour fermer le fichier, cliquez sur « x » en regard du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="5e14c-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="5e14c-136">Pour quitter Visual Studio Code, cliquez sur **Fichier->Quitter**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="5e14c-137">Utilisation d’une version installée spécifique de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e14c-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="5e14c-138">Si vous voulez utiliser une installation spécifique de PowerShell avec Visual Studio Code, vous devez ajouter une nouvelle variable à votre fichier de paramètres utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e14c-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="5e14c-139">Cliquez sur **Fichier -> Préférences -> Paramètres**</span><span class="sxs-lookup"><span data-stu-id="5e14c-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="5e14c-140">Deux volets de l’éditeur apparaissent.</span><span class="sxs-lookup"><span data-stu-id="5e14c-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="5e14c-141">Dans le volet le plus à droite (`settings.json`), insérez le paramètre ci-dessous approprié pour votre système d’exploitation quelque part entre les deux accolades (`{` et `}`) et remplacez *<version>* par la version installée de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5e14c-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="5e14c-142">Remplacez le paramètre par le chemin vers l’exécutable PowerShell souhaité</span><span class="sxs-lookup"><span data-stu-id="5e14c-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="5e14c-143">Enregistrez le fichier de paramètres et redémarrez Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="5e14c-144">Paramètres de configuration de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="5e14c-145">En suivant la procédure décrite dans le paragraphe précédent, vous pouvez ajouter des paramètres de configuration dans `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="5e14c-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="5e14c-146">Nous recommandons les paramètres de configuration suivants pour Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="5e14c-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="5e14c-147">Débogage avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="5e14c-148">Débogage sans espace de travail</span><span class="sxs-lookup"><span data-stu-id="5e14c-148">No-workspace debugging</span></span>

<span data-ttu-id="5e14c-149">À compter de Visual Studio Code version 1.9, vous pouvez déboguer des scripts PowerShell sans avoir à ouvrir le dossier contenant le script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e14c-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="5e14c-150">Ouvrez simplement le fichier de script PowerShell avec **Fichier->Ouvrir un fichier...**, définissez un point d’arrêt sur une ligne (appuyez sur F9), puis appuyez sur F5 pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="5e14c-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="5e14c-151">Vous voyez apparaître le volet Actions de débogage, qui vous permet de vous arrêter dans le débogueur, d’effectuer un pas à pas détaillé, de reprendre et d’arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="5e14c-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="5e14c-152">Débogage d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="5e14c-152">Workspace debugging</span></span>

<span data-ttu-id="5e14c-153">Le débogage d’espace de travail fait référence au débogage dans le contexte d’un dossier que vous avez ouvert dans Visual Studio Code en utilisant **Ouvrir un dossier...**  à partir du menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="5e14c-154">Le dossier que vous ouvrez est généralement votre dossier de projet PowerShell et/ou la racine de votre dépôt Git.</span><span class="sxs-lookup"><span data-stu-id="5e14c-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="5e14c-155">Même dans ce mode, vous pouvez démarrer le débogage du script PowerShell actuellement sélectionné en appuyant simplement sur F5.</span><span class="sxs-lookup"><span data-stu-id="5e14c-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="5e14c-156">Cependant, le débogage d’espace de travail vous permet de définir plusieurs configurations de débogage autres que simplement déboguer le fichier actuellement ouvert.</span><span class="sxs-lookup"><span data-stu-id="5e14c-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="5e14c-157">Par exemple, vous pouvez ajouter des configurations pour :</span><span class="sxs-lookup"><span data-stu-id="5e14c-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="5e14c-158">Lancer des tests Pester dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="5e14c-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="5e14c-159">Lancer un fichier spécifique avec des arguments dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="5e14c-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="5e14c-160">Lancer une session interactive dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="5e14c-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="5e14c-161">Attacher le débogueur à un processus hôte PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e14c-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="5e14c-162">Suivez ces étapes pour créer votre fichier de configuration de débogage :</span><span class="sxs-lookup"><span data-stu-id="5e14c-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="5e14c-163">Ouvrez la vue **Déboguer** en appuyant sur **Ctrl+Maj+D** (**Cmd+Maj+D** sur Mac).</span><span class="sxs-lookup"><span data-stu-id="5e14c-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="5e14c-164">Appuyez sur l’icône d’engrenage **Configurer** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="5e14c-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="5e14c-165">Visual Studio Code vous invite à **Sélectionner un environnement**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="5e14c-166">Choisissez **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="5e14c-167">Dans ce cas, Visual Studio Code crée un répertoire et un fichier «.vscode\launch.json » à la racine du dossier de votre espace de travail.</span><span class="sxs-lookup"><span data-stu-id="5e14c-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="5e14c-168">C’est là que votre configuration de débogage est stockée.</span><span class="sxs-lookup"><span data-stu-id="5e14c-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="5e14c-169">Si vos fichiers sont dans un dépôt Git, vous souhaitez généralement valider le fichier launch.json.</span><span class="sxs-lookup"><span data-stu-id="5e14c-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="5e14c-170">Le contenu du fichier launch.json est :</span><span class="sxs-lookup"><span data-stu-id="5e14c-170">The contents of the launch.json file are:</span></span>

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
}
```

<span data-ttu-id="5e14c-171">Ceci représente les scénarios de débogage courants.</span><span class="sxs-lookup"><span data-stu-id="5e14c-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="5e14c-172">Cependant, quand vous ouvrez ce fichier dans l’éditeur, vous voyez un bouton **Ajouter une configuration...**</span><span class="sxs-lookup"><span data-stu-id="5e14c-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="5e14c-173">Vous pouvez appuyer sur ce bouton pour ajouter d’autres configurations de débogage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e14c-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="5e14c-174">**PowerShell : Lancer un script** est une configuration très pratique que vous pouvez ajouter.</span><span class="sxs-lookup"><span data-stu-id="5e14c-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="5e14c-175">Avec cette configuration, vous pouvez spécifier un fichier spécifique avec des arguments facultatifs, qui doit être lancé quand vous appuyez sur F5, quel que soit le fichier actif dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="5e14c-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="5e14c-176">Une fois établie la configuration de débogage, vous pouvez choisir la configuration à utiliser pendant une session de débogage en la sélectionnant dans la liste déroulante des configurations de débogage de la barre d’outils de la vue **Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="5e14c-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="5e14c-177">Quelques blogs peuvent être utiles pour vous aider à prendre en main l’extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="5e14c-178">Visual Studio Code : [Extension PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="5e14c-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="5e14c-179">[Écrire et déboguer des scripts PowerShell dans Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="5e14c-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="5e14c-180">[Aide sur le débogage avec Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="5e14c-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="5e14c-181">[Débogage de PowerShell dans Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="5e14c-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="5e14c-182">[Guide pratique pour le développement avec PowerShell dans Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="5e14c-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="5e14c-183">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="5e14c-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="5e14c-184">[Fonctionnalités d’édition de Visual Studio Code pour le développement avec PowerShell – Partie 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="5e14c-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="5e14c-185">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="5e14c-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="5e14c-186">[Débogage des scripts PowerShell dans Visual Studio Code – Partie 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="5e14c-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="5e14c-187">Extension PowerShell pour Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e14c-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="5e14c-188">Vous trouverez le code source de l’extension PowerShell sur [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5e14c-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>