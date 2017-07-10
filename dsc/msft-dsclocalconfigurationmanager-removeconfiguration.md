---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager

Supprime les fichiers de configuration.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a id="parameters" class="xliff"></a>
Paramètres
----------

*Stage* \[in\]  
Spécifie le document de configuration à supprimer. Les valeurs suivantes sont valides :

|Value |Description |
|:--- |:---|
|**1** | Document de configuration **Current** (current.mof). |
|**2** | Document de configuration **Pending** (pending.mof).  |
|**4** | Document de configuration **Previous** (previous.mof). |

*Force* \[in\]  
**true** pour forcer la suppression de la configuration.

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


 

 



