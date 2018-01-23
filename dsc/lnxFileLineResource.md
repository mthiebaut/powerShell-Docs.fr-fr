---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxFileLine dans DSC pour Linux
ms.openlocfilehash: 281f08c1dbf42372762a2b1b9838427b910ea791
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a>Ressource nxFileLine dans DSC pour Linux

La ressource **nxFileLine** dans DSC PowerShell fournit un mécanisme permettant de gérer des lignes au sein d’un fichier de configuration sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description | 
|---|---|
| FilePath| Le chemin complet du fichier dans lequel gérer les lignes se trouve sur le nœud cible.| 
| ContainsLine| Une ligne à vérifier se trouve dans le fichier. Cette ligne est ajoutée au fichier si elle ne s’y trouve pas. **ContainsLine** est obligatoire, mais peut être défini sur une chaîne vide (`ContainsLine = ‘’``) s’il n’est pas nécessaire.| 
| DoesNotContainPattern| Modèle d’expression régulière pour les lignes qui ne doivent pas se trouver dans le fichier. Les lignes du fichier qui correspondent à cette expression régulière seront supprimées du fichier.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exemple

Cet exemple montre comment utiliser la ressource **nxFileLine** pour configurer le fichier `/etc/sudoers`, en s’assurant que l’utilisateur :monuser est configuré sur DoNotRequireTTY.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

