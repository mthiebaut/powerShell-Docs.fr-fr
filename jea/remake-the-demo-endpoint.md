---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "refaire le point de terminaison de démonstration"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d20ea8418cb7389d756de94ea752cf604b8d07af
ms.openlocfilehash: acd2cfbd038250a26236c875d0e8b03a32cd84f9

---

# Refaire le point de terminaison de démonstration
Dans cette section, vous allez apprendre à générer un réplica exact du point de terminaison de démonstration que vous avez utilisé dans la section ci-dessus.
Des concepts essentiels à la compréhension de JEA vont ainsi être présentés, notamment les configurations de session PowerShell et les capacités de rôle.

## Configurations de session PowerShell
Quand vous avez utilisé JEA dans la section ci-dessus, vous avez démarré en exécutant la commande suivante :

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Même si les noms des paramètres sont explicites, le paramètre *ConfigurationName* peut sembler déroutant dans un premier temps.
Ce paramètre spécifiait la configuration de session PowerShell à laquelle vous vous connectiez.

Une *configuration de session PowerShell* est une locution technique qui désigne un point de terminaison PowerShell.
Métaphoriquement, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.
Selon la façon dont vous paramétrez une configuration de session, elle peut fournir des fonctionnalités différentes aux utilisateurs qui se connectent.
Pour JEA, nous utilisons des configurations de session afin de restreindre PowerShell à un ensemble limité de fonctionnalités et pour une exécution en tant que compte virtuel privilégié.

Vous avez déjà plusieurs configurations de session PowerShell inscrites sur votre ordinateur, chacune étant configurée de façon légèrement différente.
La plupart d’entre elles sont fournies avec Windows, mais la configuration de session « JEA_Demo » a été configurée pendant la section [Conditions préalables](prerequisites.md).
Vous pouvez voir toutes les configurations de session inscrites en exécutant la commande suivante depuis une invite PowerShell d’administrateur :

```PowerShell
Get-PSSessionConfiguration
```

## Fichiers de configuration de session PowerShell
Vous pouvez créer des configurations de session en inscrivant de nouveaux *fichiers de configuration de session PowerShell*.
Les fichiers de configuration de session portent une extension de fichier « .pssc ».
Vous pouvez générer des fichiers de configuration de session avec l’applet de commande New-PSSessionConfigurationFile.

Ensuite, vous allez créer et inscrire une configuration de session pour JEA.

## Générer et modifier votre configuration de session PowerShell
Exécutez la commande suivante pour générer un fichier « squelette » de configuration de session PowerShell.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **Conseil :** Seuls les paramètres de configuration les plus courants sont inclus dans le fichier squelette par défaut.
> Utilisez le paramètre `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.

Ouvrez le fichier dans PowerShell ISE ou votre éditeur de texte favori.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Mettez à jour les champs suivants dans le fichier à l’aide des valeurs ci-dessous (pensez à les remplacer dans votre propre groupe de sécurité non-administrateur) :

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Voici la signification de chacune de ces entrées :

1.  Le champ *SessionType* définit des paramètres prédéfinis par défaut à utiliser avec ce point de terminaison.
*RestrictedRemoteServer* définit les paramètres minimum nécessaires à la gestion à distance.
Par défaut, un point de terminaison *RestrictedRemoteServer* expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host et Out-Default.
Il définit *ExecutionPolicy* sur *RemoteSigned* et *LanguageMode* sur *NoLanguage*.
L’effet net de ces paramètres est un point de départ sécurisé et minimal pour la configuration de votre point de terminaison.

2.  Le champ *RoleDefinitions* affecte des capacités de rôle à des groupes spécifiques.
Il définit qui peut faire quoi en tant que compte privilégié.
Avec ce champ, vous pouvez spécifier les capacités disponibles pour tout utilisateur qui tente d’établir une connexion en fonction de son appartenance à un groupe.
Là est l’essence de la fonctionnalité RBAC de JEA.
Dans cet exemple, vous exposez le champ RoleCapability « Maintenance » prédéfini aux membres du groupe « Contoso\JEA_NonAdmin_Operator ».

3.  Le champ *RunAsVirtualAccount* indique que PowerShell doit « s’exécuter en tant que » compte virtuel sur ce point de terminaison.
Par défaut, le compte virtuel est membre du groupe Administrateurs prédéfini.
Sur un contrôleur de domaine, il est également membre du groupe Administrateurs du domaine par défaut.
Plus loin dans ce guide, vous allez apprendre à personnaliser les privilèges du compte virtuel.

4.  Le champ *TranscriptDirectory* définit l’emplacement auquel sont enregistrées les transcriptions PowerShell « de procuration de privilège » après chaque session à distance.
Ces transcriptions vous permettent d’inspecter les actions effectuées dans chaque session de façon lisible.
Pour plus d’informations sur les transcriptions PowerShell, consultez ce [billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Remarque : Windows Eventing capture également des informations sur ce que chaque utilisateur a exécuté avec PowerShell.
Les transcriptions sont juste un peu plus faciles à lire.

Enfin, enregistrez vos modifications dans *JEADemo2.pssc*.

## Appliquer la configuration de session PowerShell

Pour créer un point de terminaison à partir d’un fichier de configuration de session, vous devez inscrire ce fichier.
Quelques éléments d’information sont alors nécessaires :

1. Le chemin du fichier de configuration de session.
2. Le nom de votre configuration de session inscrite. Il s’agit du même nom que celui que les utilisateurs fournissent pour le paramètre « ConfigurationName » quand ils se connectent à votre point de terminaison avec `Enter-PSSession` ou `New-PSSession`.

Pour inscrire la configuration de session sur votre ordinateur local, exécutez la commande suivante :

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Félicitations ! Vous avez configuré votre point de terminaison JEA.

## Tester votre point de terminaison
Réexécutez les étapes répertoriées dans la section [Utilisation de JEA](using-jea.md) pour votre nouveau point de terminaison afin de vérifier qu’il fonctionne comme prévu.
Veillez à utiliser le nouveau nom de point de terminaison (JEADemo2) quand vous indiquez le nom de la configuration dans l’applet de commande `Enter-PSSession`.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## Concepts clés
**Configuration de session PowerShell** : parfois appelée *point de terminaison PowerShell*, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.
Vous pouvez répertorier les configurations de session inscrites sur votre système en exécutant `Get-PSSessionConfiguration`.
Paramétrée de manière spécifique, une configuration de session PowerShell peut être appelée *point de terminaison JEA*.

**Fichier de configuration de session PowerShell (.pssc)** : fichier qui, une fois inscrit, définit les paramètres d’une configuration de session PowerShell.
Il contient des spécifications pour les rôles d’utilisateurs qui peuvent se connecter au point de terminaison, le compte d’identification virtuel, etc.     

**Définitions de rôles** : champ dans un fichier de configuration de session qui définit les capacités de rôle accordées aux utilisateurs qui tentent d’établir une connexion.
Ce champ définit *qui* peut faire *quoi* en tant que compte privilégié.
Là est l’essence des fonctionnalités RBAC de JEA.

**SessionType** : champ dans un fichier de configuration de session qui représente les paramètres par défaut d’une configuration de session.
Pour les points de terminaison JEA, ce champ doit avoir la valeur RestrictedRemoteServer.

**Transcription PowerShell** : fichier contenant une vue par procuration de privilège d’une session PowerShell.
Vous pouvez définir PowerShell de sorte à générer des transcriptions pour les sessions JEA à l’aide du champ TranscriptDirectory.
Pour plus d’informations sur les transcriptions, consultez ce [billet de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).




<!--HONumber=Jul16_HO1-->


