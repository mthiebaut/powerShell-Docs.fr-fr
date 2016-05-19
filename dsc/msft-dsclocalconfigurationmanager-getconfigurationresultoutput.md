---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Récupérez la sortie de l’agent de configuration associée à un travail spécifique.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationresultoutput'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager

Obtient la sortie de l’agent de configuration associée à un travail spécifique.

Syntaxe
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

Paramètres
----------

*jobId* \[in\]  
ID du travail pour lequel obtenir les données de sortie.

*resumeOutputBookmark* \[in\]  
Spécifie que la sortie doit être une continuation à partir d’un signet précédent.

*output* \[out\]  
Sortie pour le travail spécifié.

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


