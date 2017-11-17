---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuration d’un client collecteur DSC"
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="7a8ae-103">Configuration d’un client collecteur DSC</span><span class="sxs-lookup"><span data-stu-id="7a8ae-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="7a8ae-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7a8ae-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7a8ae-105">Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL ou l’emplacement du fichier où contacter le serveur collecteur pour obtenir des configurations et des ressources, et où envoyer les données du rapport.</span><span class="sxs-lookup"><span data-stu-id="7a8ae-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="7a8ae-106">Les rubriques suivantes expliquent comment configurer les clients collecteurs :</span><span class="sxs-lookup"><span data-stu-id="7a8ae-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="7a8ae-107">Configuration d’un client collecteur à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="7a8ae-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="7a8ae-108">Configuration d’un client collecteur à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="7a8ae-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="7a8ae-109">**Remarque** : Ces rubriques s’appliquent à PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="7a8ae-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="7a8ae-110">Pour configurer un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="7a8ae-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

