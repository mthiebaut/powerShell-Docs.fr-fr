---
title: "Améliorations de la console dans WMF 5.1 (préversion)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 221b8095c15a810c032bd93aafe8ec886af233d9

---

# Améliorations de la console dans WMF 5.1 (préversion)#

## Améliorations de la console PowerShell

Les modifications suivantes ont été apportées à Powershell.exe dans WMF 5.1 pour améliorer l’expérience de la console :

###Prise en charge de VT100

Ajout dans Windows 10 de la prise en charge des [séquences d’échappement VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignore certaines séquences d’échappement de mise en forme VT100 lors du calcul des largeurs de tableaux.

Ajout dans PowerShell d’une nouvelle API que vous pouvez utiliser dans le code de mise en forme pour déterminer si VT100 est pris en charge. Par exemple :

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Voici un [exemple](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) complet que vous pouvez utiliser pour mettre en surbrillance des correspondances à partir de Select-String.
Enregistrez l’exemple dans un fichier nommé `MatchInfo.format.ps1xml` puis, pour l’utiliser, dans votre profil ou ailleurs, exécutez `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Notez que les séquences d’échappement VT100 sont prises en charge uniquement à compter de la Mise à jour anniversaire Windows 10. Elles ne sont pas prises en charge sur les systèmes antérieurs.   

### Prise en charge du mode vi dans PSReadline

Ajout de la prise en charge du mode vi dans [PSReadline](https://github.com/lzybkr/PSReadLine). Pour utiliser le mode vi, exécutez `Set-PSReadline -EditMode vi`.

### Stdin redirigé avec entrée interactive 

Dans les versions antérieures, démarrer PowerShell avec `powershell -File -` était nécessaire quand stdin était redirigé et que vous souhaitiez entrer des commandes de manière interactive.

Avec WMF 5.1, cette option difficile à découvrir n’est plus nécessaire. Vous pouvez démarrer powershell sans option, par exemple `powershell`.

Notez qu’à l’heure actuelle PSReadline ne prend pas en charge stdin redirigé, et que l’expérience de modification de ligne de commande intégrée avec stdin redirigé est très limitée (par exemple, les touches de direction ne fonctionnent pas).  Une version ultérieure de PSReadline doit résoudre ce problème.   



<!--HONumber=Jul16_HO3-->


