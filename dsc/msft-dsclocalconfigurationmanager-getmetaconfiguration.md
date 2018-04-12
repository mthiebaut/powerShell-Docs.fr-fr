---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager

Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>Paramètres
----------

*MetaConfiguration* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.

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