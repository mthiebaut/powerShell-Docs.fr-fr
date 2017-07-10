---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="uninstallation-instructions" class="xliff"></a>
# Instructions de désinstallation

<a id="using-command-prompt" class="xliff"></a>
## Utilisation de l’invite de commandes
1.  Ouvrez une **invite de commandes.**
2.  Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :

Sur Windows Server 2012 R2 et Windows 8.1 :
```powershell
wusa /uninstall /kb:3134758
```
Sur Windows Server 2012 :
```powershell
wusa /uninstall /kb:3134759
```
Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :
```powershell
wusa /uninstall /kb:3134760
```

<a id="using-control-panel" class="xliff"></a>
## Utilisation du Panneau de configuration
1.  Ouvrez le **Panneau de configuration.**
2.  Ouvrez **Programmes**, puis **Désinstaller un programme.**
3.  Cliquez sur **Afficher les mises à jour installées.**
4.  Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées. Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*. Cliquez sur **Désinstaller.**

