---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Restauration à la configuration précédente.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager

Restaure la configuration à une version précédente.

Syntaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Paramètres
----------

*configurationNumber* \[in\]  
Spécifie la configuration demandée. 

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


