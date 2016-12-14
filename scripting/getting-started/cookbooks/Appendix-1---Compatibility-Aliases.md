---
title: "Annexe 1   Alias de compatibilité"
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
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

