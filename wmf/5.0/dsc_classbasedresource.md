---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Ressources DSC basées sur une classe

## <a name="defining-dsc-resources-with-classes"></a>Définition de ressources DSC avec des classes

Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes. Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

* Aucun fichier MOF pour le schéma n’est nécessaire.
* Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.
* Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

Pour plus d’informations, consultez [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).

