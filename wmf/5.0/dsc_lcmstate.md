---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="8d1eb-102">Informations détaillées sur l’état du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="8d1eb-102">Detailed information about LCM state</span></span>

<span data-ttu-id="8d1eb-103">Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="8d1eb-104">Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d1eb-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="8d1eb-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="8d1eb-105">**Idle**</span></span>
* <span data-ttu-id="8d1eb-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="8d1eb-106">**Busy**</span></span>
* <span data-ttu-id="8d1eb-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="8d1eb-107">**PendingReboot**</span></span>
* <span data-ttu-id="8d1eb-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="8d1eb-108">**PendingConfiguration**</span></span>

<span data-ttu-id="8d1eb-109">Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.</span><span class="sxs-lookup"><span data-stu-id="8d1eb-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

