---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="df0fd-103">Retrait d’éléments de la liste</span><span class="sxs-lookup"><span data-stu-id="df0fd-103">Unlisting items</span></span>

<span data-ttu-id="df0fd-104">**Pourquoi la suppression d’un élément de PowerShell Gallery n’est-elle pas proposée en option ?**</span><span class="sxs-lookup"><span data-stu-id="df0fd-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="df0fd-105">PowerShell Gallery ne gère pas la suppression définitive d’éléments par des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="df0fd-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="df0fd-106">Cela permet à d’autres utilisateurs de s’attribuer des dépendances sur vos éléments sans se soucier d’arrêts possibles.</span><span class="sxs-lookup"><span data-stu-id="df0fd-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="df0fd-107">Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, l’utilisateur ne peut plus utiliser le module Pester.</span><span class="sxs-lookup"><span data-stu-id="df0fd-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="df0fd-108">Toutefois, au lieu de supprimer un élément, vous pouvez le retirer de la liste.</span><span class="sxs-lookup"><span data-stu-id="df0fd-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="df0fd-109">**À quoi sert le retrait d’un élément dans PowerShell Gallery ?**</span><span class="sxs-lookup"><span data-stu-id="df0fd-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="df0fd-110">Le retrait de la liste d’un élément comme un module ou un script dans PowerShell Gallery permet de supprimer cet élément de l’onglet Éléments.</span><span class="sxs-lookup"><span data-stu-id="df0fd-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="df0fd-111">De plus, les éléments retirés de la liste ne sont pas détectables à l’aide de la barre de recherche.</span><span class="sxs-lookup"><span data-stu-id="df0fd-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="df0fd-112">La seule façon de télécharger un élément non listé consiste à spécifier le nom et la version exacts de l’élément.</span><span class="sxs-lookup"><span data-stu-id="df0fd-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="df0fd-113">De ce fait, le retrait d’un élément de la liste n’interrompt pas les autres modules ou scripts qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="df0fd-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="df0fd-114">Pour retirer votre élément de la liste, visitez la page des détails de l’élément, puis sélectionnez « Supprimer l’élément ».</span><span class="sxs-lookup"><span data-stu-id="df0fd-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="df0fd-115">Décochez la case « Répertorié », puis cliquez sur Enregistrer.</span><span class="sxs-lookup"><span data-stu-id="df0fd-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="df0fd-116">**Comment supprimer un élément ?**</span><span class="sxs-lookup"><span data-stu-id="df0fd-116">**How can I remove an item?**</span></span>

<span data-ttu-id="df0fd-117">Si vous êtes confronté à un scénario nécessitant la suppression d’un élément, contactez les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="df0fd-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="df0fd-118">Les scénarios de suppression valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="df0fd-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="df0fd-119">Problèmes de violation des droits d’auteur.</span><span class="sxs-lookup"><span data-stu-id="df0fd-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="df0fd-120">Élément contenant un contenu potentiellement dangereux.</span><span class="sxs-lookup"><span data-stu-id="df0fd-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="df0fd-121">Élément contenant des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="df0fd-121">Item contains sensitive data.</span></span>

<span data-ttu-id="df0fd-122">Pour soumettre une demande de suppression d’élément aux administrateurs PowerShell Gallery, visitez la page des détails de votre élément, puis sélectionnez Contacter le support technique.</span><span class="sxs-lookup"><span data-stu-id="df0fd-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


