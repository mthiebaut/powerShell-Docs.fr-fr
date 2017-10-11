---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: d13c23cd6f9cce433cd3fe1ad5f2d00e3ef0527c
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2017
---
# <a name="get-started-with-the-powershell-gallery"></a>Prendre en main PowerShell Gallery

## <a name="what-is-the-powershell-gallery"></a>Présentation de PowerShell Gallery

PowerShell Gallery est le référentiel central pour le contenu PowerShell.
Vous pouvez y trouver des modules PowerShell utiles contenant les commandes PowerShell et les ressources DSC (Configuration de l’état souhaité). Vous pouvez également trouver des scripts PowerShell, certains d’entre eux peuvent contenir des workflows PowerShell qui présentent une série de tâches et donnent le séquencement de ces tâches.
Certains de ces éléments sont créés par Microsoft et d’autres sont créés par la communauté PowerShell.

## <a name="requirements"></a>Spécifications

Le téléchargement d’éléments de PowerShell Gallery sur votre système nécessite le module [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Le module PowerShellGet se trouve dans les éléments suivants. Il est inutile de se connecter pour télécharger des éléments de PowerShell Gallery.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Programme d’installation de MSI (pour PowerShell 3 et 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet nécessite également le [fournisseur NuGet](http://go.microsoft.com/fwlink/?LinkId=722208) pour utiliser PowerShell Gallery. Vous devrez installer le fournisseur NuGet automatiquement lors de la première utilisation de PowerShellGet si le fournisseur NuGet n’est pas présent à l’un des emplacements suivants :

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Vous pouvez également exécuter `Install-PackageProvider -Name NuGet -Force` pour automatiser le téléchargement et l’installation du fournisseur NuGet.

  
Si vous avez une version antérieure à 2.8.5.201 de NuGet, vous devez appeler les applets de commande PowerShell suivantes pour installer la dernière version de NuGet et basculer vers celle-ci.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Supprimez l’ancienne version de NuGet à partir de l’emplacement d’installation ci-dessus.

Pour plus d’informations, voir <http://oneget.org/>.

  
Remarque : En raison de modifications apportées aux formats des packages, nous vous recommandons d’effectuer la mise à jour vers la dernière version de PowerShellGet et PackageManagement pour installer les éléments qui ont été récemment mis à jour. PowerShellGet est inclus dans Windows 10, au sujet duquel vous pouvez en savoir plus [ici](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet fait également partie de WMF (Windows Management Framework) 5.0, que vous pouvez télécharger [ici](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>Détection d’éléments dans PowerShell Gallery

Vous pouvez rechercher des éléments dans PowerShell Gallery à l’aide du contrôle **Rechercher** sur ce site web, ou en parcourant les pages des modules et des scripts. Vous pouvez également rechercher des éléments dans PowerShell Gallery en exécutant les applets de commande [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) et [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322), selon le type d’élément, avec `-Repository PSGallery`.

Le filtrage des résultats de PowerShell Gallery est possible en utilisant les paramètres suivants de [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) et [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)

- Nom
- AllVersions
- MinimumVersion
- RequiredVersion
- Légende
- Includes
- DscResource
- RoleCapability
- Commande
- Filtre

Si vous êtes uniquement intéressé par la détection de ressources DSC spécifiques dans PowerShell Gallery, vous pouvez exécuter l’applet de commande [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196).
[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) retourne des données sur les ressources DSC contenues dans PowerShell Gallery. Étant donné que les ressources DSC sont toujours transmises dans le cadre d’un module, vous devez toujours exécuter [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) pour installer ces ressources DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>En savoir plus sur les éléments de PowerShell Gallery

Une fois que vous avez identifié un élément qui vous intéresse, vous pouvez en savoir plus à son sujet. Pour cela, examinez la page spécifique de cet élément dans PowerShell Gallery. Dans cette page, vous serez en mesure de voir toutes les métadonnées chargées avec l’élément. Ces métadonnées associées à un élément sont fournies par l’auteur de l’élément et ne sont pas vérifiées par Microsoft. Le propriétaire de l’élément est fortement associé au compte PowerShell Gallery utilisé pour publier l’élément et est plus fiable que le champ Auteur.

Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.

Si vous exécutez [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) ou [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322), vous pouvez afficher ces données dans l’objet PSGetModuleInfo retourné.
Par exemple, l’exécution de `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` retourne des données dans le module PSReadLine dans PowerShell Gallery.

## <a name="downloading-items-from-the-powershell-gallery"></a>Téléchargement d’éléments de PowerShell Gallery

Nous conseillons le processus suivant lors du téléchargement des éléments de PowerShell Gallery :

### <a name="inspect"></a>Inspecter

Pour télécharger un élément de PowerShell Gallery pour inspection, exécutez l’applet de commande [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) ou [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334), selon le type d’élément. Cela vous permet d’enregistrer l’élément localement sans l’installer et d’inspecter son contenu. N’oubliez pas de supprimer l’élément enregistré manuellement.

Certains de ces éléments sont créés par Microsoft et d’autres sont créés par la communauté PowerShell. Microsoft recommande de passer en revue le contenu et le code des éléments de cette galerie avant l’installation.

Si vous détectez un élément publié qui vous semble suspect, cliquez sur **Signaler un abus** dans la page de l’élément.

### <a name="install"></a>Installer

Pour installer un élément de PowerShell Gallery à utiliser, exécutez l’applet de commande [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ou [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327), selon le type d’élément.

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installe le module dans `$env:ProgramFiles\WindowsPowerShell\Modules` par défaut. Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope
CurrentUser`, le module est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installe le script dans `$env:ProgramFiles\WindowsPowerShell\Scripts` par défaut. Cette opération nécessite un compte d’administrateur. Si vous ajoutez le paramètre `-Scope
CurrentUser`, le script est installé dans `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Par défaut, [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) et [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installent la version la plus récente d’un élément. Pour installer une version antérieure de l’élément, ajoutez le paramètre `-RequiredVersion`.

### <a name="deploy"></a>Déployez

Pour déployer un élément de PowerShell Gallery sur Azure Automation, cliquez sur **Déployer sur Azure Automation** dans la page de détails de l’élément. Vous êtes redirigé vers le portail de gestion Azure où vous vous connectez à l’aide des informations d’identification de compte Azure. Notez que le déploiement d’éléments avec des dépendances va déployer toutes les dépendances sur Azure Automation. Le bouton « Déployer sur Azure Automation » peut être désactivé en ajoutant la balise **AzureAutomationNotSupported** aux métadonnées de l’élément.

Pour en savoir plus sur Azure Automation, voir le [site web Azure Automation](http://azure.microsoft.com/en-us/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Mise à jour d’éléments de PowerShell Gallery

Pour mettre à jour les éléments installés à partir de PowerShell Gallery, exécutez l’applet de commande [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) ou [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787). Quand elle est exécutée sans paramètre supplémentaire, [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) tente de mettre à jour chaque module installé en exécutant [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663).
Pour mettre à jour les modules de façon sélective, ajoutez le paramètre `-Name`.

De même, quand elle est exécutée sans paramètre supplémentaire, [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) tente également de mettre à jour chaque script installé en exécutant [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327).
Pour mettre à jour les scripts de façon sélective, ajoutez le paramètre `-Name`.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Répertorier les éléments que vous avez installés à partir de PowerShell Gallery

Pour connaître les modules que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863). Cette commande répertorie tous les modules qui ont été installés directement à partir de PowerShell Gallery sur votre système.

De même, pour connaître les scripts que vous avez installés à partir de PowerShell Gallery, exécutez l’applet de commande [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790). Cette commande répertorie tous les scripts qui ont été installés directement à partir de PowerShell Gallery sur votre système.

