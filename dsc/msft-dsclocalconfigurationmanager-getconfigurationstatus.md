---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Obtenez l’historique des états de la configuration.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager

Obtenez l’historique des états de la configuration.

Syntaxe
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

Paramètres
----------

*All* \[in\]  
**true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont
l’application de la configuration et la vérification de cohérence.

*configurationStatus* \[out\]  
En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.

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


