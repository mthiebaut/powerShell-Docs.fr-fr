---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a>État de PowerShell Gallery
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017 – PowerShell Gallery indisponible pendant 2 heures le 10/10/17

__Résumé des répercussions__ : la PowerShell Gallery a connu une période de latence très élevée, ce qui a entraîné des problèmes de connexion intermittents à partir de 17 h 00 environ (heure du Pacifique) le 10/10/17. Pendant la résolution du problème, le site a été mis hors connexion pendant 2 heures environ à partir de 22 h 00 (heure du Pacifique). Le site a été restauré un peu avant minuit le 10/10/2017. 
 
__Cause première__ : la cause première de la latence élevée est toujours recherchée.

__Résolution__ : les services Web ont dû être mis hors connexion et restaurés pour résoudre le problème principal. 

__Étapes suivantes__ : la cause première du problème d’origine est en cours d’étude.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01/06/2017 - Déploiement sur Azure Automation actuellement indisponible

__Résumé de l’Impact__ : le déploiement des éléments avec des dépendances à Azure Automation à partir de PowerShell Gallery est actuellement indisponible.  L’importation d’éléments à partir de PowerShell Gallery depuis Azure Automation est toujours disponible.  
 
__Cause première__ : les éléments qui ont des dépendances à d’autres éléments et qui ont été précédemment déployés sur Azure Automation ne seront pas déployés sur Azure Automation. Les ingénieurs ont identifié un problème avec la façon dont les modèles ARM sont générés pour les éléments avec des dépendances pour la fonctionnalité Déployer sur Azure Automation.

__Résolution__ : les ingénieurs travaillent à la résolution de ce problème.  La solution actuelle pour les utilisateurs consiste à importer l’élément de PowerShell Gallery à partir d’Azure Automation. 

__Étapes suivantes__ : les ingénieurs publieront prochainement le correctif.  En attendant, utilisez la solution de contournement recommandée. 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017 - Les utilisateurs ne parviennent pas à se connecter avec un compte Azure Active Directory (AAD)

__Résumé de l’impact__ : certains utilisateurs ne parvenaient pas à se connecter à PowerShell Gallery avec un compte Azure AD. 
 
__Cause racine__: lors d’une mise à jour visant à sécuriser l’interaction avec AAD, une modification de paramètre a été oubliée. Les tests effectués pour valider la modification n’incluaient pas tous les types de comptes AAD ; par conséquent, le déploiement s’est poursuivi.

__Résolution__ : les ingénieurs ont identifié le paramètre manquant et ont résolu le problème. 

__Étapes suivantes__ : nous allons modifier nos tests afin d’inclure un ensemble plus large de types de comptes AAD.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script

__Résumé de l’impact__ : Les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com ont été rompus. Le problème a été signalé dans toutes les régions. Aucun impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuent à fonctionner.

__Cause première__ : Les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.  

__Résolution__ : Les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.

__Étapes suivantes__ : Nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 - Impossible d’envoyer des e-mails sur le site web PowerShell Gallery

__Résumé de l’impact__ : Entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.  
__Cause racine__ : Les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.  
__Résolution__ : Les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.  
__Étapes suivantes__ : Si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un e-mail à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer. Veuillez nous excuser pour ce désagrément.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com

__Résumé de l’impact__ : Entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.  
__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.  
__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.  
__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez. Nous vous remercions de votre patience.



## <a name="7132016---download-items-failed"></a>13/07/2016 – Échec du téléchargement d’éléments

__Résumé de l’impact__ : Entre le 11/07/2016 et le 13/07/2016, un sous-ensemble de clients a rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery. Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :

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

__Cause racine préliminaire__ : Les ingénieurs ont identifié un problème avec Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 11/07/2016.  
__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.  
__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.


## <a name="5192016---download-items-failed"></a>19/05/2016 – Échec du téléchargement d’éléments
__Résumé de l’impact__ : Entre le 17/05/2016 et le 19/05/2016, des clients ont rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery. Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :

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

__Cause racine préliminaire__ : Les ingénieurs ont identifié une panne au niveau du fournisseur sous-jacent d’Azure Content Delivery Network (CDN), qui a été déployé dans PowerShell Gallery le 17/05/2016.  
__Prévention__ : Les ingénieurs ont désactivé Azure CDN dans PowerShell Gallery.  
__Étapes suivantes__ : Rechercher la cause racine sous-jacente et développer une solution pour empêcher que le problème se reproduise.

