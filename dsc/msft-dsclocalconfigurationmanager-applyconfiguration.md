---
title: "Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: 6f9c6a8851732574ac72bc4f3a3db1a73fbbecf2

---

# Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager

Utilise l’agent de configuration pour appliquer la configuration en attente. 

S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.


## Syntaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## Paramètres
----------

*force* \[in\]  
Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.

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


