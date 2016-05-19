---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Envoyez le document de configuration au nœud géré et commencez à utiliser l’agent de configuration pour appliquer la configuration. Utilisez GetConfigurationResultOutput pour récupérer la sortie du résultat.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfigurationapplyasync'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.

Syntaxe
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

Paramètres
----------

*ConfigurationData* \[in\]  
Données d’environnement pour la configuration.

*force* \[in\]  
**true** pour forcer l’arrêt de la configuration.

*jobId* \[in\]  
ID du travail pour lequel envoyer la configuration.

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


