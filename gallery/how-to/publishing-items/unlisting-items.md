---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: Retrait d’éléments de la liste
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="1e3cc-103">Retrait d’éléments de la liste</span><span class="sxs-lookup"><span data-stu-id="1e3cc-103">Unlisting items</span></span>

<span data-ttu-id="1e3cc-104">**Pourquoi la suppression d’un élément de PowerShell Gallery n’est-elle pas proposée en option ?**</span><span class="sxs-lookup"><span data-stu-id="1e3cc-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="1e3cc-105">PowerShell Gallery ne gère pas la suppression définitive d’éléments par des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="1e3cc-106">Cela permet à d’autres utilisateurs de s’attribuer des dépendances sur vos éléments sans se soucier d’arrêts possibles.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="1e3cc-107">Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, l’utilisateur ne peut plus utiliser le module Pester.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="1e3cc-108">Toutefois, au lieu de supprimer un élément, vous pouvez le retirer de la liste.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="1e3cc-109">**À quoi sert le retrait d’un élément dans PowerShell Gallery ?**</span><span class="sxs-lookup"><span data-stu-id="1e3cc-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="1e3cc-110">Le retrait de la liste d’un élément comme un module ou un script dans PowerShell Gallery permet de supprimer cet élément de l’onglet Éléments. De plus, les éléments retirés de la liste ne sont pas détectables à l’aide de la barre de recherche.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="1e3cc-111">La seule façon de télécharger un élément non listé consiste à spécifier le nom et la version exacts de l’élément.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="1e3cc-112">De ce fait, le retrait d’un élément de la liste n’interrompt pas les autres modules ou scripts qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="1e3cc-113">Pour retirer votre élément de la liste, visitez la page des détails de l’élément, puis sélectionnez « Supprimer l’élément ».</span><span class="sxs-lookup"><span data-stu-id="1e3cc-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="1e3cc-114">Décochez la case « Répertorié », puis cliquez sur Enregistrer.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="1e3cc-115">**Comment supprimer un élément ?**</span><span class="sxs-lookup"><span data-stu-id="1e3cc-115">**How can I remove an item?**</span></span>

<span data-ttu-id="1e3cc-116">Si vous êtes confronté à un scénario nécessitant la suppression d’un élément, contactez les administrateurs PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="1e3cc-117">Les scénarios de suppression valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1e3cc-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="1e3cc-118">Problèmes de violation des droits d’auteur.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="1e3cc-119">Élément contenant un contenu potentiellement dangereux.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="1e3cc-120">Élément contenant des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-120">Item contains sensitive data.</span></span>

<span data-ttu-id="1e3cc-121">Pour soumettre une demande de suppression d’élément aux administrateurs PowerShell Gallery, visitez la page des détails de votre élément, puis sélectionnez Contacter le support technique.</span><span class="sxs-lookup"><span data-stu-id="1e3cc-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>