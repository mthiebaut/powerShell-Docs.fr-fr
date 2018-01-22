# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="b1180-101">Installation de PowerShell Core sous macOS et Linux</span><span class="sxs-lookup"><span data-stu-id="b1180-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="b1180-102">Prend en charge [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] et [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="b1180-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="b1180-103">Pour les distributions Linux qui ne sont pas officiellement prises en charge, vous pouvez essayer d’utiliser [AppImage PowerShell][lai].</span><span class="sxs-lookup"><span data-stu-id="b1180-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="b1180-104">Vous pouvez également essayer de déployer des fichiers binaires PowerShell directement à l’aide de [l’archive `tar.gz`][tar] Linux, mais vous devez configurer les dépendances nécessaires selon le système d’exploitation dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="b1180-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b1180-105">Tous les packages sont disponibles dans notre page de [versions][] GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1180-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b1180-106">Une fois que le package est installé, exécutez `pwsh` à partir d’un terminal.</span><span class="sxs-lookup"><span data-stu-id="b1180-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="b1180-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b1180-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="b1180-108">Installation via un dépôt de packages - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b1180-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="b1180-109">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b1180-110">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="b1180-110">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-111">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="b1180-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="b1180-112">Installation par téléchargement direct - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b1180-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="b1180-113">Téléchargez le package Debian `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b1180-113">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b1180-114">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b1180-115">Notez que `dpkg -i` échoue avec des dépendances non satisfaites ; la commande suivante, `apt-get install -f`, les résout et finalise la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="b1180-116">Désinstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b1180-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="b1180-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b1180-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b1180-118">Installation via un dépôt de packages - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b1180-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b1180-119">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b1180-120">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="b1180-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-121">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="b1180-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b1180-122">Installation par téléchargement direct - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b1180-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b1180-123">Téléchargez le package Debian `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b1180-123">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b1180-124">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b1180-125">Notez que `dpkg -i` échoue avec des dépendances non satisfaites ; la commande suivante, `apt-get install -f`, les résout et finalise la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b1180-126">Désinstallation - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b1180-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="b1180-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b1180-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="b1180-128">Installation via un dépôt de packages - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b1180-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="b1180-129">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b1180-130">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="b1180-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-131">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="b1180-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="b1180-132">Installation par téléchargement direct - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b1180-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="b1180-133">Téléchargez le package Debian `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b1180-133">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b1180-134">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b1180-135">Notez que `dpkg -i` échoue avec des dépendances non satisfaites ; la commande suivante, `apt-get install -f`, les résout et finalise la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="b1180-136">Désinstallation - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b1180-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="b1180-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b1180-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b1180-138">Installation via un dépôt de packages - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b1180-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b1180-139">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b1180-140">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="b1180-140">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-141">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="b1180-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="b1180-142">Installation par téléchargement direct - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b1180-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="b1180-143">Téléchargez le package Debian `powershell_6.0.0-rc-1.debian.8_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="b1180-143">Download the Debian package `powershell_6.0.0-rc-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b1180-144">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b1180-145">Notez que `dpkg -i` échoue avec des dépendances non satisfaites ; la commande suivante, `apt-get install -f`, les résout et finalise la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="b1180-146">Désinstallation - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b1180-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="b1180-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b1180-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b1180-148">Installation via un dépôt de packages - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b1180-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b1180-149">PowerShell Core pour Linux est publié dans des dépôts de packages pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b1180-150">Il s’agit de la méthode recommandée.</span><span class="sxs-lookup"><span data-stu-id="b1180-150">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-151">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez par la suite simplement utiliser `sudo apt-get upgrade powershell` pour le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="b1180-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b1180-152">Installation par téléchargement direct - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b1180-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b1180-153">Téléchargez le package Debian `powershell_6.0.0-rc-1.debian.9_amd64.deb` à partir de la page de [versions][] sur l’ordinateur Debian.</span><span class="sxs-lookup"><span data-stu-id="b1180-153">Download the Debian package `powershell_6.0.0-rc-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b1180-154">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b1180-155">Notez que `dpkg -i` échoue avec des dépendances non satisfaites ; la commande suivante, `apt-get install -f`, les résout et finalise la configuration du package PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b1180-156">Désinstallation - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b1180-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b1180-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b1180-157">CentOS 7</span></span>

