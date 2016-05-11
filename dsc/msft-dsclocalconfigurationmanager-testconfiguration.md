---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Envoyez le document de configuration au nœud géré et testez-le par rapport à la configuration actuelle.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_testconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager

Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.

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


