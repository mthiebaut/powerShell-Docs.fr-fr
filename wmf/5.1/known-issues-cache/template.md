---
title: "exemple de modèle d’un problème ou limitation connu"
contributor: 
translationtype: Human Translation
ms.sourcegitcommit: a952a27ec1695ce9951c352446194cf72d18f50a
ms.openlocfilehash: cfe0a6562743f1df81acb81e33c120cb67f9042c

---

>Remarque : fournir un titre descriptif proposé et une brève description

## Exemples : erreurs ExecutionPolicy erronées ##
Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.

### Solution

Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Set-ExecutionPolicy RemoteSigned
```



<!--HONumber=Jul16_HO1-->


