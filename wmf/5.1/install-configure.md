---
title: "Installer et configurer WMF 5.1 (préversion)"
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a53817d6af625822d9183d2a0d5bc7bf4d2b264
ms.openlocfilehash: 058d18deeb3d4926970ea25a157f92ad14836e4b

---

# Installer et configurer WMF 5.1 (préversion) #

## Installer .NET 4.6
Vous devez installer le .NET Framework 4.6 pour utiliser WMF 5.1. Cette opération est nécessaire pour activer les nouvelles fonctionnalités de signature de catalogue, ce qui a un impact sur plusieurs aspects du chargement des modules et des scripts dans WMF 5.1. 

Le [.NET Framework 4.6 est disponible dans l’article de la Base de connaissances 3045560](https://support.microsoft.com/en-us/kb/3045560). Des instructions d’installation sont disponibles à l’emplacement du téléchargement.

> **Remarque :** Le fait que le programme d’installation de WMF 5.1 Preview ne détecte pas l’absence de .NET 4.6 est un problème connu : il vous sera donc possible d’installer WMF 5.1 Preview avant d’installer .NET 4.6. Nos tests ont montré que vous pouvez installer .NET 4.6 après avoir installé WMF 5.1 Preview. La version finale de WMF 5.1 vérifiera correctement cette configuration requise avant l’installation. 

## Télécharger et installer WMF 5.1

Téléchargez le package WMF 5.1 correspondant au système d’exploitation et à l’architecture sur lesquels vous souhaitez installer :

| Système d'exploitation       | Conditions préalables | Liens de package             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Mise à jour de sécurité pour [la signature du code SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64 :** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86 :** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Mise à jour de sécurité pour [la signature du code SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | **x64 :** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86 :** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## Installer WMF 5.1 à partir de l’Explorateur Windows (ou de l’Explorateur de fichiers dans Windows Server 2012 R2 ou Windows 8.1)

1. Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.

2. Double-cliquez sur le fichier MSU pour l’exécuter.

## Installer WMF 5.1 à partir de l’invite de commandes##

1. Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur). Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.

2. Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.1.

3. Exécutez l’une des commandes suivantes :
    - Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`.
    - Sur les ordinateurs qui exécutent Windows Server 2012, exécutez `W2K12-KB3156423-x64.msu /quiet`.
    - Sur les ordinateurs qui exécutent Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, exécutez `Win7AndW2K8R2-KB3156424-x64.msu /quiet`.
    - Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez `Win8.1-KB3156422-x86.msu /quiet`.
    - Sur les ordinateurs qui exécutent Windows 7 SP1 x86, exécutez `Win7-KB3156424-x86.msu /quiet`.

## Notes d’installation supplémentaires pour Windows Server 2008 SP1 et Windows 7 SP1##
L’installation de WMF 5.1 sur Windows Server 2008 SP1 ou Windows 7 SP1 nécessite l’installation des éléments suivants :
- Service Pack le plus récent
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1 nécessite [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560). Vous pouvez installer Microsoft .NET Framework 4.6 en suivant les instructions à l’emplacement du téléchargement.
- Mise à jour de sécurité pour [la signature du code SHA-2](https://technet.microsoft.com/en-us/library/security/3033929). Ceci est nécessaire pour utiliser les nouvelles applets de commande PowerShell pour les fichiers catalogue Windows. 

> **Dépendance de WinRM** : la Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7. Pour activer WinRM, dans une session Windows PowerShell avec élévation des privilèges, exécutez `Set-WSManQuickConfig`.




<!--HONumber=Jul16_HO5-->


