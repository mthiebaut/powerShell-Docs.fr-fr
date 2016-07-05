---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "création de rapports sur JEA"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# Création de rapports sur JEA
Étant donné que JEA permet à des utilisateurs non privilégiés de s’exécuter dans un contexte privilégié, la journalisation et l’audit sont extrêmement importants.
Dans cette section, nous allons passer en revue les outils que vous pouvez utiliser pour la journalisation et la création de rapports.

## Création de rapports sur les actions JEA
### Transcription de procuration de privilège
Un des moyens les plus rapides d’obtenir un résumé de ce qui se passe au cours d’une session PowerShell consiste à observer une personne qui tape au clavier.
Vous voyez ses commandes, la sortie de ces commandes et tout va bien.
Ou pas, mais au moins vous savez.
La transcription PowerShell a pour but de vous donner un aperçu similaire après coup.

Quand vous utilisez le champ « TranscriptDirectory » dans votre configuration de session, PowerShell enregistre automatiquement une transcription de toutes les actions effectuées au cours d’une session donnée.
Vous pouvez trouver des transcriptions de vos sessions dans ce document : « $env:ProgramData\JEAConfiguration\Transcripts ».

Comme vous pouvez le voir, la transcription enregistre des informations sur l’utilisateur « connecté », l’utilisateur « du compte d’identification », les commandes exécutées pendant la session et bien plus encore.
Pour plus d’informations sur la transcription PowerShell, consultez [ce billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

### Journaux des événements PowerShell
Quand l’enregistrement des modules est activé, toutes les actions PowerShell sont également enregistrées dans les journaux des événements Windows standard.
Ces journaux sont un peu plus délicats à gérer par rapport aux transcriptions, mais le niveau de détail qu’ils donnent peut vous être utile.

Dans le journal des opérations « PowerShell », l’ID d’événement 4104 enregistre chaque commande appelée si vous avez activé l’enregistrement des modules.

### Autres journaux des événements
Contrairement aux journaux et transcriptions PowerShell, les autres mécanismes de journalisation ne capturent pas « l’utilisateur connecté ».
Vous devrez effectuer une corrélation entre les autres journaux et les journaux PowerShell pour faire correspondre les actions effectuées.

Dans le journal des opérations « Windows Remote Management », l’ID d’événement 193 enregistre le SID et le nom de l’utilisateur, ainsi que le SID du compte virtuel d’identification pour faciliter cette corrélation.
Vous avez peut-être également remarqué que le nom du compte virtuel d’identification inclut à la fin le domaine et le nom de l’utilisateur qui tente d’établir une connexion.

## Création de rapports sur la configuration JEA
### Get-PSSessionConfiguration
Pour créer des rapports précis sur l’état de votre environnement, il est important de connaître le nombre de points de terminaison JEA que vous avez configurés sur votre ordinateur.
`Get-PSSessionConfiguration` permet exactement de le déterminer.

### Get-PSSessionCapability
Créer manuellement des rapports sur les capacités d’un utilisateur donné par le biais d’un point de terminaison JEA peut s’avérer assez complexe.
Vous devez probablement inspecter plusieurs capacités de rôle.
Heureusement, l’applet de commande « Get-PSSessionCapability » permet de le faire.

Pour tester, exécutez la commande suivante à partir d’une invite PowerShell d’administrateur :
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jun16_HO4-->


