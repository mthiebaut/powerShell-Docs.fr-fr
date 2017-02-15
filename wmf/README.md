---
title: Windows Management Framework (WMF)
ms.date: 2017-02-14
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 749dd8b19592cb5f40a5aed32d28edeb5cb2dfc9
ms.sourcegitcommit: bb2c52577a519c0599a0b3c961f749fe0df70a45
translationtype: HT
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) est le mécanisme de remise qui fournit une interface de gestion cohérente sur les différentes versions de Windows et Windows Server.
Quand WMF est installé, les clients peuvent interagir de manière transparente entre des combinaisons de systèmes d’exploitation dans leur environnement.
WMF rend les mises à jour des fonctionnalités de gestion, dans une version donnée de Windows et Windows Server, disponibles pour installation sur des versions inférieures (en général, deux versions inférieures) de Windows et Windows Server.

L’installation de WMF ajoute ou met à jour les fonctionnalités suivantes :

- Windows PowerShell
- Configuration de l’état souhaité de Windows PowerShell (DSC)
- Windows PowerShell Integrated Script Environment (ISE)
- Windows Remote Management (WinRM)
- Infrastructure de gestion Windows (WMI, Windows Management Instrumentation)
- Windows PowerShell Web Services (Extension ISS Management OData)
- Journalisation de l’inventaire logiciel
- Fournisseur CIM de Gestionnaire de serveur

## <a name="wmf-release-notes"></a>Notes de publication de WMF

Pour en savoir plus sur les diverses améliorations apportées à PowerShell et d’autres composants d’une version donnée de WMF, consultez les liens ci-dessous pour consulter les notes de publication :

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilité de WMF sur les systèmes d’exploitation Windows

| Version du système d'exploitation | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Fourni par défaut |  |  |  |  |
| Windows 10 | Fourni par défaut | Fourni par défaut  | | | |  
| Windows Server 2012 R2| Oui | Oui | Fourni par défaut |  |  |
| Windows 8.1 | Oui | Oui |  Fourni par défaut |  |  |
| Windows Server 2012 | Oui | Oui | Oui |  Fourni par défaut | |
| Windows 8 |  |  |  | Fourni par défaut | |
| Windows Server 2008 R2 SP1 | Oui | Oui | Oui |  Oui| Fourni par défaut |
| Windows 7 SP1  | Oui | Oui | Oui | Oui | Fourni par défaut |
| Windows Server 2008 SP2 | | | | Oui | Oui |
| Windows Vista | | | | | Oui |
| Windows Server 2003| | | |  | Oui |
| Windows XP | | | |  | Oui |

**« Fourni par défaut »** : les fonctionnalités de `specified WMF` ont été fournies dans la version indiquée de Windows et Windows Server.
Par conséquent, `specified WMF` n’a pas besoin d’être installé sur les versions indiquées du système d’exploitation.
