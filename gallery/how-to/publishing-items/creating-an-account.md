---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: Création d’un compte PowerShell Gallery
ms.openlocfilehash: 3ec9ad8f979fc0b88fbee72fc28ad1e3394eb01d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="d2dda-103">Création d’un compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d2dda-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="d2dda-104">Un compte PowerShell Gallery doit être créé avant de publier quoi que ce soit dessus.</span><span class="sxs-lookup"><span data-stu-id="d2dda-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="d2dda-105">Les comptes PowerShell Gallery doivent être liés à un compte de messagerie compatible Azure Active Directory ou un compte de messagerie Microsoft (avec un domaine outlook.com, hotmail.com, etc.)</span><span class="sxs-lookup"><span data-stu-id="d2dda-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="d2dda-106">Pour créer un compte PowerShell Gallery, accédez à https://PowerShellGallery.com et cliquez sur « S’inscrire » (voir l’image ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="d2dda-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Créer un nouveau compte](../../Images/CreatingAccount-Register.png)

<span data-ttu-id="d2dda-108">Sur la page suivante, sélectionnez « Compte professionnel ou scolaire » pour utiliser un compte Azure Active Directory et connectez-vous avec votre compte.</span><span class="sxs-lookup"><span data-stu-id="d2dda-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="d2dda-109">Pour utiliser un compte Microsoft, par exemple avec un domaine Hotmail.com ou Outlook.com, choisissez « Compte personnel », puis connectez-vous.</span><span class="sxs-lookup"><span data-stu-id="d2dda-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="d2dda-110">Une fois que vous êtes connecté, il vous est demandé de créer un nom d’utilisateur pour PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d2dda-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="d2dda-111">Passez en revue les liens des conditions d’utilisation et de la politique de confidentialité, saisissez un nom d’utilisateur, puis cliquez sur S’inscrire.</span><span class="sxs-lookup"><span data-stu-id="d2dda-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="d2dda-112">Remarque : Ce nom de compte ne peut pas être modifié une fois qu’il est créé.</span><span class="sxs-lookup"><span data-stu-id="d2dda-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="d2dda-113">Consultez [Gestion des propriétaires d’éléments](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) pour plus d’informations à ce sujet.</span><span class="sxs-lookup"><span data-stu-id="d2dda-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="d2dda-114">Pratiques recommandées pour les comptes PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d2dda-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="d2dda-115">Il est important que le compte de messagerie utilisé avec votre compte PowerShell Gallery soit surveillé activement.</span><span class="sxs-lookup"><span data-stu-id="d2dda-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="d2dda-116">Toutes les communications avec les propriétaires des éléments PowerShell Gallery passent par l’adresse de messagerie associée à votre compte PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d2dda-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="d2dda-117">Si nous ne pouvons pas contacter un propriétaire d’élément, il peut être demandé à l’équipe des opérations de supprimer un élément dans certaines circonstances.</span><span class="sxs-lookup"><span data-stu-id="d2dda-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="d2dda-118">Les organisations qui publient sur PowerShell Gallery créent souvent un compte unique à cet effet sur Outlook.com, ou un autre domaine de compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d2dda-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="d2dda-119">Dans de nombreux cas, ce compte n’est pas surveillé régulièrement.</span><span class="sxs-lookup"><span data-stu-id="d2dda-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="d2dda-120">Dans ce cas, il est recommandé d’utiliser le transfert d’Outlook pour envoyer un courrier électronique à une autre adresse, appartenant généralement à l’organisation, qui est surveillée par les propriétaires de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d2dda-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="d2dda-121">S’il existe plusieurs propriétaires associés un élément, toutes les communications provenant de PowerShell Gallery seront transmises à tous les propriétaires.</span><span class="sxs-lookup"><span data-stu-id="d2dda-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="d2dda-122">Consultez [Gestion des propriétaires d’éléments](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) pour plus d’informations sur l’ajout de propriétaires à un élément.</span><span class="sxs-lookup"><span data-stu-id="d2dda-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>