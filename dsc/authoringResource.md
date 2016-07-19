---
title: "Création de ressources DSC Windows PowerShell personnalisées"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 5b43723f7b14eb4bca06d0430b5981c3663c5801

---

# Création de ressources DSC Windows PowerShell personnalisées

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement. Pour plus d’informations, consultez [Ressources DSC Windows PowerShell intégrées](builtInResource.md). Cette rubrique constitue une présentation du développement de ressources et fournit des liens vers des rubriques contenant des informations spécifiques et des exemples.

## Composants de la ressource DSC

Une ressource DSC est un module Windows PowerShell. Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource. Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script. À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe. Les rubriques suivantes expliquent plus en détail comment créer des ressources DSC.

* [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md) 
* [Implémentation d’une ressource DSC en C#](authoringResourceMofCS.md) 
* [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md) 
* [Ressources composites : utilisation d’une configuration DSC comme ressource](authoringResourceComposite.md) 
* [Utilisation du Concepteur de ressources](authoringResourceMofDesigner.md) 




<!--HONumber=Jun16_HO4-->


