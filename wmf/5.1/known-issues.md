---
title: "Problèmes connus dans WMF 5.1 (préversion)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 387ebc0467b9f154444292f391af0f4b77123639

---

#Problèmes connus dans WMF 5.1 (préversion) #

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

##Problèmes liés à Pester
Dans cette version, vous devez savoir qu’il existe deux problèmes quand vous utilisez Pester sur Nano Server :

* L’exécution des tests directement sur Pester peut entraîner des échecs en raison des différences entre la version CLR complète et la version CLR de base. En particulier, la méthode Validate n’est pas disponible sur le type XmlDocument. Six tests qui tentent de valider le schéma des journaux de sortie nunit échouent systématiquement. 
* Un test de couverture du code échoue, car la ressource DSC *WindowsFeature* n’existe pas dans Nano Server. Toutefois, ces échecs sont généralement sans conséquence et peuvent être ignorés.


<!--HONumber=Jul16_HO3-->


