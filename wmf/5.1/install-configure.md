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
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# Installer et configurer WMF 5.1 (préversion) #

***Remarque :*** 
*Ce contenu est un espace réservé. Les liens ci-dessous pointent vers les versions WMF 5.0 et seront mis à jour lors de la publication des fichiers binaires.*

Téléchargez le package WMF 5.1 correspondant au système d’exploitation et à l’architecture sur lesquels vous souhaitez installer :

| Système d'exploitation       | Architecture | Nom du package              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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

> **Dépendance de WinRM** : la Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7. Pour activer WinRM, dans une session Windows PowerShell avec élévation des privilèges, exécutez `Set-WSManQuickConfig`.




<!--HONumber=Jul16_HO2-->


