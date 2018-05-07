# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="c0e59-101">Installation de PowerShell Core sous macOS</span><span class="sxs-lookup"><span data-stu-id="c0e59-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="c0e59-102">PowerShell Core prend en charge macOS 10.12 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c0e59-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="c0e59-103">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="c0e59-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c0e59-104">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="c0e59-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="c0e59-105">Installation via Homebrew sous macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="c0e59-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="c0e59-106">[Homebrew][brew] est le gestionnaire de package préféré pour macOS.</span><span class="sxs-lookup"><span data-stu-id="c0e59-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="c0e59-107">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="c0e59-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="c0e59-108">Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.</span><span class="sxs-lookup"><span data-stu-id="c0e59-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="c0e59-109">Pour commencer, installez [Homebrew-Cask][cask] afin de pouvoir installer d’autres packages :</span><span class="sxs-lookup"><span data-stu-id="c0e59-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="c0e59-110">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0e59-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="c0e59-111">Enfin, vérifiez que votre installation fonctionne correctement :</span><span class="sxs-lookup"><span data-stu-id="c0e59-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="c0e59-112">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="c0e59-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="c0e59-113">Les commandes ci-dessus peuvent être appelées à partir d’un ordinateur hôte PowerShell (pwsh). Dans ce cas, vous devez quitter l’interpréteur de commandes PowerShell, puis le redémarrer pour terminer la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="c0e59-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="c0e59-114">et actualiser les valeurs indiquées dans $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="c0e59-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="c0e59-115">Installation par téléchargement direct</span><span class="sxs-lookup"><span data-stu-id="c0e59-115">Installation via Direct Download</span></span>

<span data-ttu-id="c0e59-116">Téléchargez le package PKG `powershell-6.0.2-osx.10.12-x64.pkg` à partir de la page de [versions][] sur votre ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="c0e59-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="c0e59-117">Vous pouvez double-cliquer sur le fichier et suivre les invites ou l’installer à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="c0e59-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="c0e59-118">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="c0e59-118">Binary Archives</span></span>

<span data-ttu-id="c0e59-119">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes macOS et Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="c0e59-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="c0e59-120">Installation des archives binaires sur macOS</span><span class="sxs-lookup"><span data-stu-id="c0e59-120">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="c0e59-121">Désinstallation de PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c0e59-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="c0e59-122">Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :</span><span class="sxs-lookup"><span data-stu-id="c0e59-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="c0e59-123">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="c0e59-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c0e59-124">Pour supprimer les chemins PowerShell supplémentaires, consultez la section sur les [chemins][] dans ce document et supprimez les chemins souhaités avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="c0e59-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="c0e59-125">Cela est inutile si vous avez installé PowerShell avec Homebrew.</span><span class="sxs-lookup"><span data-stu-id="c0e59-125">This is not necessary if you installed with Homebrew.</span></span>

[chemins]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="c0e59-127">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="c0e59-127">Paths</span></span>

* <span data-ttu-id="c0e59-128">`$PSHOME` est `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="c0e59-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="c0e59-129">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c0e59-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c0e59-130">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c0e59-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c0e59-131">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0e59-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c0e59-132">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0e59-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c0e59-133">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c0e59-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c0e59-134">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c0e59-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c0e59-135">Les profils respectent la configuration par hôte de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0e59-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="c0e59-136">Donc, les profils spécifiques à l’hôte par défaut existent dans `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="c0e59-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c0e59-137">PowerShell respecte la [spécification de répertoire de base XDG][xdg-bds] sur macOS.</span><span class="sxs-lookup"><span data-stu-id="c0e59-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="c0e59-138">Étant donné que macOS est une dérivation de BSD, le préfixe `/usr/local` est utilisé au lieu de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="c0e59-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="c0e59-139">Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.0.0/`, et le lien symbolique est placé sur `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="c0e59-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
