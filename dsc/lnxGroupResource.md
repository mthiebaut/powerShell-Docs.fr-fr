---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxGroup dans DSC pour Linux
ms.openlocfilehash: fcd1dfd3110b1358ed7ef9ca8d57154186b271f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="84ccc-103">Ressource nxGroup dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="84ccc-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="84ccc-104">La ressource **nxGroup** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="84ccc-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="84ccc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84ccc-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="84ccc-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="84ccc-106">Properties</span></span>

|  <span data-ttu-id="84ccc-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="84ccc-107">Property</span></span> |  <span data-ttu-id="84ccc-108">Description</span><span class="sxs-lookup"><span data-stu-id="84ccc-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="84ccc-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="84ccc-109">GroupName</span></span>| <span data-ttu-id="84ccc-110">Spécifie le nom du groupe pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="84ccc-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="84ccc-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="84ccc-111">Ensure</span></span>| <span data-ttu-id="84ccc-112">Détermine si l’existence du groupe doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="84ccc-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="84ccc-113">Définissez cette propriété sur « Present » pour vous assurer que le groupe existe.</span><span class="sxs-lookup"><span data-stu-id="84ccc-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="84ccc-114">Définissez la propriété sur « Absent » pour vous assurer que le groupe n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="84ccc-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="84ccc-115">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="84ccc-115">The default value is "Present".</span></span>| 
| <span data-ttu-id="84ccc-116">Members</span><span class="sxs-lookup"><span data-stu-id="84ccc-116">Members</span></span>| <span data-ttu-id="84ccc-117">Spécifie les membres qui constituent le groupe.</span><span class="sxs-lookup"><span data-stu-id="84ccc-117">Specifies the members that form the group.</span></span>| 
| <span data-ttu-id="84ccc-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="84ccc-118">MembersToInclude</span></span>| <span data-ttu-id="84ccc-119">Spécifie les utilisateurs qui doivent faire partie du groupe.</span><span class="sxs-lookup"><span data-stu-id="84ccc-119">Specifies the users who you want to ensure are members of the group.</span></span>| 
| <span data-ttu-id="84ccc-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="84ccc-120">MembersToExclude</span></span>| <span data-ttu-id="84ccc-121">Spécifie les utilisateurs qui ne doivent pas faire partie du groupe.</span><span class="sxs-lookup"><span data-stu-id="84ccc-121">Specifies the users who you want to ensure are not members of the group.</span></span>| 
| <span data-ttu-id="84ccc-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="84ccc-122">PreferredGroupID</span></span>| <span data-ttu-id="84ccc-123">Définit l’ID de groupe à la valeur fournie, si possible.</span><span class="sxs-lookup"><span data-stu-id="84ccc-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="84ccc-124">Si l’ID de groupe est déjà utilisé, l’ID de groupe disponible suivant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="84ccc-124">If the group id is currently in use, the next available group id is used.</span></span>| 
| <span data-ttu-id="84ccc-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="84ccc-125">DependsOn</span></span> | <span data-ttu-id="84ccc-126">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="84ccc-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="84ccc-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="84ccc-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="84ccc-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="84ccc-128">Example</span></span>

<span data-ttu-id="84ccc-129">L’exemple suivant vérifie que l’utilisateur « monuser » existe et qu’il est membre du groupe « DBusers ».</span><span class="sxs-lookup"><span data-stu-id="84ccc-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

