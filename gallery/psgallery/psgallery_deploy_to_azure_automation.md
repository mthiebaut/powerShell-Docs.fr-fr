---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a>Déployer sur Azure Automation
===========================

Le bouton Déployer sur Azure Automation dans la page de détails de l’élément déploie l’élément de PowerShell Gallery sur Azure Automation.

![Bouton Déployer sur Azure Automation](Images/DeployToAzureAutomationButton.png)

Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.
Si l’élément contient des dépendances, toutes les dépendances sont également déployées sur Azure Automation.

AVERTISSEMENT : Si les mêmes élément et version existent déjà dans votre compte Automation, un nouveau déploiement à partir de PowerShell Gallery remplace l’élément du compte Automation.

Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation.  Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.

Le bouton Déployer sur Azure Automation peut être désactivé en ajoutant la balise AzureAutomationNotSupported aux métadonnées de l’élément.

Pour en savoir plus sur Azure Automation, voir le site web Azure Automation [site web Azure Automation](http://azure.microsoft.com/en-us/services/automation/).

