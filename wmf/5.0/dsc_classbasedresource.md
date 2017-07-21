---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="28a1c-102">Ressources DSC basées sur une classe</span><span class="sxs-lookup"><span data-stu-id="28a1c-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="28a1c-103">Définition de ressources DSC avec des classes</span><span class="sxs-lookup"><span data-stu-id="28a1c-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="28a1c-104">Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes.</span><span class="sxs-lookup"><span data-stu-id="28a1c-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="28a1c-105">Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="28a1c-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="28a1c-106">Aucun fichier MOF pour le schéma n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="28a1c-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="28a1c-107">Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="28a1c-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="28a1c-108">Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="28a1c-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="28a1c-109">Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="28a1c-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

