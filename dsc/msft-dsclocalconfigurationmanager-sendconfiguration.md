---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
Paramètres
----------

*ConfigurationData* \[in\]  
Données d’environnement pour la configuration.

*force* \[in\]  
**true** pour forcer l’arrêt de la configuration.

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


 

 



