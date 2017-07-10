---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager

Utilise l’agent de configuration pour appliquer la configuration en attente. 

S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.


<a id="syntax" class="xliff"></a>
## Syntaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
## Paramètres
----------

*force* \[in\]  
Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.

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

 

 



