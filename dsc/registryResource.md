---
title: Ressource Registry dans DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: d94f178fb75d15b12268ad783f78183ceba9f2b3
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-registry-resource"></a>Ressource Registry dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Clé| Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique. Ce chemin doit inclure la ruche.| 
| ValueName| Indique le nom de la valeur de Registre.| 
| Ensure| Indique si la clé et la valeur existent. Pour vous assurer qu’elles existent, définissez cette propriété sur « Present ». Pour vous assurer qu’elles n’existent pas, définissez la propriété sur « Absent ». La valeur par défaut est « Present ».| 
| Force| Si la clé de Registre spécifiée est présente, __Force__ la remplace par la nouvelle valeur.| 
| Hex| Indique si les données sont exprimées au format hexadécimal. Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal. Non valide pour les autres types. La valeur par défaut est __$false__.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Les données de la valeur de Registre.| 
| ValueType| Indique le type de la valeur. Les types pris en charge sont les suivants : 
<ul><li>Chaîne (REG_SZ)</li>


<li>Binaire (REG-BINARY)</li>


<li>Dword 32 bits (REG_DWORD)</li>


<li>Qword 64 bits (REG_QWORD)</li>


<li>Chaînes multiples (REG_MULTI_SZ)</li>


<li>Chaîne extensible (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Exemple
Cet exemple permet de s’assurer qu’une clé nommée « ExampleKey » est présente dans la ruche **HKEY\_LOCAL\_MACHINE**.
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

>**Remarque :** La modification d’un paramètre de Registre dans la ruche **HKEY\_CURRENT\_USER** implique que la configuration s’exécute avec les informations d’identification de l’utilisateur, plutôt qu’en tant que système.
>Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration. Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](runAsUser.md)



