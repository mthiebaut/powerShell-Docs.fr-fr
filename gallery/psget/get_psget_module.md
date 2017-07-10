---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galerie,powershell,cmdlet,psget
title: Obtenir le module PowerShellGet
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="get-powershellget-module" class="xliff"></a>
Obtenir le module PowerShellGet
========================

<a id="powershellget-is-an-in-box-module-in-the-following-releases" class="xliff"></a>
### PowerShellGet est un module inclus par défaut dans les versions suivantes
- [Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) ou version ultérieure
- [Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) ou version ultérieure
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou version ultérieure
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

<a id="get-powershellget-module-for-powershell-versions-30-and-40" class="xliff"></a>
### Obtenir le module PowerShellGet pour les versions PowerShell 3.0 et 4.0
- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

<a id="get-the-latest-version-from-powershell-gallery" class="xliff"></a>
### Obtenir la dernière version de PowerShell Gallery

- Avant d’effectuer la mise à jour de PowerShellGet, vous devez toujours installer le dernier fournisseur Nuget. Pour ce faire, exécutez la commande suivante dans une session PowerShell avec élévation de privilèges.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

<a id="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget" class="xliff"></a>
#### Pour les systèmes avec PowerShell 5.0 (ou version ultérieure), vous pouvez installer la dernière version de PowerShellGet 
- Pour effectuer cette opération sous Windows 10, Windows Server 2016, tout système équipé de WMF 5.0 ou 5.1, ou tout système équipé de PowerShell 6, exécutez les commandes suivantes à partir d’une session PowerShell avec élévation de privilèges.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Utilisez Update-Module pour obtenir les versions plus récentes.
```powershell
Update-Module -Name PowerShellGet
Exit
```

<a id="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409" class="xliff"></a>
#### Pour les systèmes exécutant PowerShell 3 ou PowerShell 4 et qui ont installé [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Utilisez l’applet de commande PowerShellGet ci-dessous à partir d’une session PowerShell avec élévation de privilèges pour enregistrer les modules dans un répertoire local

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Assurez-vous que les modules PowerShellGet et PackageManagment ne sont pas chargés dans d’autres processus.
- Supprimez le contenu des dossiers `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` et `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Ouvrez à nouveau la Console PS avec élévation de privilèges, puis exécutez les commandes suivantes.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force