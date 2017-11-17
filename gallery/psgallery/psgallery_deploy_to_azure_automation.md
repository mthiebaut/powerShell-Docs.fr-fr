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
<a name="deploy-to-azure-automation"></a><span data-ttu-id="24c21-103">Déployer sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="24c21-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="24c21-104">Le bouton Déployer sur Azure Automation dans la page de détails de l’élément déploie l’élément de PowerShell Gallery sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="24c21-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Bouton Déployer sur Azure Automation](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="24c21-106">Quand vous cliquez dessus, vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure.</span><span class="sxs-lookup"><span data-stu-id="24c21-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="24c21-107">Si l’élément contient des dépendances, toutes les dépendances sont également déployées sur Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="24c21-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="24c21-108">AVERTISSEMENT : Si les mêmes élément et version existent déjà dans votre compte Automation, un nouveau déploiement à partir de PowerShell Gallery remplace l’élément du compte Automation.</span><span class="sxs-lookup"><span data-stu-id="24c21-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="24c21-109">Si vous déployez un module, il apparaît dans la section Modules d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="24c21-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="24c21-110">Si vous déployez un script, il apparaît dans la section Runbooks d’Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="24c21-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="24c21-111">Le bouton Déployer sur Azure Automation peut être désactivé en ajoutant la balise AzureAutomationNotSupported aux métadonnées de l’élément.</span><span class="sxs-lookup"><span data-stu-id="24c21-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="24c21-112">Pour en savoir plus sur Azure Automation, voir le site web Azure Automation [site web Azure Automation](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="24c21-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