> <span data-ttu-id="b1180-158">Ce package fonctionne également sur Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="b1180-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b1180-159">Installation via un dépôt de packages (par défaut) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b1180-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b1180-160">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-161">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b1180-162">Installation par téléchargement direct - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b1180-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b1180-163">À l’aide de [CentOS 7][], téléchargez le package RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur CentOS.</span><span class="sxs-lookup"><span data-stu-id="b1180-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="b1180-164">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b1180-165">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="b1180-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b1180-166">Désinstallation - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b1180-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b1180-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b1180-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b1180-169">Installation via un dépôt de packages (par défaut) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b1180-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b1180-170">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b1180-171">Après avoir inscrit le dépôt Microsoft une fois en tant que superutilisateur, vous devez simplement utiliser `sudo yum update powershell` pour mettre à jour PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1180-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b1180-172">Installation par téléchargement direct - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b1180-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b1180-173">Téléchargez le package RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="b1180-173">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="b1180-174">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b1180-175">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="b1180-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b1180-176">Désinstallation - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b1180-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="b1180-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b1180-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="b1180-178">**Remarque :** Lors de l’installation de PowerShell Core, OpenSUSE peut signaler que rien ne fournit `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="b1180-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="b1180-179">`libcurl` doit déjà être installé sur les versions prises en charge d’OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="b1180-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="b1180-180">Exécutez `zypper search libcurl` pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="b1180-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="b1180-181">L’erreur présentera 2 « solutions ».</span><span class="sxs-lookup"><span data-stu-id="b1180-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="b1180-182">Choisissez « Solution 2 » pour poursuivre l’installation de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="b1180-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="b1180-183">Installation via un dépôt de packages (par défaut) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b1180-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="b1180-184">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="b1180-185">Installation par téléchargement direct - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b1180-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="b1180-186">Téléchargez le package RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="b1180-186">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b1180-187">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="b1180-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="b1180-188">Désinstallation - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b1180-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="b1180-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b1180-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="b1180-190">Installation via un dépôt de packages (par défaut) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b1180-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="b1180-191">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="b1180-192">Installation par téléchargement direct - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b1180-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="b1180-193">Téléchargez le package RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="b1180-193">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b1180-194">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b1180-195">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="b1180-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="b1180-196">Désinstallation - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b1180-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="b1180-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b1180-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="b1180-198">Installation via un dépôt de packages (par défaut) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b1180-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="b1180-199">PowerShell Core pour Linux est publié dans des dépôts Microsoft officiels pour faciliter l’installation (et les mises à jour).</span><span class="sxs-lookup"><span data-stu-id="b1180-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="b1180-200">Installation par téléchargement direct - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b1180-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="b1180-201">Téléchargez le package RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` à partir de la page de [versions][] sur l’ordinateur Fedora.</span><span class="sxs-lookup"><span data-stu-id="b1180-201">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b1180-202">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b1180-203">Vous pouvez également installer le package RPM sans l’étape intermédiaire de téléchargement :</span><span class="sxs-lookup"><span data-stu-id="b1180-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="b1180-204">Désinstallation - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b1180-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b1180-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="b1180-205">Arch Linux</span></span>

<span data-ttu-id="b1180-206">PowerShell est disponible dans le dépôt utilisateur [Arch Linux][].</span><span class="sxs-lookup"><span data-stu-id="b1180-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b1180-207">Il peut être compilé avec la [dernière version identifiée][arch-release]</span><span class="sxs-lookup"><span data-stu-id="b1180-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b1180-208">Il peut être compilé à partir de la [dernière validation sur le maître][arch-git]</span><span class="sxs-lookup"><span data-stu-id="b1180-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b1180-209">Il peut être installé à l’aide de la [dernière ressource binaire de version][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="b1180-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b1180-210">Les packages dans le dépôt utilisateur Arch Linux sont gérés par la communauté ; il n’existe aucune prise en charge officielle.</span><span class="sxs-lookup"><span data-stu-id="b1180-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="b1180-211">Pour plus d’informations sur l’installation de packages à partir du dépôt utilisateur Arch Linux, consultez le [Wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou le [fichier Dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la communauté.</span><span class="sxs-lookup"><span data-stu-id="b1180-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="b1180-213">AppImage Linux</span><span class="sxs-lookup"><span data-stu-id="b1180-213">Linux AppImage</span></span>

<span data-ttu-id="b1180-214">En utilisant une distribution Linux récente, téléchargez AppImage `powershell-6.0.0-rc-x86_64.AppImage` à partir de la page de [versions][] sur l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="b1180-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-rc-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="b1180-215">Exécutez ensuite le code suivant dans le terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

<span data-ttu-id="b1180-216">[AppImage][] vous permet d’exécuter PowerShell sans l’installer.</span><span class="sxs-lookup"><span data-stu-id="b1180-216">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="b1180-217">Il s’agit d’une application portable qui regroupe PowerShell et ses dépendances (dont les dépendances système de .NET Core) en un package cohérent.</span><span class="sxs-lookup"><span data-stu-id="b1180-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="b1180-218">Ce package fonctionne indépendamment de la distribution Linux de l’utilisateur et est un fichier binaire unique.</span><span class="sxs-lookup"><span data-stu-id="b1180-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="b1180-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b1180-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="b1180-221">Installation via Homebrew (par défaut) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b1180-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="b1180-222">[Homebrew][brew] est le gestionnaire de package manquant pour macOS.</span><span class="sxs-lookup"><span data-stu-id="b1180-222">[Homebrew][brew] is the missing package manager for macOS.</span></span>
<span data-ttu-id="b1180-223">Si la commande `brew` est introuvable, vous devez installer Homebrew en suivant [leurs instructions][brew].</span><span class="sxs-lookup"><span data-stu-id="b1180-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="b1180-224">Une fois que vous avez installé Homebrew, l’installation de PowerShell est facile.</span><span class="sxs-lookup"><span data-stu-id="b1180-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="b1180-225">Pour commencer, installez [Homebrew-Cask][cask] afin de pouvoir installer d’autres packages :</span><span class="sxs-lookup"><span data-stu-id="b1180-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="b1180-226">Maintenant, vous pouvez installer PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b1180-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b1180-227">Quand de nouvelles versions de PowerShell sont publiées, mettez simplement à jour les formules de Homebrew et mettez à niveau PowerShell :</span><span class="sxs-lookup"><span data-stu-id="b1180-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="b1180-228">Remarque : En raison de [ce problème dans Cask](https://github.com/caskroom/homebrew-cask/issues/29301), vous devez pour l’instant effectuer une réinstallation afin de procéder à la mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="b1180-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="b1180-229">Installation par téléchargement direct - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b1180-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="b1180-230">À l’aide de macOS 10.12, téléchargez le package PKG `powershell-6.0.0-rc-osx.10.12-x64.pkg` à partir de la page de [versions][] sur l’ordinateur macOS.</span><span class="sxs-lookup"><span data-stu-id="b1180-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-rc-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="b1180-231">Double-cliquez sur le fichier et suivez les invites ou installez-le à partir du terminal :</span><span class="sxs-lookup"><span data-stu-id="b1180-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="b1180-232">Désinstallation - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b1180-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="b1180-233">Si vous avez installé PowerShell avec Homebrew, la désinstallation est simple :</span><span class="sxs-lookup"><span data-stu-id="b1180-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b1180-234">Si vous avez installé PowerShell par téléchargement direct, PowerShell doit être supprimé manuellement :</span><span class="sxs-lookup"><span data-stu-id="b1180-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b1180-235">Pour désinstaller les chemins PowerShell supplémentaires (par exemple, le chemin du profil utilisateur), consultez la section sur les [chemins][paths] ci-dessous dans ce document et supprimez les chemins souhaités avec `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b1180-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span>
<span data-ttu-id="b1180-236">(Remarque : Cela est inutile si vous avez installé PowerShell avec Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="b1180-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="b1180-237">Kali</span><span class="sxs-lookup"><span data-stu-id="b1180-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="b1180-238">Installation</span><span class="sxs-lookup"><span data-stu-id="b1180-238">Installation</span></span>

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="b1180-239">Exécuter PowerShell dans la dernière version de Kali (publication en continu Kali GNU/Linux) sans l’installer</span><span class="sxs-lookup"><span data-stu-id="b1180-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b1180-240">Désinstallation - Kali</span><span class="sxs-lookup"><span data-stu-id="b1180-240">Uninstallation - Kali</span></span>

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="b1180-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b1180-241">Raspbian</span></span>

<span data-ttu-id="b1180-242">Actuellement, PowerShell est uniquement pris en charge sur Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="b1180-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="b1180-243">Installation</span><span class="sxs-lookup"><span data-stu-id="b1180-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b1180-244">Désinstallation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="b1180-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b1180-245">Archives binaires</span><span class="sxs-lookup"><span data-stu-id="b1180-245">Binary Archives</span></span>

<span data-ttu-id="b1180-246">Les archives `tar.gz` binaires PowerShell sont fournies pour les plateformes macOS et Linux afin de permettre des scénarios de déploiement avancés.</span><span class="sxs-lookup"><span data-stu-id="b1180-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b1180-247">Dépendances</span><span class="sxs-lookup"><span data-stu-id="b1180-247">Dependencies</span></span>

<span data-ttu-id="b1180-248">Pour Linux, PowerShell génère des binaires portables pour toutes les distributions Linux.</span><span class="sxs-lookup"><span data-stu-id="b1180-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="b1180-249">Toutefois, le runtime .NET Core nécessite différentes dépendances sur différentes distributions et PowerShell se comporte par conséquent de la même manière.</span><span class="sxs-lookup"><span data-stu-id="b1180-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="b1180-250">Le graphique suivant montre les dépendances .NET Core 2.0 sur différentes distributions Linux prises en charge officiellement.</span><span class="sxs-lookup"><span data-stu-id="b1180-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="b1180-251">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="b1180-251">OS</span></span>                 | <span data-ttu-id="b1180-252">Dépendances</span><span class="sxs-lookup"><span data-stu-id="b1180-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b1180-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b1180-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="b1180-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b1180-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b1180-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b1180-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b1180-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b1180-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="b1180-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b1180-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b1180-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b1180-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b1180-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b1180-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="b1180-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b1180-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b1180-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b1180-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b1180-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b1180-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b1180-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b1180-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b1180-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b1180-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b1180-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="b1180-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b1180-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b1180-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b1180-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b1180-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b1180-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b1180-268">CentOS 7</span></span> <br> <span data-ttu-id="b1180-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b1180-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="b1180-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b1180-270">RHEL 7</span></span> <br> <span data-ttu-id="b1180-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b1180-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="b1180-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b1180-272">Fedora 25</span></span> | <span data-ttu-id="b1180-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="b1180-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b1180-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b1180-274">Fedora 26</span></span>          | <span data-ttu-id="b1180-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="b1180-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b1180-276">Pour déployer les fichiers binaires PowerShell sur les distributions Linux qui ne sont pas officiellement prises en charge, vous devez installer les dépendances nécessaires pour le système d’exploitation cible dans une procédure distincte.</span><span class="sxs-lookup"><span data-stu-id="b1180-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="b1180-277">Par exemple, notre [fichier Dockerfile Amazon Linux][amazon-dockerfile] installe tout d’abord les dépendances, puis extrait l’archive `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="b1180-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b1180-278">Installation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="b1180-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b1180-279">Linux</span><span class="sxs-lookup"><span data-stu-id="b1180-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="b1180-280">macOS</span><span class="sxs-lookup"><span data-stu-id="b1180-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="b1180-281">Désinstallation - Archives binaires</span><span class="sxs-lookup"><span data-stu-id="b1180-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b1180-282">Linux</span><span class="sxs-lookup"><span data-stu-id="b1180-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="b1180-283">macOS</span><span class="sxs-lookup"><span data-stu-id="b1180-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b1180-284">Chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="b1180-284">Paths</span></span>

* <span data-ttu-id="b1180-285">`$PSHOME` est `/opt/microsoft/powershell/6.0.0-rc/`</span><span class="sxs-lookup"><span data-stu-id="b1180-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0-rc/`</span></span>
* <span data-ttu-id="b1180-286">Les profils utilisateur sont lus à partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b1180-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b1180-287">Les profils par défaut sont lus à partir de `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b1180-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b1180-288">Les modules utilisateur sont lus à partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b1180-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b1180-289">Les modules partagés sont lus à partir de `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b1180-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b1180-290">Les modules par défaut sont lus à partir de `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b1180-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b1180-291">L’historique PSReadline est enregistré dans `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b1180-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b1180-292">Les profils respectant la configuration par hôte de PowerShell, les profils spécifiques à l’hôte par défaut existent sur `Microsoft.PowerShell_profile.ps1` aux mêmes emplacements.</span><span class="sxs-lookup"><span data-stu-id="b1180-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b1180-293">Sur Linux et macOS, la [spécification de répertoire de base XDG][xdg-bds] est respectée.</span><span class="sxs-lookup"><span data-stu-id="b1180-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="b1180-294">Notez que, comme macOS est une dérivation de BSD, au lieu de `/opt`, le préfixe utilisé est `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="b1180-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span>
<span data-ttu-id="b1180-295">Par conséquent, `$PSHOME` est `/usr/local/microsoft/powershell/6.0.0-rc/`, et le lien symbolique est placé sur `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="b1180-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versions]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
