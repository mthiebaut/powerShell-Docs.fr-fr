---
title: "Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4129c83dd0b72159cbf1d47c037b9d462ca45f0e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager

Appelle directement la méthode **Test** d’une ressource DSC.

<a name="syntax"></a>Syntaxe
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Paramètres
----------

*ResourceType* \[in\]  
Nom de la ressource à appeler.

*ModuleName* \[in\]  
Nom du module qui contient la ressource à appeler.

*resourceProperty* \[in\]  
Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.

*InDesiredState* \[out\]  
En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.

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


 

 



