---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource Log dans DSC
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a><span data-ttu-id="865ed-103">Ressource Log dans DSC</span><span class="sxs-lookup"><span data-stu-id="865ed-103">DSC Log Resource</span></span> 

> <span data-ttu-id="865ed-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="865ed-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="865ed-105">La ressource __Log__ dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="865ed-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="865ed-106">REMARQUE : Par défaut, seuls les journaux des opérations relatifs à DSC sont activés.</span><span class="sxs-lookup"><span data-stu-id="865ed-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="865ed-107">Pour que le journal d’analyse soit disponible ou visible, il doit être activé.</span><span class="sxs-lookup"><span data-stu-id="865ed-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="865ed-108">Consultez l’article suivant.</span><span class="sxs-lookup"><span data-stu-id="865ed-108">See the following article.</span></span>

[<span data-ttu-id="865ed-109">Où se trouvent les journaux des événements DSC ?</span><span class="sxs-lookup"><span data-stu-id="865ed-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="865ed-110">Propriétés</span><span class="sxs-lookup"><span data-stu-id="865ed-110">Properties</span></span>
|  <span data-ttu-id="865ed-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="865ed-111">Property</span></span>  |  <span data-ttu-id="865ed-112">Description</span><span class="sxs-lookup"><span data-stu-id="865ed-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="865ed-113">Message</span><span class="sxs-lookup"><span data-stu-id="865ed-113">Message</span></span>| <span data-ttu-id="865ed-114">Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="865ed-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="865ed-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="865ed-115">DependsOn</span></span> | <span data-ttu-id="865ed-116">Indique que la configuration d’une autre ressource doit être exécutée avant l’écriture de ce message dans le journal.</span><span class="sxs-lookup"><span data-stu-id="865ed-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="865ed-117">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="865ed-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="865ed-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="865ed-118">Example</span></span>

<span data-ttu-id="865ed-119">L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="865ed-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="865ed-120">**Remarque** : Si vous exécutez [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) avec cette ressource configurée, elle retourne toujours la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="865ed-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

