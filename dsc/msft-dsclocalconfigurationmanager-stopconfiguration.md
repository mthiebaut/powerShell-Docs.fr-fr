---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Arrêt de la configuration en cours.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_stopconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager

Arrête la modification de la configuration en cours.

Syntaxe
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

Paramètres
----------

*force* \[in\]  
**true** pour forcer l’arrêt de la configuration.

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


