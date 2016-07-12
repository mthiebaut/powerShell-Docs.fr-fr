---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "conditions préalables"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# Conditions préalables

## État initial
Avant d’entamer cette section, vérifiez les points suivants :

1. JEA est disponible sur votre système. Consultez le fichier [LISEZMOI](./README.md) pour connaître les systèmes d’exploitation actuellement pris en charge et les téléchargements requis.
2. Vous possédez des droits d’administrateur sur l’ordinateur sur lequel vous testez JEA.
3. L’ordinateur est joint à un domaine.
Consultez la section [Création d’un contrôleur de domaine](#creating-a-domain-controller) pour configurer rapidement un nouveau domaine sur un serveur si vous n’en avez pas déjà un.

## Activer la communication à distance de PowerShell
La gestion avec JEA s’effectue via la communication à distance de PowerShell.
Exécutez la commande suivante dans une fenêtre PowerShell de l’administrateur pour vous assurer qu’elle est activée et correctement configurée :

```PowerShell
Enable-PSRemoting
```

Si vous ne connaissez pas bien la communication à distance de PowerShell, n’hésitez pas à exécuter `Get-Help about_Remote` pour en savoir plus sur cet important concept fondamental.

## Identifier vos utilisateurs ou groupes
Pour voir JEA en action, vous devez identifier les utilisateurs et groupes non-administrateurs que vous aller utiliser tout au long de ce guide.

Si vous utilisez un domaine existant, identifiez ou créez quelques utilisateurs ou groupes non privilégiés.
Vous donnerez à ces non-administrateurs un accès à JEA.
Chaque fois que vous voyez la variable `$NonAdministrator` en haut d’un script, attribuez-la à vos utilisateurs ou groupes non-administrateurs.

Si vous avez créé un domaine ex nihilo, cette tâche est beaucoup plus facile.
Utilisez la section [Configurer des utilisateurs et des groupes](creating-a-domain-controller.md#set-up-users-and-groups) en annexe pour créer des utilisateurs et groupes non-administrateurs.
Les valeurs par défaut de `$NonAdministrator` vont correspondre aux groupes créés dans cette section.

## Configurer le fichier de capacité de rôle de maintenance
Exécutez les commandes suivantes dans PowerShell pour créer le fichier de capacité de rôle démonstration que nous allons utiliser pour la section suivante.
Plus loin dans ce guide, vous allez découvrir à quoi sert ce fichier.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions =
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams
```

## Créer et inscrire le fichier de configuration de session de démonstration
Exécutez les commandes suivantes pour créer et inscrire le fichier de configuration de session de démonstration que nous allons utiliser pour la section suivante.
Plus loin dans ce guide, vous allez découvrir à quoi sert ce fichier.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```

## Activer l’enregistrement des modules PowerShell (facultatif)
Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système.
Vous n’êtes pas obligé de l’activer pour que JEA fonctionne, mais elle s’avérera utile dans la section [Création de rapports sur JEA](reporting-on-jea.md).

1. Ouvrez l'éditeur de stratégie de groupe locale
2. Accédez à « Configuration de l’ordinateur\Modèles d’administration\Composants Windows\Windows PowerShell ».
3. Double cliquez sur « Activer l’enregistrement des modules ».
4. Cliquez sur « Activé ».
5. Dans la section Options, cliquez sur « Afficher » en regard des noms de module.
6. Tapez « \* » dans la fenêtre contextuelle. Ainsi, PowerShell enregistre les commandes de tous les modules.
7. Cliquez sur OK et appliquez la stratégie.

Remarque : Vous pouvez également activer la transcription PowerShell à l’échelle du système via la stratégie de groupe.

**Bravo ! Vous avez à présent configuré votre ordinateur avec le point de terminaison de démonstration et vous êtes prêt à découvrir JEA.**




<!--HONumber=Jul16_HO1-->


