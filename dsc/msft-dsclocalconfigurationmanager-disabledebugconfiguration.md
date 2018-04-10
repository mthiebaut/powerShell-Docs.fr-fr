---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9392a721a542c89be8794882a800b374f11ca5fd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode DisableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager

Désactive le débogage des ressources DSC.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 DisableDebugConfiguration();
```

<a name="parameters"></a>Paramètres
----------

Cette méthode n’a aucun paramètre.

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