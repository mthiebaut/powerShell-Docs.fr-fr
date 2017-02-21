---
title: Ressources DSC PackageManagementSource
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 22e61490e7b3f98335334a2703ec9639cbdaa87e
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
---
# <a name="dsc-packagemanagementsource-resource"></a>Ressources DSC PackageManagementSource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible. **Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.** Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.

## <a name="syntax"></a>Syntaxe

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Nom| Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.| 
| Ensure| Détermine si la source du package doit être inscrite ou désinscrite.| 
| InstallationPolicy| Détermine si vous faites confiance à la source du package. Valeurs disponibles : « Untrusted », « Trusted ».| 
| ProviderName| Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package.| 
| SourceUri| Spécifie l’URI de la source du package.| 
| SourceCredential| Informations d’identification permettant l’accès au package sur une source distante.| 

## <a name="example"></a>Exemple

Cet exemple inscrit la source du package http://nuget.org à l’aide de la ressource DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```
