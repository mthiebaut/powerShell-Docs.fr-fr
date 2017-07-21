---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a><span data-ttu-id="c2c2f-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c2c2f-103">Unregister-PSRepository</span></span>

<span data-ttu-id="c2c2f-104">Annule l’enregistrement d’un référentiel.</span><span class="sxs-lookup"><span data-stu-id="c2c2f-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="c2c2f-105">Description</span><span class="sxs-lookup"><span data-stu-id="c2c2f-105">Description</span></span>

<span data-ttu-id="c2c2f-106">L’applet de commande Unregister-PSRepository annule l’enregistrement d’un référentiel pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c2c2f-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="c2c2f-107">L’annulation de l’enregistrement et un nouvel enregistrement du référentiel PSGallery sont autorisés pour des scénarios d’entreprise et déconnectés.</span><span class="sxs-lookup"><span data-stu-id="c2c2f-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="c2c2f-108">Les utilisateurs peuvent réinscrire le dépôt PSGallery en exécutant simplement `Register-PSRepository -Default`</span><span class="sxs-lookup"><span data-stu-id="c2c2f-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="c2c2f-109">Étant donné que PSGallery est le référentiel de publication par défaut dans les applets de commande Publish-Module et Publish-Script, une erreur est générée si PSGallery n’est pas disponible dans la liste des référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="c2c2f-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="c2c2f-110">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c2c2f-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c2c2f-111">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c2c2f-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="c2c2f-112">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c2c2f-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="c2c2f-113">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="c2c2f-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="c2c2f-114">L’annulation de l’enregistrement et un nouvel enregistrement du référentiel PSGallery sont autorisés pour des scénarios d’entreprise et déconnectés.</span><span class="sxs-lookup"><span data-stu-id="c2c2f-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

