---
title: "Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: a81b41f66883b3cf0931905d24c8ff92ef55b6c7

---

# Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager

Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.

Syntaxe
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

Paramètres
----------

*ConfigurationData* \[in\]  
Données d’environnement pour la configuration.

*force* \[in\]  
**true** pour forcer l’arrêt de la configuration.

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


