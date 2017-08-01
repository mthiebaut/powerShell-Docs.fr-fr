---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "déploiement et maintenance de plusieurs ordinateurs"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="fb603-103">Déploiement et maintenance de plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="fb603-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="fb603-104">À ce stade, vous avez plusieurs fois déployé JEA sur des systèmes locaux.</span><span class="sxs-lookup"><span data-stu-id="fb603-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="fb603-105">Étant donné que votre environnement de production comprend probablement plusieurs ordinateurs, il est important de parcourir les étapes critiques du processus de déploiement qui doivent être répétées sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fb603-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="fb603-106">Étapes générales :</span><span class="sxs-lookup"><span data-stu-id="fb603-106">High Level Steps:</span></span>
1.  <span data-ttu-id="fb603-107">Copiez vos modules (avec des capacités de rôle) sur chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="fb603-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="fb603-108">Copiez vos fichiers de configuration de session sur chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="fb603-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="fb603-109">Exécutez `Register-PSSessionConfiguration` avec votre configuration de session.</span><span class="sxs-lookup"><span data-stu-id="fb603-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="fb603-110">Conservez une copie de votre configuration de session et de vos kits de ressources à un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fb603-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="fb603-111">Pendant que vous apportez des modifications, il est toujours intéressant de disposer d’une « seule source de vérité ».</span><span class="sxs-lookup"><span data-stu-id="fb603-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="fb603-112">Exemple de script</span><span class="sxs-lookup"><span data-stu-id="fb603-112">Example Script</span></span>
<span data-ttu-id="fb603-113">Voici un exemple de script de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fb603-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="fb603-114">Pour l’utiliser dans votre environnement, vous devrez utiliser les noms/chemins de partages de fichiers et modules réels.</span><span class="sxs-lookup"><span data-stu-id="fb603-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
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
## <a name="modifying-capabilities"></a><span data-ttu-id="fb603-115">Modification des capacités</span><span class="sxs-lookup"><span data-stu-id="fb603-115">Modifying Capabilities</span></span>
<span data-ttu-id="fb603-116">Quand vous vous occupez d’un grand nombre d’ordinateurs, il est important que les modifications soient introduites de façon cohérente.</span><span class="sxs-lookup"><span data-stu-id="fb603-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="fb603-117">Une fois que JEA a une ressource DSC, votre environnement est synchronisé.</span><span class="sxs-lookup"><span data-stu-id="fb603-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="fb603-118">En attendant, nous vous recommandons vivement de conserver une copie principale de vos configurations de session et de redéployer chaque fois que vous apportez une modification.</span><span class="sxs-lookup"><span data-stu-id="fb603-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="fb603-119">Suppression de capacités</span><span class="sxs-lookup"><span data-stu-id="fb603-119">Removing Capabilities</span></span>
<span data-ttu-id="fb603-120">Pour supprimer votre configuration JEA de vos systèmes, utilisez la commande suivante sur chaque ordinateur :</span><span class="sxs-lookup"><span data-stu-id="fb603-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

