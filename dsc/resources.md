---
title: Ressources DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd

---

# Ressources DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.

Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.  Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.  

Les rubriques suivantes décrivent les ressources DSC :

- [Ressources DSC intégrées](builtInResource.md)
- [Créer des ressources DSC personnalisées](authoringResource.md)
- [Ressources DSC intégrées pour Linux](lnxBuiltInResources.md)




<!--HONumber=Jun16_HO4-->


