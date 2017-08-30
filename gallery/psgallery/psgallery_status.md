---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: d192c706bdbe9aa693f791ef1c8108aeaaae385b
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="48f0d-103">État de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="48f0d-103">PowerShell Gallery Status</span></span>
=========================
## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="48f0d-104">01/06/2017 - Déploiement sur Azure Automation actuellement indisponible</span><span class="sxs-lookup"><span data-stu-id="48f0d-104">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="48f0d-105">__Résumé de l’Impact__ : le déploiement des éléments avec des dépendances à Azure Automation à partir de PowerShell Gallery est actuellement indisponible.</span><span class="sxs-lookup"><span data-stu-id="48f0d-105">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="48f0d-106">L’importation d’éléments à partir de PowerShell Gallery depuis Azure Automation est toujours disponible.</span><span class="sxs-lookup"><span data-stu-id="48f0d-106">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="48f0d-107">__Cause première__ : les éléments qui ont des dépendances à d’autres éléments et qui ont été précédemment déployés sur Azure Automation ne seront pas déployés sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="48f0d-107">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="48f0d-108">Les ingénieurs ont identifié un problème avec la façon dont les modèles ARM sont générés pour les éléments avec des dépendances pour la fonctionnalité Déployer sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="48f0d-108">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="48f0d-109">__Résolution__ : les ingénieurs travaillent à la résolution de ce problème.</span><span class="sxs-lookup"><span data-stu-id="48f0d-109">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="48f0d-110">La solution actuelle pour les utilisateurs consiste à importer l’élément de PowerShell Gallery à partir d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="48f0d-110">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="48f0d-111">__Étapes suivantes__ : les ingénieurs publieront prochainement le correctif.</span><span class="sxs-lookup"><span data-stu-id="48f0d-111">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="48f0d-112">En attendant, utilisez la solution de contournement recommandée.</span><span class="sxs-lookup"><span data-stu-id="48f0d-112">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="48f0d-113">11/04/2017 - Les utilisateurs ne parviennent pas à se connecter avec un compte Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="48f0d-113">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="48f0d-114">__Résumé de l’impact__ : certains utilisateurs ne parvenaient pas à se connecter à PowerShell Gallery avec un compte Azure AD.</span><span class="sxs-lookup"><span data-stu-id="48f0d-114">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="48f0d-115">__Cause racine__: lors d’une mise à jour visant à sécuriser l’interaction avec AAD, une modification de paramètre a été oubliée.</span><span class="sxs-lookup"><span data-stu-id="48f0d-115">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="48f0d-116">Les tests effectués pour valider la modification n’incluaient pas tous les types de comptes AAD ; par conséquent, le déploiement s’est poursuivi.</span><span class="sxs-lookup"><span data-stu-id="48f0d-116">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="48f0d-117">__Résolution__ : les ingénieurs ont identifié le paramètre manquant et ont résolu le problème.</span><span class="sxs-lookup"><span data-stu-id="48f0d-117">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="48f0d-118">__Étapes suivantes__ : nous allons modifier nos tests afin d’inclure un ensemble plus large de types de comptes AAD.</span><span class="sxs-lookup"><span data-stu-id="48f0d-118">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="48f0d-119">27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script</span><span class="sxs-lookup"><span data-stu-id="48f0d-119">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="48f0d-120">__Résumé de l’impact__ : Les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com ont été rompus.</span><span class="sxs-lookup"><span data-stu-id="48f0d-120">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="48f0d-121">Le problème a été signalé dans toutes les régions.</span><span class="sxs-lookup"><span data-stu-id="48f0d-121">This was being reported across all the regions.</span></span> <span data-ttu-id="48f0d-122">Aucun impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuent à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="48f0d-122">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="48f0d-123">__Cause première__ : Les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.</span><span class="sxs-lookup"><span data-stu-id="48f0d-123">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="48f0d-124">__Résolution__ : Les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.</span><span class="sxs-lookup"><span data-stu-id="48f0d-124">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="48f0d-125">__Étapes suivantes__ : Nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.</span><span class="sxs-lookup"><span data-stu-id="48f0d-125">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="48f0d-126">15/12/2016 - Impossible d’envoyer des e-mails sur le site web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="48f0d-126">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="48f0d-127">__Résumé de l’impact__ : Entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48f0d-127">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="48f0d-128">__Cause racine__ : Les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="48f0d-128">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="48f0d-129">__Résolution__ : Les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="48f0d-129">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="48f0d-130">__Étapes suivantes__ : Si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un e-mail à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer.</span><span class="sxs-lookup"><span data-stu-id="48f0d-130">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="48f0d-131">Veuillez nous excuser pour ce désagrément.</span><span class="sxs-lookup"><span data-stu-id="48f0d-131">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="48f0d-132">10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="48f0d-132">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="48f0d-133">__Résumé de l’impact__ : Entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.</span><span class="sxs-lookup"><span data-stu-id="48f0d-133">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="48f0d-134">__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.</span><span class="sxs-lookup"><span data-stu-id="48f0d-134">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="48f0d-135">__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.</span><span class="sxs-lookup"><span data-stu-id="48f0d-135">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="48f0d-136">__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez.</span><span class="sxs-lookup"><span data-stu-id="48f0d-136">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="48f0d-137">Nous vous remercions de votre patience.</span><span class="sxs-lookup"><span data-stu-id="48f0d-137">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="48f0d-138">13/07/2016 – Échec du téléchargement d’éléments</span><span class="sxs-lookup"><span data-stu-id="48f0d-138">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="48f0d-139">__Résumé de l’impact__ : Entre le 11/07/2016 et le 13/07/2016, un sous-ensemble de clients a rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48f0d-139">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="48f0d-140">Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :</span><span class="sxs-lookup"><span data-stu-id="48f0d-140">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="48f0d-141">__Cause racine préliminaire__ : Les ingénieurs ont identifié un problème avec Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 11/07/2016.</span><span class="sxs-lookup"><span data-stu-id="48f0d-141">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="48f0d-142">__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48f0d-142">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="48f0d-143">__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.</span><span class="sxs-lookup"><span data-stu-id="48f0d-143">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="48f0d-144">19/05/2016 – Échec du téléchargement d’éléments</span><span class="sxs-lookup"><span data-stu-id="48f0d-144">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="48f0d-145">__Résumé de l’impact__ : Entre le 17/05/2016 et le 19/05/2016, des clients ont rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48f0d-145">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="48f0d-146">Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :</span><span class="sxs-lookup"><span data-stu-id="48f0d-146">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="48f0d-147">__Cause racine préliminaire__ : Les ingénieurs ont identifié une panne au niveau du fournisseur sous-jacent d’Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 17/05/2016.</span><span class="sxs-lookup"><span data-stu-id="48f0d-147">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="48f0d-148">__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="48f0d-148">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="48f0d-149">__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.</span><span class="sxs-lookup"><span data-stu-id="48f0d-149">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

