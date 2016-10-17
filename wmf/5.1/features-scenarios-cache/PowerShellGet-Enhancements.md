---
title: "exemple de modèle d’écriture d’une fonctionnalité ou d’un scénario"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>Remarque : fournir un titre descriptif proposé et une brève description

## Améliorations apportées à PowerShellGet ##
Les applets de commande dans le module PowerShellGet ont été considérablement mises à jour dans WMF 5.1. Les nouveaux scénarios suivants sont à présent pris en charge :

- **Prise en charge de proxy :** L’utilisation des applets de commande PowerShellGet avec un proxy interne est maintenant prise en charge, avec l’ajout des paramètres Proxy et ProxyCredential à l’ensemble des applets de commande Find-, Install-, Save- et Publish- dans le module PowerShellGet (par exemple, Find-Module, Install-Module, Save-Module, Publish-Module). 
- **Application de la signature de catalogue :** Toutes les applets de commande PowerShellGet recherchent et appliquent maintenant la mise à jour des modules signés. Les modules signés à l’aide des nouvelles applets de commande de catalogue seront vérifiés par les applets de commande PowerShellGet pour garantir que le module n’a pas été modifié pendant le transit et que les mises à jour du module peuvent provenir uniquement de l’éditeur d’origine. Cela affecte les applets de commande Install-Module et Update-Module. 
- **Partage et acquisition de capacités spécifiques au rôle :** Les capacités spécifiques au rôle sont les définitions de point de terminaison utilisées pour configurer l’administration suffisante à contraindre et sont partagées via PowerShell Gallery dans les modules PowerShell. Les applets de commande incluent Find-RoleCapability et New-PSRoleCapabilityFile. 
- **Rechercher une commande :** Find-Command permet aux utilisateurs de localiser un module dans PowerShell Gallery qui contient une commande qu’ils recherchent. 
- **Référentiels authentifiés :** Le flux de gestion de packages Visual Studio nécessite une authentification, maintenant prise en charge via les applets de commande PowerShellGet.

Les commentaires des utilisateurs ont identifié d’autres secteurs pouvant être améliorés et traités dans 5.1, parmi lesquels :

- **Modifications apportées à Install-Script :** L’emplacement utilisé par Install-script n’est pas automatiquement ajouté au chemin utilisateur dans 5.1. Cette modification a été effectuée dans la version autonome de PowerShellGet et se trouve maintenant dans WMF 5.1.
- **Ajout de champs de métadonnées aux scripts existants :** Update-ScriptFileInfo peut servir dans des scripts existants pour ajouter les champs de métadonnées par défaut nécessaires pour publier dans PowerShell Gallery. Les utilisateurs devaient auparavant effectuer une fusion manuelle dans un script existant.
- **Publication d’un module de version inférieure dans PowerShell Gallery :** Il est maintenant possible de publier un module avec un numéro de version inférieur à la version la plus élevée précédente dans PowerShell Gallery avec Publish-Module. Si un éditeur a publié la version 2.0.0 de son module avec les dernières modifications issues des versions 1.x, il n’est pas facile pour lui de publier un correctif pour la version 1.5.0. Il peut à présent publier un correctif pour la version 1.5.1 afin d’améliorer la prise en charge de la gestion des modules dans PowerShell Gallery. 
- **Recherche de remplacement de commande lors de l’installation des scripts et des modules :** Install-Module et Install-Script vont maintenant vérifier si elles contiennent des commandes qui sont déjà présentes sur le système et générer par défaut une erreur le cas échéant. 
- **Démarrage de Nuget dans les applets de commande Publish- :** Il n’existait auparavant aucun moyen d’installer automatiquement le fournisseur Nuget lors de l’utilisation de Publish-Module ou de Publish-Script, ce qui compliquait certaines tâches d’automatisation. Les utilisateurs peuvent désormais ajouter -Force aux commandes Publish- pour ignorer l’invite. 

>Remarque : Les détails supplémentaires sur les nouveaux concepts, l’implémentation, les exemples, etc. doivent être liés à la documentation technique canonique.

**En savoir plus sur l’utilisation de PowerShellGet**
- [About-CatalogSigning]()
- []()
- [Filtrer les résultats de Get-Module par CompatiblePSEditions]()
- [Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell]()






<!--HONumber=Aug16_HO3-->


