---
title: "Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 4f3d74949d98e3ab3f5136303e229c23ed903c5d

---

# Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager

Supprime les fichiers de configuration.

Syntaxe
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

Paramètres
----------

*Stage* \[in\]  
Spécifie le document de configuration à supprimer. Les valeurs suivantes sont valides :

|Valeur |Description |
|:--- |:---|
|**1** | Document de configuration **Current** (current.mof). |
|**2** | Document de configuration **Pending** (pending.mof).  |
|**4** | Document de configuration **Previous** (previous.mof). |

*Force* \[in\]  
**true** pour forcer la suppression de la configuration.

## Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## Remarques

Il s’agit d’une méthode statique.

## Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


## Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 






<!--HONumber=Jun16_HO4-->


