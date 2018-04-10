---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource Registry dans DSC
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="88200-103">Ressource Registry dans DSC</span><span class="sxs-lookup"><span data-stu-id="88200-103">DSC Registry Resource</span></span>

> <span data-ttu-id="88200-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="88200-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="88200-105">La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="88200-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="88200-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88200-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="88200-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="88200-107">Properties</span></span>
|  <span data-ttu-id="88200-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="88200-108">Property</span></span>  |  <span data-ttu-id="88200-109">Description</span><span class="sxs-lookup"><span data-stu-id="88200-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="88200-110">Clé</span><span class="sxs-lookup"><span data-stu-id="88200-110">Key</span></span>| <span data-ttu-id="88200-111">Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="88200-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="88200-112">Ce chemin doit inclure la ruche.</span><span class="sxs-lookup"><span data-stu-id="88200-112">This path must include the hive.</span></span>|
| <span data-ttu-id="88200-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="88200-113">ValueName</span></span>| <span data-ttu-id="88200-114">Indique le nom de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="88200-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="88200-115">Pour ajouter ou supprimer une clé de Registre, spécifiez cette propriété comme une chaîne vide sans définir ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="88200-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="88200-116">Pour modifier ou supprimer la valeur par défaut d’une clé de Registre, spécifiez cette propriété comme une chaîne vide tout en définissant ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="88200-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="88200-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="88200-117">Ensure</span></span>| <span data-ttu-id="88200-118">Indique si la clé et la valeur existent.</span><span class="sxs-lookup"><span data-stu-id="88200-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="88200-119">Pour vous assurer qu’elles existent, définissez cette propriété sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="88200-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="88200-120">Pour vous assurer qu’elles n’existent pas, définissez la propriété sur « Absent ».</span><span class="sxs-lookup"><span data-stu-id="88200-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="88200-121">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="88200-121">The default value is "Present".</span></span>|
| <span data-ttu-id="88200-122">Force</span><span class="sxs-lookup"><span data-stu-id="88200-122">Force</span></span>| <span data-ttu-id="88200-123">Si la clé de Registre spécifiée est présente, __Force__ la remplace par la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="88200-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="88200-124">Si vous supprimez une clé de Registre avec des sous-clés, la valeur doit être __$true__</span><span class="sxs-lookup"><span data-stu-id="88200-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="88200-125">Hex</span><span class="sxs-lookup"><span data-stu-id="88200-125">Hex</span></span>| <span data-ttu-id="88200-126">Indique si les données sont exprimées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="88200-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="88200-127">Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="88200-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="88200-128">Non valide pour les autres types.</span><span class="sxs-lookup"><span data-stu-id="88200-128">Not valid for other types.</span></span> <span data-ttu-id="88200-129">La valeur par défaut est __$false__.</span><span class="sxs-lookup"><span data-stu-id="88200-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="88200-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="88200-130">DependsOn</span></span>| <span data-ttu-id="88200-131">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="88200-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="88200-132">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="88200-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="88200-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="88200-133">ValueData</span></span>| <span data-ttu-id="88200-134">Les données de la valeur de Registre.</span><span class="sxs-lookup"><span data-stu-id="88200-134">The data for the registry value.</span></span>|
| <span data-ttu-id="88200-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="88200-135">ValueType</span></span>| <span data-ttu-id="88200-136">Indique le type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="88200-136">Indicates the type of the value.</span></span> <span data-ttu-id="88200-137">Les types pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="88200-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="88200-138">Chaîne (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="88200-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="88200-139">Binaire (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="88200-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="88200-140">Dword 32 bits (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="88200-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="88200-141">Qword 64 bits (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="88200-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="88200-142">Chaînes multiples (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="88200-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="88200-143">Chaîne extensible (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="88200-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="88200-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="88200-144">Example</span></span>
<span data-ttu-id="88200-145">Cet exemple permet de s’assurer qu’une clé nommée « ExampleKey » est présente dans la ruche **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="88200-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

><span data-ttu-id="88200-146">**Remarque :** La modification d’un paramètre de Registre dans la ruche **HKEY\_CURRENT\_USER** implique que la configuration s’exécute avec les informations d’identification de l’utilisateur, plutôt qu’en tant que système.</span><span class="sxs-lookup"><span data-stu-id="88200-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="88200-147">Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="88200-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="88200-148">Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="88200-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>