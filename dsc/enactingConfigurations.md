---
ms.date: 2017-10-16
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Application des configurations
ms.openlocfilehash: 4285dbe04c9745ec2a859e479848da2881c18de0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="enacting-configurations"></a>Application des configurations

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Il existe deux façons de promulguer des configurations DSC PowerShell : le mode par envoi et le mode par extraction.

## <a name="push-mode"></a>Mode par envoi

![Mode par envoi](images/pushModel.png "Fonctionnement du mode par envoi")

Avec le mode par envoi, l’utilisateur applique activement une configuration à un nœud cible en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).

Après la création et la compilation d’une configuration, vous pouvez la promulguer avec le mode par envoi en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) et en définissant le paramètre -Path de l’applet de commande sur le chemin de la configuration MOF.
Par exemple, si la configuration MOF se trouve à l’emplacement `C:\DSC\Configurations\localhost.mof`, vous pouvez l’appliquer à l’ordinateur local avec la commande suivante :`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Remarque__ : Par défaut, DSC exécute une configuration comme tâche en arrière-plan. Pour exécuter la configuration de manière interactive, appelez [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) avec le paramètre __-Wait__.

## <a name="pull-mode"></a>Mode par extraction

![Mode par extraction](images/pullModel.png "Fonctionnement du mode par extraction")

Avec le mode par extraction, les clients d’extraction sont configurés de façon à obtenir leurs configurations d’état souhaité à partir d’un service d’extraction distant.
De même, le serveur a été configuré pour héberger le service DSC et approvisionné avec les configurations et les ressources requises par les clients d’extraction.
Chacun des clients d’extraction est associé à un événement planifié qui effectue une vérification de conformité à intervalles réguliers sur la configuration du nœud.
Quand l’événement est déclenché pour la première fois, le gestionnaire de configuration local sur le client d’extraction envoie une requête au service d’extraction pour obtenir la configuration spécifiée dans le gestionnaire de configuration local.
Si cette configuration existe sur le service d’extraction et si les vérifications de validation initiales renvoient un résultat positif, la configuration est téléchargée sur le client d’extraction, où elle est ensuite exécutée par le gestionnaire de configuration local.

Le gestionnaire de configuration local vérifie que le client est conforme à la configuration à intervalles réguliers, dont la fréquence est spécifiée par la propriété **ConfigurationModeFrequencyMins** du gestionnaire de configuration local.
Le gestionnaire de configuration local vérifie la présence de configurations mises à jour sur le service d’extraction à intervalles réguliers, spécifiés par la propriété **RefreshModeFrequency** du gestionnaire de configuration local.
Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).

La solution recommandée pour l’hébergement d’un service d’extraction est le service de cloud DSC, [Azure Automation](https://azure.microsoft.com/en-us/services/automation/).
Cette solution hébergée fournit des fonctionnalités de gestion graphique, de rapports et de gestion centralisée.

Pour plus d’informations sur la configuration d’un service d’extraction sur Windows Server, consultez [Configuration d’un serveur collecteur sur Windows Server](pullServer.md).
N’oubliez cependant pas que cette implémentation a des fonctionnalités limitées et nécessite une intégration « faite maison ».

Les rubriques suivantes expliquent les clients et les services d’extraction :

- [Vue d’ensemble d’Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configuration d’un serveur collecteur SMB](pullServerSMB.md)
- [Configuration d’un client d’extraction](pullClientConfigID.md)
