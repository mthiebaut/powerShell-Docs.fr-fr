---
title: "Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 95b141472d9428cee71b6970fc1f496704211c0b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Paramètres
----------

*ConfigurationData* \[in\]  
Données d’environnement pour la configuration.

*force* \[in\]  
**true** pour forcer l’arrêt de la configuration.

## <a name="return-value"></a>Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



