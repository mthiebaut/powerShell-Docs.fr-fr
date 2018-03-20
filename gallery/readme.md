---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery, powershell, applet de commande, psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a>PowerShell Gallery

PowerShell Gallery est le référentiel central pour le contenu PowerShell. Les nouvelles commandes PowerShell ou les ressources DSC (configuration de l’état souhaité) sont disponibles dans la galerie.

## <a name="powershellget-overview"></a>Vue d’ensemble de PowerShellGet

Le module PowerShellGet contient des applets de commande permettant de détecter, d’installer, de mettre à jour et de publier les artefacts PowerShell tels que les modules, les ressources DSC, les fonctionnalités de rôle et les scripts à partir du référentiel [PowerShell Gallery](https://www.PowerShellGallery.com) et d’autres référentiels privés.

## <a name="getting-started-with-the-gallery"></a>Prise en main de la galerie

L’installation d’éléments à partir de la galerie nécessite la dernière version du module PowerShellGet, qui est disponible dans Windows 10, dans Windows Management Framework (WMF) 5.0 ou dans le programme d’installation basé sur MSI (pour PowerShell 3 et 4).

- [**Obtenir Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
- [**Obtenir WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) ou
- [**Obtenir le programme d’installation de MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Avec le module [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) le plus récent, vous pouvez effectuer les opérations suivantes :

-   Parcourir les éléments de la galerie avec [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) et [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Enregistrer des éléments dans votre système à partir de la galerie avec [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) et [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Installer des éléments à partir de la galerie avec [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) et [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Charger des éléments dans la galerie avec [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) et [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Ajouter votre propre référentiel personnalisé avec [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Pour plus d’informations sur l’utilisation des commandes PowerShellGet avec la galerie, consultez la page [Getting Started](psgallery/psgallery_gettingstarted.md). Vous pouvez également exécuter *Update-Help-Module PowerShellGet* pour installer l’aide locale sur ces commandes.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Le module **PowerShellGet** nécessite **PowerShell 3.0 ou ultérieur**.

Par conséquent, **PowerShellGet** nécessite l’un des systèmes d’exploitation suivants :

- Windows 10
- Windows 8.1 Professionnel
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** nécessite également .NET Framework 4.5 ou ultérieur. Vous pouvez installer .NET Framework 4.5 ou ultérieur à partir [d’ici](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Vous avez une question ? Vous avez des commentaires ?

Des informations supplémentaires relatives à PowerShell Gallery et PowerShellGet sont disponibles dans la page [Getting Started](psgallery/psgallery_gettingstarted.md). Envoyez vos commentaires et signalez les problèmes à l’aide de [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

