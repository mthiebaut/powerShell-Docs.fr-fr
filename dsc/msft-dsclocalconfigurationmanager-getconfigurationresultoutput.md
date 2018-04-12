---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager

Obtient la sortie de l’agent de configuration associée à un travail spécifique.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Paramètres
----------

*jobId* \[in\] ID du travail pour lequel obtenir les données de sortie.

*resumeOutputBookmark* \[in\] Spécifie que la sortie doit être une continuation à partir d’un signet précédent.

*output* \[out\] Sortie pour le travail spécifié.

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