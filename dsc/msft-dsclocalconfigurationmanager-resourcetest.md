---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Exécutez Test directement sur un fournisseur.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourcetest'
MSHAttr: 'PreferredLib:/library'
title: 'Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager'
---

# Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager

Appelle directement la méthode **Test** d’une ressource DSC.

Syntaxe
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

Paramètres
----------

*ResourceType* \[in\]  
Nom de la ressource à appeler.

*ModuleName* \[in\]  
Nom du module qui contient la ressource à appeler.

*resourceProperty* \[in\]  
Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’
applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.

*InDesiredState* \[out\]  
En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.

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


