---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: "Annexe 1 : Alias de compatibilité"
ms.technology: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 126c124bd9bd4aa7c724fc0ef0b075a649d66f44
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="appendix-1---compatibility-aliases"></a>Annexe 1 - Alias de compatibilité
Windows PowerShell dispose de plusieurs alias de transition qui permettent aux utilisateurs d’UNIX et de Cmd d’utiliser des noms de commande familiers dans Windows PowerShell. Les alias courants sont répertoriés dans le tableau ci-dessous, ainsi que la commande Windows PowerShell sous-jacente, et l’alias Windows PowerShell standard, s’il en existe.

Pour trouver la commande Windows PowerShell vers laquelle pointe un alias, dans Windows PowerShell utilisez l’applet de commande Get-Alias. Par exemple, tapez **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Commande CMD|Commande UNIX|Commande PS|Alias PS|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (fonction)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|

