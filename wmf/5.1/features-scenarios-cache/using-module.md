---
title: FullyQualifiedModuleName pour 'using module'
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

FullyQualifiedModuleName pour 'using module'
=========================

Désormais, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell.

Problèmes liés à WMF 5.0
----------

* L’utilisateur n’a aucun moyen de spécifier la version du module dans `using module`.
* Si plusieurs versions du module sont disponibles sur le système, une erreur s’affiche.

WMF 5.1
----------

* L’utilisateur peut utiliser `ModuleSpecification` [hashtable](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx). Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`

**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* S’il existe plusieurs versions du module, powershell utilise la **même logique de résolution** que `Import-Module` et aucune erreur n’est générée.

* Ainsi, `using module` se comporte comme `Import-Module` et `Import-DscResource`.



<!--HONumber=Jul16_HO3-->


