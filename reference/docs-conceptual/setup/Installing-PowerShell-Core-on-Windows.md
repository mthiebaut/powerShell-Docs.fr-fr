# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="ca4cd-101">Installation de PowerShell Core sous Windows</span><span class="sxs-lookup"><span data-stu-id="ca4cd-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="ca4cd-102">MSI</span><span class="sxs-lookup"><span data-stu-id="ca4cd-102">MSI</span></span>

<span data-ttu-id="ca4cd-103">Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="ca4cd-104">Le fichier MSI ressemble à ceci : `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="ca4cd-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="ca4cd-105">Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="ca4cd-106">Un raccourci est placé dans le menu Démarrer lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="ca4cd-107">Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="ca4cd-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="ca4cd-108">Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="ca4cd-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ca4cd-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ca4cd-109">Prerequisites</span></span>

<span data-ttu-id="ca4cd-110">Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :</span><span class="sxs-lookup"><span data-stu-id="ca4cd-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="ca4cd-111">Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="ca4cd-112">Il est disponible par téléchargement direct ou sur Windows Update.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="ca4cd-113">Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).</span><span class="sxs-lookup"><span data-stu-id="ca4cd-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="ca4cd-114">Installer WMF (Windows Management Framework) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ou une version ultérieure ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="ca4cd-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="ca4cd-115">ZIP</span></span>

<span data-ttu-id="ca4cd-116">Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="ca4cd-117">Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="ca4cd-118">Ainsi, pour que la communication à distance via WSMan puisse fonctionner correctement sur les versions de Windows antérieures à Windows 10, vous devez vérifier que ces [conditions préalables](#prerequisites) sont remplies.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="ca4cd-119">Déploiement sur Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca4cd-119">Deploying on Nano Server</span></span>

<span data-ttu-id="ca4cd-120">Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="ca4cd-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="ca4cd-121">Nano Server est un système d’exploitation « sans périphérique de contrôle » et le déploiement des fichiers binaires PowerShell Core peut se dérouler de deux manières différentes :</span><span class="sxs-lookup"><span data-stu-id="ca4cd-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="ca4cd-122">Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="ca4cd-123">En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="ca4cd-124">Dans les deux cas, vous avez besoin du package de la version Zip Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».</span><span class="sxs-lookup"><span data-stu-id="ca4cd-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="ca4cd-125">Déploiement hors connexion de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ca4cd-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="ca4cd-126">Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="ca4cd-127">Démontez l’image et démarrez-la.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="ca4cd-128">Connectez-vous à l’instance de boîte de réception de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="ca4cd-129">Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [technique d’une autre instance](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="ca4cd-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="ca4cd-130">Déploiement en ligne de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="ca4cd-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="ca4cd-131">La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="ca4cd-132">Connectez-vous à l’instance de boîte de réception de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca4cd-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="ca4cd-133">Copiez le fichier sur l’instance de Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca4cd-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="ca4cd-134">Entrez dans la session</span><span class="sxs-lookup"><span data-stu-id="ca4cd-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="ca4cd-135">Extrayez le fichier Zip</span><span class="sxs-lookup"><span data-stu-id="ca4cd-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="ca4cd-136">Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [technique d’une autre instance](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="ca4cd-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="ca4cd-137">Instructions pour créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="ca4cd-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="ca4cd-138">PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="ca4cd-139">Pour plus d’informations, voir :</span><span class="sxs-lookup"><span data-stu-id="ca4cd-139">For more information, see:</span></span>

* <span data-ttu-id="ca4cd-140">[Communication à distance SSH dans PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="ca4cd-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="ca4cd-141">[Communication à distance WSMan dans PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="ca4cd-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="ca4cd-142">Instructions d’installation des artefacts</span><span class="sxs-lookup"><span data-stu-id="ca4cd-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="ca4cd-143">Nous publions une archive avec des bits CoreCLR sur chaque build CI avec [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="ca4cd-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="ca4cd-144">Artefacts CoreCLR</span><span class="sxs-lookup"><span data-stu-id="ca4cd-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="ca4cd-145">Téléchargez le package zip à partir de l’onglet des **artefacts** de la build particulière.</span><span class="sxs-lookup"><span data-stu-id="ca4cd-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="ca4cd-146">Débloquez le fichier zip : cliquez avec le bouton droit dans l’Explorateur de fichiers -> Propriétés -> cochez la case Débloquer -> Appliquer</span><span class="sxs-lookup"><span data-stu-id="ca4cd-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="ca4cd-147">Extrayez le fichier zip dans le répertoire `bin`</span><span class="sxs-lookup"><span data-stu-id="ca4cd-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versions]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
