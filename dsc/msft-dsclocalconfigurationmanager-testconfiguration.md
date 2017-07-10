---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.

<a id="syntax" class="xliff"></a>
Syntaxe
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a id="parameters" class="xliff"></a>
Paramètres
----------

*configurationData* \[in\]  
Données d’environnement pour la configuration.

*InDesiredState* \[out\]  
En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.

*ResourcesInDesiredState* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.

*ResourcesNotInDesiredState* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.

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


 

 



