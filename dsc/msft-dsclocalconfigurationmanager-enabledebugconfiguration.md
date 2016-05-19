---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Activez la configuration DSC de débogage.'
MS-HAID: 'cimwin32a.msft\_dsclocalconfigurationmanager\_enabledebugconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager

Active le débogage des ressources DSC.

Syntaxe
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

Paramètres
----------

*BreakAll* \[in\]  
Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.

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


