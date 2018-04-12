---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="4c739-103">État de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="4c739-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="4c739-104">10/10/2017 – PowerShell Gallery indisponible pendant 2 heures le 10/10/17</span><span class="sxs-lookup"><span data-stu-id="4c739-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="4c739-105">__Résumé des répercussions__ : la PowerShell Gallery a connu une période de latence très élevée, ce qui a entraîné des problèmes de connexion intermittents à partir de 17 h 00 environ (heure du Pacifique) le 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="4c739-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="4c739-106">Pendant la résolution du problème, le site a été mis hors connexion pendant 2 heures environ à partir de 22 h 00 (heure du Pacifique).</span><span class="sxs-lookup"><span data-stu-id="4c739-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="4c739-107">Le site a été restauré un peu avant minuit le 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="4c739-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="4c739-108">__Cause première__ : la cause première de la latence élevée est toujours recherchée.</span><span class="sxs-lookup"><span data-stu-id="4c739-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="4c739-109">__Résolution__ : les services Web ont dû être mis hors connexion et restaurés pour résoudre le problème principal.</span><span class="sxs-lookup"><span data-stu-id="4c739-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="4c739-110">__Étapes suivantes__ : la cause première du problème d’origine est en cours d’étude.</span><span class="sxs-lookup"><span data-stu-id="4c739-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="4c739-111">01/06/2017 - Déploiement sur Azure Automation actuellement indisponible</span><span class="sxs-lookup"><span data-stu-id="4c739-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="4c739-112">__Résumé de l’Impact__ : le déploiement des éléments avec des dépendances à Azure Automation à partir de PowerShell Gallery est actuellement indisponible.</span><span class="sxs-lookup"><span data-stu-id="4c739-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="4c739-113">L’importation d’éléments à partir de PowerShell Gallery depuis Azure Automation est toujours disponible.</span><span class="sxs-lookup"><span data-stu-id="4c739-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="4c739-114">__Cause première__ : les éléments qui ont des dépendances à d’autres éléments et qui ont été précédemment déployés sur Azure Automation ne seront pas déployés sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="4c739-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="4c739-115">Les ingénieurs ont identifié un problème avec la façon dont les modèles ARM sont générés pour les éléments avec des dépendances pour la fonctionnalité Déployer sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="4c739-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="4c739-116">__Résolution__ : les ingénieurs travaillent à la résolution de ce problème.</span><span class="sxs-lookup"><span data-stu-id="4c739-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="4c739-117">La solution actuelle pour les utilisateurs consiste à importer l’élément de PowerShell Gallery à partir d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="4c739-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="4c739-118">__Étapes suivantes__ : les ingénieurs publieront prochainement le correctif.</span><span class="sxs-lookup"><span data-stu-id="4c739-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="4c739-119">En attendant, utilisez la solution de contournement recommandée.</span><span class="sxs-lookup"><span data-stu-id="4c739-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="4c739-120">11/04/2017 - Les utilisateurs ne parviennent pas à se connecter avec un compte Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="4c739-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="4c739-121">__Résumé de l’impact__ : certains utilisateurs ne parvenaient pas à se connecter à PowerShell Gallery avec un compte Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4c739-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="4c739-122">__Cause racine__: lors d’une mise à jour visant à sécuriser l’interaction avec AAD, une modification de paramètre a été oubliée.</span><span class="sxs-lookup"><span data-stu-id="4c739-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="4c739-123">Les tests effectués pour valider la modification n’incluaient pas tous les types de comptes AAD ; par conséquent, le déploiement s’est poursuivi.</span><span class="sxs-lookup"><span data-stu-id="4c739-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="4c739-124">__Résolution__ : les ingénieurs ont identifié le paramètre manquant et ont résolu le problème.</span><span class="sxs-lookup"><span data-stu-id="4c739-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="4c739-125">__Étapes suivantes__ : nous allons modifier nos tests afin d’inclure un ensemble plus large de types de comptes AAD.</span><span class="sxs-lookup"><span data-stu-id="4c739-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="4c739-126">27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script</span><span class="sxs-lookup"><span data-stu-id="4c739-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="4c739-127">__Résumé de l’impact__ : Les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com ont été rompus.</span><span class="sxs-lookup"><span data-stu-id="4c739-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="4c739-128">Le problème a été signalé dans toutes les régions.</span><span class="sxs-lookup"><span data-stu-id="4c739-128">This was being reported across all the regions.</span></span> <span data-ttu-id="4c739-129">Aucun impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuent à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4c739-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="4c739-130">__Cause première__ : Les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.</span><span class="sxs-lookup"><span data-stu-id="4c739-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="4c739-131">__Résolution__ : Les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.</span><span class="sxs-lookup"><span data-stu-id="4c739-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="4c739-132">__Étapes suivantes__ : Nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.</span><span class="sxs-lookup"><span data-stu-id="4c739-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="4c739-133">15/12/2016 - Impossible d’envoyer des e-mails sur le site web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="4c739-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="4c739-134">__Résumé de l’impact__ : Entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c739-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="4c739-135">__Cause racine__ : Les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="4c739-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="4c739-136">__Résolution__ : Les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="4c739-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="4c739-137">__Étapes suivantes__ : Si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un e-mail à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer.</span><span class="sxs-lookup"><span data-stu-id="4c739-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="4c739-138">Veuillez nous excuser pour ce désagrément.</span><span class="sxs-lookup"><span data-stu-id="4c739-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="4c739-139">10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="4c739-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="4c739-140">__Résumé de l’impact__ : Entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.</span><span class="sxs-lookup"><span data-stu-id="4c739-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="4c739-141">__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.</span><span class="sxs-lookup"><span data-stu-id="4c739-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="4c739-142">__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.</span><span class="sxs-lookup"><span data-stu-id="4c739-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="4c739-143">__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez.</span><span class="sxs-lookup"><span data-stu-id="4c739-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="4c739-144">Nous vous remercions de votre patience.</span><span class="sxs-lookup"><span data-stu-id="4c739-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="4c739-145">13/07/2016 – Échec du téléchargement d’éléments</span><span class="sxs-lookup"><span data-stu-id="4c739-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="4c739-146">__Résumé de l’impact__ : Entre le 11/07/2016 et le 13/07/2016, un sous-ensemble de clients a rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c739-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="4c739-147">Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :</span><span class="sxs-lookup"><span data-stu-id="4c739-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

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

<span data-ttu-id="4c739-148">__Cause racine préliminaire__ : Les ingénieurs ont identifié un problème avec Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 11/07/2016.</span><span class="sxs-lookup"><span data-stu-id="4c739-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="4c739-149">__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c739-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="4c739-150">__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.</span><span class="sxs-lookup"><span data-stu-id="4c739-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="4c739-151">19/05/2016 – Échec du téléchargement d’éléments</span><span class="sxs-lookup"><span data-stu-id="4c739-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="4c739-152">__Résumé de l’impact__ : Entre le 17/05/2016 et le 19/05/2016, des clients ont rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c739-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="4c739-153">Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :</span><span class="sxs-lookup"><span data-stu-id="4c739-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

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

<span data-ttu-id="4c739-154">__Cause racine préliminaire__ : Les ingénieurs ont identifié une panne au niveau du fournisseur sous-jacent d’Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 17/05/2016.</span><span class="sxs-lookup"><span data-stu-id="4c739-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="4c739-155">__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4c739-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="4c739-156">__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.</span><span class="sxs-lookup"><span data-stu-id="4c739-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>