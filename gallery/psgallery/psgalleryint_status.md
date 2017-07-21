---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="3e490-103">État de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="3e490-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="3e490-104">27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script</span><span class="sxs-lookup"><span data-stu-id="3e490-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="3e490-105">__Résumé de l’impact__ : Les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com ont été rompus.</span><span class="sxs-lookup"><span data-stu-id="3e490-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="3e490-106">Le problème a été signalé dans toutes les régions.</span><span class="sxs-lookup"><span data-stu-id="3e490-106">This was being reported across all the regions.</span></span> <span data-ttu-id="3e490-107">Aucun impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuent à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="3e490-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="3e490-108">__Cause première__ : Les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.</span><span class="sxs-lookup"><span data-stu-id="3e490-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="3e490-109">__Résolution__ : Les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.</span><span class="sxs-lookup"><span data-stu-id="3e490-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="3e490-110">__Étapes suivantes__ : Nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.</span><span class="sxs-lookup"><span data-stu-id="3e490-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="3e490-111">15/12/2016 - Impossible d’envoyer des e-mails sur le site web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="3e490-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="3e490-112">__Résumé de l’impact__ : Entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="3e490-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="3e490-113">__Cause racine__ : Les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="3e490-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="3e490-114">__Résolution__ : Les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="3e490-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="3e490-115">__Étapes suivantes__ : Si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un e-mail à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer.</span><span class="sxs-lookup"><span data-stu-id="3e490-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="3e490-116">Veuillez nous excuser pour ce désagrément.</span><span class="sxs-lookup"><span data-stu-id="3e490-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="3e490-117">10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="3e490-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="3e490-118">__Résumé de l’impact__ : Entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.</span><span class="sxs-lookup"><span data-stu-id="3e490-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="3e490-119">__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.</span><span class="sxs-lookup"><span data-stu-id="3e490-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="3e490-120">__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.</span><span class="sxs-lookup"><span data-stu-id="3e490-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="3e490-121">__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez.</span><span class="sxs-lookup"><span data-stu-id="3e490-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="3e490-122">Nous vous remercions de votre patience.</span><span class="sxs-lookup"><span data-stu-id="3e490-122">Thank you for your patience.</span></span>


