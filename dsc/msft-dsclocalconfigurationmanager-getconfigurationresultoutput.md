---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager

Obtient la sortie de l’agent de configuration associée à un travail spécifique.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a id="parameters" class="xliff"></a>
Paramètres
----------

*jobId* \[in\]  
ID du travail pour lequel obtenir les données de sortie.

*resumeOutputBookmark* \[in\]  
Spécifie que la sortie doit être une continuation à partir d’un signet précédent.

*output* \[out\]  
Sortie pour le travail spécifié.

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

 

 



