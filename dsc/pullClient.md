---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Configuration d’un client collecteur DSC
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Configuration d’un client collecteur DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Le serveur collecteur (fonctionnalité Windows *Service DSC*) est un composant pris en charge de Windows Server. Toutefois, nous ne prévoyons pas de proposer de nouvelles fonctionnalités. Il est recommandé de commencer la transition des clients gérés vers [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (qui comprend d’autres fonctionnalités que le serveur collecteur de Windows Server) ou l’une des solutions de la Communauté répertoriées [ici](pullserver.md#community-solutions-for-pull-service).

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL ou l’emplacement du fichier où contacter le serveur collecteur pour obtenir des configurations et des ressources, et où envoyer les données du rapport.

Les rubriques suivantes expliquent comment configurer les clients collecteurs :

* [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)
* [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)

> **Remarque** : Ces rubriques s’appliquent à PowerShell 5.0. Pour configurer un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md).