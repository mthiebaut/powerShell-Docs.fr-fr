---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Spécification de dépendances entre nœuds"
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="c0671-103">Spécification de dépendances entre nœuds</span><span class="sxs-lookup"><span data-stu-id="c0671-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="c0671-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c0671-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c0671-105">DSC fournit des ressources spéciales, **WaitForAll**, **WaitForAny** et **WaitForSome**, qui peuvent être utilisées dans les configurations pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="c0671-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="c0671-106">Le comportement de ces ressources est le suivant :</span><span class="sxs-lookup"><span data-stu-id="c0671-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="c0671-107">**WaitForAll** : réussit si la ressource spécifiée est dans l’état souhaité sur tous les nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="c0671-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="c0671-108">**WaitForAny** : réussit si la ressource spécifiée est dans l’état souhaité sur au moins l’un des nœuds cibles définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="c0671-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="c0671-109">**WaitForSome** : spécifie une propriété **NodeCount** en plus d’une propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="c0671-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="c0671-110">La ressource réussit si elle est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="c0671-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="c0671-111">Utilisation de ressources WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="c0671-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="c0671-112">Pour utiliser les ressources **WaitForXXXX**, vous créez un bloc de ressources du type de ressource qui spécifie la ressource DSC et les nœuds à attendre.</span><span class="sxs-lookup"><span data-stu-id="c0671-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="c0671-113">Vous utilisez ensuite la propriété **DependsOn** dans tous les autres blocs de ressources dans votre configuration pour attendre que les conditions spécifiées dans le nœud **WaitForXXXX** réussissent.</span><span class="sxs-lookup"><span data-stu-id="c0671-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="c0671-114">Par exemple, dans la configuration suivante, le nœud cible attend que la ressource **xADDomain** se termine sur le nœud **MyDC** avec un nombre maximal de 30 tentatives, à des intervalles de 15 secondes, avant que le nœud cible ne puisse joindre le domaine.</span><span class="sxs-lookup"><span data-stu-id="c0671-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

><span data-ttu-id="c0671-115">**Remarque** : Par défaut les ressources WaitForXXX effectuent une tentative, puis échouent.</span><span class="sxs-lookup"><span data-stu-id="c0671-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="c0671-116">Même si ce n’est pas obligatoire, vous indiquez généralement un intervalle avant nouvelle tentative et un nombre.</span><span class="sxs-lookup"><span data-stu-id="c0671-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0671-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0671-117">See Also</span></span>
* [<span data-ttu-id="c0671-118">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="c0671-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="c0671-119">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="c0671-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="c0671-120">Configuration du Gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="c0671-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

