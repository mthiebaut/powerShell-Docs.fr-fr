---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "capacités de rôle"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 81fd386d58576a8930093b4f18ce36a4ff6cecd0
ms.openlocfilehash: a3dd4a217f5b1fd80e97adf802c65073ca015bbc

---

# Capacités de rôle

## Vue d’ensemble
Dans la section ci-dessus, vous avez appris que le champ « RoleDefinitions » définit quels groupes ont accès à quelles capacités de rôle.
Vous vous êtes peut-être demandé : « Que sont les capacités de rôle ? »
Cette section va répondre à cette question.  

## Présentation des capacités de rôle PowerShell
Les capacités de rôle PowerShell définissent « ce » qu’un utilisateur peut faire sur un point de terminaison JEA.
Elles dressent la liste des éléments comme les commandes visibles, les applications visibles, etc.
Les capacités de rôle sont définies par des fichiers portant une extension « .psrc ».

## Contenu des capacités de rôle
Nous allons commencer en examinant et en modifiant le fichier de capacité de rôle de démonstration que vous avez utilisé précédemment.
Imaginez que vous avez déployé votre configuration de session sur votre environnement, mais que vous avez reçu des commentaires vous invitant à modifier les capacités exposées aux utilisateurs.
Les opérateurs ont besoin de pouvoir redémarrer les ordinateurs et aussi d’être en mesure d’obtenir des informations sur les paramètres réseau.
L’équipe de sécurité vous a également dit que qu’il ne faut pas permettre aux utilisateurs d’exécuter « Restart-Service » sans aucune restriction.
Vous devez restreindre les services que les opérateurs peuvent redémarrer.

Pour apporter ces modifications, commencez par exécuter PowerShell ISE en tant qu’administrateur et ouvrir le fichier suivant :

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Maintenant recherchez et mettez à jour les lignes suivantes dans le fichier :

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Ce fichier contient quelques exemples intéressants :

1.  Vous avez restreint Restart-Service de sorte que les opérateurs puissent uniquement l’utiliser avec le paramètre -Name et qu’ils soient uniquement autorisés à spécifier « Spooler » en tant qu’argument pour ce paramètre.
Si vous le voulez, vous pouvez également restreindre les arguments en utilisant une expression régulière qui utilise « ValidatePattern » au lieu de « ValidateSet ».

2.  Vous avez exposé toutes les commandes avec le verbe « Get » à partir du module NetTCPIP.
Étant donné que les commandes « Get » ne modifient généralement pas l’état du système, cette action est relativement sûre.
Ceci dit, il est fortement conseillé d’examiner de près chaque commande que vous exposez par le biais de JEA.

3.  Vous avez exposé un exécutable (ipconfig) en utilisant VisibleExternalCommands.
Vous pouvez également exposer des scripts PowerShell complets avec ce champ.
Il est important de toujours fournir le chemin complet des commandes externes pour veiller à ce qu’aucun programme portant le même nom (et potentiellement malveillant) placé dans le chemin de l’utilisateur ne soit exécuté à la place.

Enregistrez le fichier et reconnectez-vous au point de terminaison de démonstration pour vérifier que les modifications ont fonctionné.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Étant donné que vous avez modifié uniquement le fichier de capacité de rôle, il est inutile réinscrire la configuration de session.
PowerShell recherche automatiquement votre capacité de rôle mise à jour quand un utilisateur se connecte.
Dans la mesure où les capacités de rôle sont chargées au démarrage de la session, les sessions existantes ne sont pas affectées par les mises à jour apportées aux fichiers de capacités de rôle.

Maintenant, vérifiez que vous pouvez redémarrer l’ordinateur en exécutant Restart-Computer avec le paramètre -WhatIf (sauf si vous souhaitez réellement redémarrer l’ordinateur).

```PowerShell
Restart-Computer -WhatIf
```

Vérifiez que vous pouvez exécuter « ipconfig ».

```PowerShell
ipconfig
```

Enfin, vérifiez que Restart-Service ne fonctionne que pour le service Spooler.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail
```

Quittez la session quand vous avez terminé.

```PowerShell
Exit-PSSession
```

## Création de capacités de rôle
Dans la section suivante, vous allez créer un point de terminaison JEA pour les utilisateurs du support technique AD.
À titre de préparation, nous allons créer un fichier de capacité de rôle vierge à remplir pendant cette section.
Les capacités de rôle doivent être créées dans un dossier « RoleCapabilities » à l’intérieur d’un module PowerShell valide afin de pouvoir être résolues lorsqu’une session démarre.

Les modules PowerShell sont essentiellement des packages de fonctionnalités PowerShell.
Ils peuvent contenir des fonctions, applets de commandes, ressources DSC, capacités de rôle PowerShell, etc.
Pour plus d’informations sur les modules, exécutez `Get-Help about_Modules` dans une console PowerShell.

Pour créer un module PowerShell avec un fichier de capacité de rôle vierge, exécutez les commandes suivantes :  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File

# Create a RoleCapabilities folder in the Contoso_AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

Félicitations ! Vous avez créé un fichier de capacité de rôle vierge.
Il servira dans la section suivante.

## Concepts clés
**Capacité de rôle (.psrc)** : fichier qui définit ce qu’un utilisateur peut faire sur un point de terminaison JEA.
Elle dresse la liste des éléments comme les commandes visibles, les applications de console visibles, etc.
Pour que PowerShell détecte les capacités de rôle, vous devez les placer dans un dossier « RoleCapabilities » dans un module PowerShell valide.

**Module PowerShell** : package de fonctionnalités PowerShell.
Il peut contenir des fonctions, applets de commandes, ressources DSC, capacités de rôle PowerShell, etc.
Pour être chargés automatiquement, les modules PowerShell doivent se trouver sous un chemin dans `$env:PSModulePath`.




<!--HONumber=Jul16_HO1-->


