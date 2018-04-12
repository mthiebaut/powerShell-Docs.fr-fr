---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Paramètres
----------

*configurationData* \[in\] Spécifie les données de configuration à envoyer.

*configurations* \[out\] En retour, contient une instance incorporée des configurations.

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