---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Appel direct de méthodes de ressources DSC
ms.openlocfilehash: dbf0a4ada4c6cc2e7d65698b87a5a29a2ea84781
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="3fb21-103">Appel direct de méthodes de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="3fb21-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="3fb21-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3fb21-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3fb21-105">Vous pouvez utiliser l’applet de commande [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) pour appeler directement les fonctions ou méthodes d’une ressource DSC (les fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** d’une ressource basée sur MOF, ou les méthodes **Get**, **Set** et **Test** d’une ressource basée sur la classe).</span><span class="sxs-lookup"><span data-stu-id="3fb21-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="3fb21-106">Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources.</span><span class="sxs-lookup"><span data-stu-id="3fb21-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="3fb21-107">Cette applet de commande est généralement utilisée avec une propriété de métaconfiguration `refreshMode = 'Disabled'`, mais vous pouvez l’utiliser quelle que soit la valeur de **refreshMode**.</span><span class="sxs-lookup"><span data-stu-id="3fb21-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="3fb21-108">Lors de l’appel de l’applet de commande **Invoke-DscResource**, vous spécifiez la méthode ou fonction à appeler à l’aide du paramètre **Method**.</span><span class="sxs-lookup"><span data-stu-id="3fb21-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="3fb21-109">Vous spécifiez les propriétés de la ressource en passant une table de hachage comme valeur du paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="3fb21-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="3fb21-110">Voici quelques exemples d’appels directs de méthodes de ressources :</span><span class="sxs-lookup"><span data-stu-id="3fb21-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="3fb21-111">S’assurer de la présence d’un fichier</span><span class="sxs-lookup"><span data-stu-id="3fb21-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="3fb21-112">Tester la présence d’un fichier</span><span class="sxs-lookup"><span data-stu-id="3fb21-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="3fb21-113">Obtenir le contenu du fichier</span><span class="sxs-lookup"><span data-stu-id="3fb21-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="3fb21-114">**Remarque :** l’appel direct de méthodes de ressources composites n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3fb21-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="3fb21-115">Appelez plutôt les ressources sous-jacentes qui forment la ressource composite.</span><span class="sxs-lookup"><span data-stu-id="3fb21-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fb21-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fb21-116">See Also</span></span>
- [<span data-ttu-id="3fb21-117">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="3fb21-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="3fb21-118">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fb21-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="3fb21-119">Débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="3fb21-119">Debugging DSC resources</span></span>](debugResource.md)