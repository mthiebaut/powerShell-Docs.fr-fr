---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 814b1172505e1bac59a75fee494e9741f7d1f820
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="enhanced-transcription-options"></a>Options de transcription améliorées

La transcription Windows PowerShell a été améliorée pour s’appliquer à toutes les applications d’hébergement (telles que Windows PowerShell ISE), et pas simplement à l’hôte de la console (powershell.exe).

Outre l’extension de la transcription, la fonctionnalité de transcription proprement dite a été mise à jour pour prendre en charge l’imbrication arbitraire des transcriptions, des métadonnées supplémentaires dans l’en-tête de transcription résultant, et la définition d’un répertoire de sortie de transcription (pour prendre en charge la collecte de journaux centralisée).

Vous pouvez configurer les options de transcription (notamment activer une transcription à l’échelle du système) avec le paramètre stratégie de groupe **Activer la transcription PowerShell** (Modèles d’administration -> Composants Windows -> Windows PowerShell).