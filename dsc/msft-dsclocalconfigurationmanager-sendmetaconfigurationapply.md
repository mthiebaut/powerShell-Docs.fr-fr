---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager

Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 SendMetaConfigurationApply(
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


 

 



