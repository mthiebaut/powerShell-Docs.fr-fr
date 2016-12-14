---
title: "Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0777467d37e2f5588f9c0ef368148e3bea963a5b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Paramètres
----------

*configurationData* \[in\]  
Données d’environnement pour la configuration.

*InDesiredState* \[out\]  
En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.

*ResourcesInDesiredState* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.

*ResourcesNotInDesiredState* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.

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


 

 



