## <a name="microsoft-open-source-code-of-conduct"></a>Code de conduite Microsoft Open Source

Ce projet a adopté le [Code de conduite Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/).
Pour plus d’informations, consultez le [Forum Aux Questions sur le Code de conduite](https://opensource.microsoft.com/codeofconduct/faq/) ou contactez [opencode@microsoft.com](mailto:opencode@microsoft.com) si vous avez d’autres questions ou des commentaires.

[![État de la build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>Documentation de PowerShell

Bienvenue dans le dépôt de documents de PowerShell, qui héberge la documentation officielle de Windows PowerShell. 

## <a name="repository-structure"></a>Structure du référentiel
Chaque dossier de ce référentiel est publié sur [MSDN](https://msdn.microsoft.com/en-us/powershell). Les dossiers correspondent aux ressources PowerShell suivantes :
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) correspond à la fonctionnalité DSC
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) correspond à la [Galerie PowerShell](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) correspond à la fonctionnalité JEA (Just Enough Administration)
* [/reference/](https://msdn.microsoft.com/powershell/reference/) correspond à la référence de module PowerShell dans les versions 2.0, 3.0, 4.0, 5.0, 5.1 et 6.0
  * À l’avenir, ce contenu sera récupéré par l’applet de commande `Get-Help`
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) correspond au contenu général des informations de référence sur PowerShell
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) contient les notes de publication pour Windows Management Framework, le package utilisé pour distribuer les nouvelles versions de PowerShell aux versions antérieures de Windows. 



## <a name="contributing"></a>Contribution

Nous fusionnons activement les contributions dans ce dépôt via une [demande Pull](https://help.github.com/articles/using-pull-requests/) dans la branche de *préproduction*. Notez qu’avant d’envoyer une demande Pull, vous devez [signer un contrat de licence de contribution](https://cla.microsoft.com/) pour garantir que la communauté est libre d’utiliser vos envois.
Pour plus d’informations sur la contribution, lisez notre [guide des contributions](CONTRIBUTING.md).
Il existe un [guide de style](./STYLE.md) préliminaire que vous pouvez consulter avant d’apporter des contributions.
Utilisez les modèles « Issue » et « Pull Request » afin que la documentation soit cohérente entre les versions. 
