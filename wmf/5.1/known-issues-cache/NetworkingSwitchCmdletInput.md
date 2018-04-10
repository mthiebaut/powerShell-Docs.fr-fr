---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
contributor: vaibch
title: Échec des applets de commande du Gestionnaire de commutateur réseau
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="f8103-103">Les applets de commande du Gestionnaire de commutateur réseau peuvent être utilisées pour gérer les commutateurs réseau via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="f8103-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="f8103-104">Quelques applets de commande de ce module peuvent accepter des valeurs provenant de pipelines.</span><span class="sxs-lookup"><span data-stu-id="f8103-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="f8103-105">Dans WMF 5.1 Preview, l’exécution des applets de commande qui peuvent accepter une valeur provenant d’un pipeline échoue quand les valeurs ne sont pas passées via des pipelines.</span><span class="sxs-lookup"><span data-stu-id="f8103-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="f8103-106">Si le paramètre « InputObject » n’est pas utilisé, l’applet de commande doit continuer à s’exécuter sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="f8103-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="f8103-107">Voici la liste des applets de commande affectées (ces applets de commande peuvent accepter une valeur pour le paramètre « InputObject » provenant d’un pipeline).</span><span class="sxs-lookup"><span data-stu-id="f8103-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="f8103-108">Si cette valeur n’est pas passée depuis un pipeline, l’exécution de l’applet de commande échoue.</span><span class="sxs-lookup"><span data-stu-id="f8103-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="f8103-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="f8103-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="f8103-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="f8103-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="f8103-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="f8103-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="f8103-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="f8103-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="f8103-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="f8103-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="f8103-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="f8103-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="f8103-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="f8103-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="f8103-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="f8103-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="f8103-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="f8103-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="f8103-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="f8103-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="f8103-119">Solution</span><span class="sxs-lookup"><span data-stu-id="f8103-119">Resolution</span></span>
<span data-ttu-id="f8103-120">Les applets de commande fonctionnent correctement quand la valeur du paramètre InputObject leur est passée via un pipeline.</span><span class="sxs-lookup"><span data-stu-id="f8103-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="f8103-121">Voici quelques exemples qui fonctionnent pour les applets de commande ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="f8103-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="f8103-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="f8103-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="f8103-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="f8103-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="f8103-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="f8103-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="f8103-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="f8103-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="f8103-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="f8103-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="f8103-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="f8103-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="f8103-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="f8103-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="f8103-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="f8103-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```