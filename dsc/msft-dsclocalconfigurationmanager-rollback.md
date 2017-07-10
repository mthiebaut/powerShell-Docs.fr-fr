---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="rollback-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager

Restaure la configuration à une version précédente.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a id="parameters" class="xliff"></a>
Paramètres
----------

*configurationNumber* \[in\]  
Spécifie la configuration demandée. 

<a id="return-value" class="xliff"></a>
## Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

<a id="remarks" class="xliff"></a>
## Remarques

Il s’agit d’une méthode statique.

<a id="requirements" class="xliff"></a>
## Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



