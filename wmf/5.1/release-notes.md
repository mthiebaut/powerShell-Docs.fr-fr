---
title: "Notes de publication de WMF 5.1 (préversion)"
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 5eb9eae6257cdb57f4f778b5dddf5aa7ef9d10bb
ms.openlocfilehash: 12f2c084ab92134b733ee037c3d9fbd512af2e4c

---

# Notes de publication de Windows Management Framework (WMF) 5.1 Preview #

WMF 5.1 Preview comprend les composants PowerShell, WMI, WinRM et SIL (Software Inventory and Licensing), qui sont publiés avec Windows Server 2016. WMF 5.1 peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, et fournit plusieurs améliorations par rapport à WMF 5.0 RTM, notamment :

- Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo
- Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA
- Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB
- Améliorations du débogage pour les classes DSC et PowerShell
- Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet
- Réponses à plusieurs demandes et problèmes des utilisateurs

**Remarques importantes :**

- **WMF 5.1 Preview nécessite Windows Management Framework 4.6**. L’installation réussit, mais des fonctionnalités clés échouent si .NET 4.6 n’est pas installé. Des instructions sont disponibles dans la rubrique [Installer et configurer WMF 5.1 (Preview)](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure). 
- **WMF 5.1 Preview n’est pas pris en charge pour les déploiements de production** pour l’instant. Cette préversion est destinée à fournir des informations sur le contenu de la version et à vous donner la possibilité de fournir des commentaires à l’équipe PowerShell.
- WMF 5.1 Preview peut être installé directement sur WMF 5.0.
- Le fait que WMF 4.0 est actuellement nécessaire pour pouvoir installer WMF 5.1 Preview sur Windows 7 et Windows Server 2008 est un problème connu. Cette condition requise devrait être supprimée avant la version finale.
- L’installation des prochaines versions de WMF 5.1, notamment la version RTM, nécessitera la désinstallation de WMF 5.1 Preview.



<!--HONumber=Jul16_HO5-->


