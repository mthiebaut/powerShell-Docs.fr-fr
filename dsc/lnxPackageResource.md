---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxPackage dans DSC pour Linux
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-for-linux-nxpackage-resource" class="xliff"></a>
# Ressource nxPackage dans DSC pour Linux

La ressource **nxPackage** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des packages sur un nœud Linux.

<a id="syntax" class="xliff"></a>
## Syntaxe

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

<a id="properties" class="xliff"></a>
## Propriétés

|  Propriété |  Description | 
|---|---|
| Name| Nom du package pour lequel vous souhaitez garantir un état spécifique.| 
| Ensure| Détermine si l’existence du package doit être vérifiée. Définissez cette propriété sur « Present » pour vous assurer que le package existe. Définissez la propriété sur « Absent » pour vous assurer que le package n’existe pas. La valeur par défaut est « Present ».|  
| PackageManager| Les valeurs prises en charge sont « yum », « apt » et « zypper ». Spécifie le gestionnaire de package à utiliser lors de l’installation de packages. Si **FilePath** est spécifié, le chemin fourni est utilisé pour installer le package. Sinon, un gestionnaire de package est utilisé pour installer le package à partir d’un référentiel préconfiguré. Si ni **PackageManager** ni **FilePath** ne sont spécifiés, le gestionnaire de package par défaut pour le système est utilisé.| 
| FilePath| Chemin du fichier contenant le package.| 
| PackageGroup| Si sa valeur est **$true**, **Name** doit correspondre au nom d’un groupe de package à utiliser avec **PackageManager**. **PackageGroup** n’est pas valide si **FilePath** est spécifié.| 
| Arguments| Chaîne d’arguments transmise telle quelle au package.| 
| ReturnCode| Code de retour attendu. Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 

<a id="example" class="xliff"></a>
## Exemple

L’exemple suivant vérifie que le package nommé « httpd » a été installé sur un ordinateur Linux, à l’aide du gestionnaire de package « Yum ».

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

