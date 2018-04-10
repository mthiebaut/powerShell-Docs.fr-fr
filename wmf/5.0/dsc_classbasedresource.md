---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Ressources DSC basées sur une classe

## <a name="defining-dsc-resources-with-classes"></a>Définition de ressources DSC avec des classes

Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes.
Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

* Aucun fichier MOF pour le schéma n’est nécessaire.
* Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.
* Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).