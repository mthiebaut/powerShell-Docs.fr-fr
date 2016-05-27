---
title:  Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager

Arrête la modification de la configuration en cours.

Syntaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

Paramètres
----------

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


 

 





<!--HONumber=May16_HO3-->


