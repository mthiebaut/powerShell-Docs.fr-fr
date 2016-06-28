---
title: Ressource nxSshAuthorizedKeys dans DSC pour Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: edc906b4e9c925320c4ed00c5ab295189066ccb9

---

# Ressource nxSshAuthorizedKeys dans DSC pour Linux

La ressource **nxAuthorizedKeys** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des clés SSH autorisées pour un utilisateur spécifique.

## Syntaxe

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| KeyComment| Commentaire unique utilisé pour identifier une clé de manière unique.| 
| Ensure| Spécifie si la clé est définie. Définissez cette propriété sur « Absent » pour vous assurer que la clé n’existe pas dans le fichier de clés autorisées de l’utilisateur. Définissez cette propriété sur « Present » pour vous assurer que la clé est définie dans le fichier de clés autorisées de l’utilisateur.| 
| Username| Nom de l’utilisateur pour lequel gérer les clés SSH autorisées. Si aucun nom n’est défini, l’utilisateur par défaut est l’utilisateur « racine ».| 
| Key| Contenu de la clé. Cette propriété doit être spécifiée si **Ensure** est défini sur « Present ».| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant définit une clé SSH autorisée publique pour l’utilisateur « monuser ».

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```




<!--HONumber=Jun16_HO4-->


