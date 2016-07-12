---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "déploiement et maintenance de plusieurs ordinateurs"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# Déploiement et maintenance de plusieurs ordinateurs
À ce stade, vous avez plusieurs fois déployé JEA sur des systèmes locaux.
Étant donné que votre environnement de production comprend probablement plusieurs ordinateurs, il est important de parcourir les étapes critiques du processus de déploiement qui doivent être répétées sur chaque ordinateur.

## Étapes générales :
1.  Copiez vos modules (avec des capacités de rôle) sur chaque nœud.
2.  Copiez vos fichiers de configuration de session sur chaque nœud.
3.  Exécutez `Register-PSSessionConfiguration` avec votre configuration de session.
4.  Conservez une copie de votre configuration de session et de vos kits de ressources à un emplacement sécurisé.
Pendant que vous apportez des modifications, il est toujours intéressant de disposer d’une « seule source de vérité ».

## Exemple de script
Voici un exemple de script de déploiement.
Pour l’utiliser dans votre environnement, vous devrez utiliser les noms/chemins de partages de fichiers et modules réels.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## Modification des capacités
Quand vous vous occupez d’un grand nombre d’ordinateurs, il est important que les modifications soient introduites de façon cohérente.
Une fois que JEA a une ressource DSC, votre environnement est synchronisé.
En attendant, nous vous recommandons vivement de conserver une copie principale de vos configurations de session et de redéployer chaque fois que vous apportez une modification.

## Suppression de capacités
Pour supprimer votre configuration JEA de vos systèmes, utilisez la commande suivante sur chaque ordinateur :
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Jul16_HO1-->


