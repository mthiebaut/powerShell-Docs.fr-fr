---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Notes de publication de WMF 5.1
ms.openlocfilehash: f80c1ec5886578e3e43f2c96981f40152db000d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="windows-management-framework-wmf-51-release-notes" class="xliff"></a>
# Notes de publication de Windows Management Framework (WMF) 5.1 #

WMF 5.1 comprend les composants PowerShell, WMI, WinRM et SIL (Software Inventory and Licensing) qui sont publiés avec Windows Server 2016.
WMF 5.1 peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, et fournit plusieurs améliorations par rapport à WMF 5.0 RTM, notamment :

- Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

**Remarques importantes :**

- **WMF 5.1 nécessite le .NET Framework 4.5.2**. L’installation réussit, mais des fonctionnalités clés échouent si le .NET Framework 4.5.2 n’est pas installé. Des instructions sont disponibles dans la rubrique [Installer et configurer WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure).
- La version préliminaire de WMF 5.1 doit être désinstallée avant d’installer la version WMF 5.1 RTM.
- WMF 5.1 peut être installé directement sur WMF 5.0 ou WMF 4.0.
- Il n’est __pas nécessaire__ d’installer WMF 4.0 avant d’installer WMF 5.1 sur Windows 7 et Windows Server 2008 R2. C’était un problème lié à version 5.1 WMF qui a été résolu.  


