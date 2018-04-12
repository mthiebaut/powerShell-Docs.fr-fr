---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager

Arrête la modification de la configuration en cours.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Paramètres
----------

*force* \[in\] **true** pour forcer l’arrêt de la configuration.

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