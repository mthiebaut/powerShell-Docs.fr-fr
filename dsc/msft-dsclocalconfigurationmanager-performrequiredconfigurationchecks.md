---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Démarre la vérification de cohérence.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_performrequiredconfigurationchecks'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager

Commence une vérification de cohérence à l’aide du Planificateur de tâches.

Syntaxe
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

Paramètres
----------

*Flags* \[in\]  
Masque de bits qui spécifie le type de vérification de cohérence à exécuter. Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :

|Valeur |Description |
|:--- |:---|
|**1** | Vérification de cohérence normale. |
|**2** | Poursuite d’une vérification de cohérence après un redémarrage. Cette valeur ne doit pas être combinée avec d’autres valeurs. |
|**4** | La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud. Cette valeur doit toujours être combinée avec **1** avec une valeur de **5**. |
|**8** | Envoyez l’état au serveur de rapports. |

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


