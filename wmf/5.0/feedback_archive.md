---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a>Applets de commande d’archive

Deux nouvelles applets de commande, **compression-Archive** et **Expand-Archive**, permettent de compresser et de décompresser des fichiers ZIP.

## <a name="compress-archive"></a>Compress-Archive
L’applet de commande **Compress-Archive** crée un fichier d’archive à partir de fichiers spécifiés. Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage. Un fichier d’archive peut être compressé à l’aide d’un algorithme de compression spécifié par le paramètre **-CompressionLevel**.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
L’applet de commande **Expand-Archive** extrait les fichiers à partir d’un fichier d’archive spécifié. Un fichier d’archive permet d’empaqueter, et éventuellement de compresser, plusieurs fichiers dans un fichier unique pour faciliter la gestion et le stockage.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

