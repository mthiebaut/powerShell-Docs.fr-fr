---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager

Utilise l’agent de configuration pour appliquer la configuration en attente.

S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.


## <a name="syntax"></a>Syntaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Paramètres
----------

*force* \[in\] Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.

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