---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Paramètres
----------

*ConfigurationData* \[in\] Les données d’environnement pour la configuration.

*force* \[in\] **true** pour forcer l’arrêt de la configuration.

*jobId* \[in\] ID du travail pour lequel envoyer la configuration.

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