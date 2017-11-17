---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 81ce13a082ad1d7a13ba5fd76a7595b55708f54e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="28538-102">Inscrire un dépôt PowerShell</span><span class="sxs-lookup"><span data-stu-id="28538-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="28538-103">Vous pouvez configurer PowerShellGet pour qu’il opère sur des dépôts internes.</span><span class="sxs-lookup"><span data-stu-id="28538-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="28538-104">Vous devez pour cela utiliser les ajouts suivants :</span><span class="sxs-lookup"><span data-stu-id="28538-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="28538-105">Register-PSRepository : inscrit un dépôt pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="28538-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="28538-106">Unregister-PSRepository : supprime un dépôt inscrit pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="28538-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="28538-107">Set-PSRepository : définir des valeurs pour un dépôt inscrit.</span><span class="sxs-lookup"><span data-stu-id="28538-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="28538-108">Get-PSRepository : obtenir tous les dépôts inscrits pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="28538-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="28538-109">Après avoir inscrit un dépôt, vous pouvez utiliser Find-Module et Install-Module pour l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="28538-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```

