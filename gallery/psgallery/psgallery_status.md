---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: 48f554793d25c2d5ea10bc202489845f4225b2b9
ms.sourcegitcommit: ba8ed836799ef465e507fa1b8d341ba38459d863
translationtype: HT
---
<a name="powershell-gallery-status"></a>État de PowerShell Gallery
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script

__Résumé de l’impact__ : les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com étaient rompus. Cela était signalé dans toutes les régions. Cela n’avait pas impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continuaient à fonctionner.

__Cause première__ : les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.  

__Résolution__ : les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.

__Étapes suivantes__ : nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 - Impossible d’envoyer des courriers électroniques sur le site web PowerShell Gallery

__Résumé de l’impact__ : entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.  
__Cause racine__ : les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.  
__Résolution__ : les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.  
__Étapes__ : si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un courrier électronique à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer. Veuillez nous excuser pour ce désagrément.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com

__Résumé de l’impact__ : entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.  
__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.  
__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.  
__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez. Nous vous remercions de votre patience.



## <a name="7132016---download-items-failed"></a>13/07/2016 – Échec du téléchargement d’éléments

__Résumé de l’impact__ : Entre le 11/07/2016 et le 13/07/2016, un sous-ensemble de clients a rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery. Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :

```PowerShell
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
__Résumé de l’impact__ : Entre le 17/05/2016 et le 19/05/2016, un sous-ensemble de clients a rencontré des problèmes lors du téléchargement d’éléments à partir de PowerShell Gallery. Vraisemblablement le problème s’est manifesté dans le message d’erreur suivant retourné par Install-Module/Install-Script et Save-Module/Save-Script :

```PowerShell
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

