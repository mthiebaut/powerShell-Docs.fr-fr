---
title: Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager

Restaure la configuration à une version précédente.

Syntaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Paramètres
----------

*configurationNumber* \[in\]  
Spécifie la configuration demandée. 

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


