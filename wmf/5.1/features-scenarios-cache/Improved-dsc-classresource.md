---
title: "Améliorations des ressources de classe DSC"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## Améliorations des ressources de classe DSC

Dans cette version, nous avons résolu les problèmes connus suivants de WMF 5.0 :
* Get-DscConfiguration peut retourner des valeurs vides (Null) ou des erreurs si un type complexe/de table de hachage est retourné par la fonction Get() d’une ressource DSC basée sur une classe.
* Get-DscConfiguration retourne une erreur si des informations d’identification RunAs sont utilisées dans une configuration DSC.
* Une ressource basée sur une classe ne peut pas être utilisée dans une configuration composite.
* Start-DscConfiguration se bloque si une ressource basée sur une classe a une propriété de son propre type.
* Une ressource basée sur une classe ne peut pas être utilisée comme ressource exclusive.



<!--HONumber=Jul16_HO3-->


