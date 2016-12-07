---
title: "exemple de modèle d’un problème ou limitation connu"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>Remarque : fournir un titre descriptif proposé et une brève description

## <a name="example-erroneous-executionpolicy-errors"></a>Exemples : erreurs ExecutionPolicy erronées ##
Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.

### <a name="resolution"></a>Solution

Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Set-ExecutionPolicy RemoteSigned
```
