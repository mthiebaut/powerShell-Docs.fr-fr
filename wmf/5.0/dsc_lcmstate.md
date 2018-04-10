---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="03c47-102">Informations détaillées sur l’état du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="03c47-102">Detailed information about LCM state</span></span>

<span data-ttu-id="03c47-103">Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="03c47-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="03c47-104">Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="03c47-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="03c47-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="03c47-105">**Idle**</span></span>
* <span data-ttu-id="03c47-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="03c47-106">**Busy**</span></span>
* <span data-ttu-id="03c47-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="03c47-107">**PendingReboot**</span></span>
* <span data-ttu-id="03c47-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="03c47-108">**PendingConfiguration**</span></span>

<span data-ttu-id="03c47-109">Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.</span><span class="sxs-lookup"><span data-stu-id="03c47-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>