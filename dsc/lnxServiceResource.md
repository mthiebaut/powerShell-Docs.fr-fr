---
title: Ressource nxService dans DSC pour Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 8443860628617eb56ce370be62f9618f19f78077
ms.sourcegitcommit: 26f4e52f3dd008b51b7eae7b634f0216eec6200e
translationtype: HT
---
# <a name="dsc-for-linux-nxservice-resource"></a>Ressource nxService dans DSC pour Linux

La ressource **nxService** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des services sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés
|  Propriété |  Description | 
|---|---|
| Nom| Nom du service/démon à configurer.| 
| Controller| Type de contrôleur de service à utiliser lors de la configuration du service.| 
| Enabled| Indique si le service s’exécute au démarrage du système.| 
| State| Indique si le service est en cours d’exécution. Définissez cette propriété sur « Stopped » pour vous assurer que le service n’est pas en cours d’exécution. Définissez cette propriété sur « Running » pour vous assurer que le service est en cours d’exécution.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Informations supplémentaires

La ressource **nxService** ne crée pas de fichier de définition ni de script pour le service si celui-ci n’existe pas. Vous pouvez utiliser la ressource **nxFile** dans DSC PowerShell pour gérer l’existence ou le contenu du fichier de définition ou script du service.

## <a name="example"></a>Exemple

L’exemple suivant configure le service « httpd » (pour Apache HTTP Server) qui est inscrit auprès du contrôleur de service **SystemD**.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

