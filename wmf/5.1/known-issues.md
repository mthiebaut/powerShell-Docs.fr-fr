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
ms.sourcegitcommit: f413ba6470985622e55bb4bd175d7c5d4b94c7d9
ms.openlocfilehash: e545d49381a92ef3f7cc6a27316cbfc3a036a8c9

---

#Problèmes connus dans WMF 5.1 (préversion) #

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

##Pester
Dans cette version, vous devez savoir qu’il existe deux problèmes quand vous utilisez Pester sur Nano Server :

* L’exécution des tests directement sur Pester peut entraîner des échecs en raison des différences entre la version CLR complète et la version CLR de base. En particulier, la méthode Validate n’est pas disponible sur le type XmlDocument. Six tests qui tentent de valider le schéma des journaux de sortie NUnit échouent systématiquement. 
* Un test de couverture du code échoue, car la ressource DSC *WindowsFeature* n’existe pas dans Nano Server. Toutefois, ces échecs sont généralement sans conséquence et peuvent être ignorés.

##Validation de l’opération 

* Update-Help échoue pour le module Microsoft.PowerShell.Operation.Validation en raison d’un URI d’aide qui ne fonctionne pas



<!--HONumber=Sep16_HO3-->


