---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_deploy_to_azure_automation
ms.technology: powershell
ms.openlocfilehash: 20b0dd53b5d10f36089a884a99209a575332a91a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
<a name="deploy-to-azure-automation"></a>Déployer sur Azure Automation
===========================

Le bouton Déployer sur Azure Automation dans la page de détails de l’élément déploie l’élément de PowerShell Gallery sur Azure Automation.

![Bouton Déployer sur Azure Automation](Images/DeployToAzureAutomationButton.png)

Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.
Si l’élément contient des dépendances, toutes les dépendances sont également déployées sur Azure Automation.

AVERTISSEMENT : Si les mêmes élément et version existent déjà dans votre compte Automation, un nouveau déploiement à partir de PowerShell Gallery remplace l’élément du compte Automation.

Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation.  Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.

Le bouton Déployer sur Azure Automation peut être désactivé en ajoutant la balise AzureAutomationNotSupported aux métadonnées de l’élément.

Pour en savoir plus sur Azure Automation, voir le site web Azure Automation [site web Azure Automation](http://azure.microsoft.com/en-us/services/automation/).

