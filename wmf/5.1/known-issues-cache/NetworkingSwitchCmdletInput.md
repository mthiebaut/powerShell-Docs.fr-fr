---
title: "Échec des applets de commande du Gestionnaire de commutateur réseau"
contributor: vaibch
ms.openlocfilehash: 8495d79aec54d93f94e745e2efccb5116ad5d944
ms.sourcegitcommit: a3966253a165d193a42b43b9430a4dc76988f82f
ms.translationtype: HT
ms.contentlocale: fr-FR
---
<span data-ttu-id="71fc5-102">Les applets de commande du Gestionnaire de commutateur réseau peuvent être utilisées pour gérer les commutateurs réseau via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="71fc5-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="71fc5-103">Quelques applets de commande de ce module peuvent accepter des valeurs provenant de pipelines.</span><span class="sxs-lookup"><span data-stu-id="71fc5-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="71fc5-104">Dans WMF 5.1 Preview, l’exécution des applets de commande qui peuvent accepter une valeur provenant d’un pipeline échoue quand les valeurs ne sont pas passées via des pipelines.</span><span class="sxs-lookup"><span data-stu-id="71fc5-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="71fc5-105">Si le paramètre « InputObject » n’est pas utilisé, l’applet de commande doit continuer à s’exécuter sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="71fc5-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="71fc5-106">Voici la liste des applets de commande affectées (ces applets de commande peuvent accepter une valeur pour le paramètre « InputObject » provenant d’un pipeline).</span><span class="sxs-lookup"><span data-stu-id="71fc5-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="71fc5-107">Si cette valeur n’est pas passée depuis un pipeline, l’exécution de l’applet de commande échoue.</span><span class="sxs-lookup"><span data-stu-id="71fc5-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="71fc5-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="71fc5-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="71fc5-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="71fc5-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="71fc5-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="71fc5-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="71fc5-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="71fc5-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="71fc5-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="71fc5-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="71fc5-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="71fc5-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="71fc5-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="71fc5-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="71fc5-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="71fc5-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="71fc5-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="71fc5-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="71fc5-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="71fc5-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="71fc5-118">Solution</span><span class="sxs-lookup"><span data-stu-id="71fc5-118">Resolution</span></span>
<span data-ttu-id="71fc5-119">Les applets de commande fonctionnent correctement quand la valeur du paramètre InputObject leur est passée via un pipeline.</span><span class="sxs-lookup"><span data-stu-id="71fc5-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="71fc5-120">Voici quelques exemples qui fonctionnent pour les applets de commande ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="71fc5-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="71fc5-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="71fc5-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="71fc5-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="71fc5-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="71fc5-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="71fc5-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="71fc5-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="71fc5-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="71fc5-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="71fc5-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="71fc5-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="71fc5-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="71fc5-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="71fc5-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="71fc5-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="71fc5-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
