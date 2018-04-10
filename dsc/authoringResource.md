---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Création de ressources DSC Windows PowerShell personnalisées
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Création de ressources DSC Windows PowerShell personnalisées

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La configuration de l’état souhaité (DSC) de Windows PowerShell comprend des ressources intégrées que vous pouvez utiliser pour configurer votre environnement. Pour plus d’informations, consultez [Ressources DSC Windows PowerShell intégrées](builtInResource.md). Cette rubrique constitue une présentation du développement de ressources et fournit des liens vers des rubriques contenant des informations spécifiques et des exemples.

## <a name="dsc-resource-components"></a>Composants de la ressource DSC

Une ressource DSC est un module Windows PowerShell. Le module contient à la fois le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail spécifié par une configuration) de la ressource. Un schéma de ressources DSC peut être défini dans un fichier MOF et l’implémentation est effectuée par un module de script. À partir de la version 5 des classes PowerShell, le schéma et l’implémentation peuvent être définis dans une classe. Les rubriques suivantes expliquent plus en détail comment créer des ressources DSC.

* [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
* [Implementing a DSC resource in C#](authoringResourceMofCS.md)
* [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md)
* [Ressources composites : utilisation d’une configuration DSC comme ressource](authoringResourceComposite.md)
* [Utilisation du Concepteur de ressources](authoringResourceMofDesigner.md)