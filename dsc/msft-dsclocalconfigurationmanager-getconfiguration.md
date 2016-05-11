---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Envoyez le document de configuration au nœud géré et utilisez l’agent de configuration pour appliquer la configuration à l’aide de la méthode Get.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.

Syntaxe
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

Paramètres
----------

*configurationData* \[in\]  
Spécifie les données de configuration à envoyer.

*configurations* \[out\]  
En retour, contient une instance incorporée des configurations.

## Valeur renvoyée
------------

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## Remarques

Il s’agit d’une méthode statique.

## Spécifications
------------
>**MOF :** DscCore.mof

>**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration


## Voir aussi


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
 

 





<!--HONumber=Apr16_HO2-->


