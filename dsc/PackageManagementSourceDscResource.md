---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressources DSC PackageManagementSource
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
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
| Name| Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.|
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