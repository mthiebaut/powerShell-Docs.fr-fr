# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="259dd-101">Accès distant à WS-Management (WSMan) dans PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="259dd-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="259dd-102">Instructions pour créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="259dd-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="259dd-103">Le package PowerShell Core pour Windows inclut un plug-in WinRM (`pwrshplugin.dll`) et un script d’installation (`Install-PowerShellRemoting.ps1`) dans `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="259dd-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="259dd-104">Ces fichiers permettent à PowerShell d’accepter les connexions à distance PowerShell entrantes quand son point de terminaison est spécifié.</span><span class="sxs-lookup"><span data-stu-id="259dd-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="259dd-105">Motivation</span><span class="sxs-lookup"><span data-stu-id="259dd-105">Motivation</span></span>

<span data-ttu-id="259dd-106">Une installation de PowerShell peut établir des sessions PowerShell sur des ordinateurs distants avec `New-PSSession` et `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="259dd-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="259dd-107">Pour lui permettre d’accepter les connexions à distance PowerShell, l’utilisateur doit créer un point de terminaison d’accès distant WinRM.</span><span class="sxs-lookup"><span data-stu-id="259dd-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="259dd-108">Il s’agit d’un scénario à choisir explicitement là où l’utilisateur exécute Install-PowerShellRemoting.ps1 pour créer le point de terminaison WinRM.</span><span class="sxs-lookup"><span data-stu-id="259dd-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="259dd-109">Le script d’installation est une solution à court terme jusqu’à ce que nous ajoutions une fonctionnalité supplémentaire à `Enable-PSRemoting` pour effectuer la même action.</span><span class="sxs-lookup"><span data-stu-id="259dd-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="259dd-110">Pour plus d’informations, reportez-vous au problème [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="259dd-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="259dd-111">Actions du script</span><span class="sxs-lookup"><span data-stu-id="259dd-111">Script Actions</span></span>

<span data-ttu-id="259dd-112">Le script</span><span class="sxs-lookup"><span data-stu-id="259dd-112">The script</span></span>

1. <span data-ttu-id="259dd-113">Crée un répertoire pour le plug-in dans %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="259dd-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="259dd-114">Copie pwrshplugin.dll à cet emplacement</span><span class="sxs-lookup"><span data-stu-id="259dd-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="259dd-115">Génère un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="259dd-115">Generates a configuration file</span></span>
1. <span data-ttu-id="259dd-116">Inscrit ce plug-in auprès de WinRM</span><span class="sxs-lookup"><span data-stu-id="259dd-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="259dd-117">Inscription</span><span class="sxs-lookup"><span data-stu-id="259dd-117">Registration</span></span>

<span data-ttu-id="259dd-118">Le script doit être exécuté dans une session PowerShell de niveau administrateur et il s’exécute dans deux modes.</span><span class="sxs-lookup"><span data-stu-id="259dd-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="259dd-119">Exécuté par l’instance de PowerShell qu’il inscrira</span><span class="sxs-lookup"><span data-stu-id="259dd-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="259dd-120">Exécuté par une autre instance de PowerShell pour le compte de l’instance qu’il inscrira</span><span class="sxs-lookup"><span data-stu-id="259dd-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="259dd-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="259dd-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="259dd-122">**REMARQUE :** Le script d’inscription de l’accès distant doit redémarrer WinRM : toutes les sessions PSRP existantes seront donc terminées immédiatement après l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="259dd-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="259dd-123">S’il est exécuté pendant une session à distance, ceci mettra fin à la connexion.</span><span class="sxs-lookup"><span data-stu-id="259dd-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="259dd-124">Comment se connecter à un nouveau point de terminaison</span><span class="sxs-lookup"><span data-stu-id="259dd-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="259dd-125">Créez une session PowerShell sur le nouveau point de terminaison PowerShell en spécifiant `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="259dd-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="259dd-126">Pour vous connecter à l’instance PowerShell de l’exemple ci-dessus, utilisez :</span><span class="sxs-lookup"><span data-stu-id="259dd-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="259dd-127">Notez que les appels de `New-PSSession` et de `Enter-PSSession` qui ne spécifient pas `-ConfigurationName` ciblent le point de terminaison PowerShell par défaut, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="259dd-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>