
---
titre :   Clé de Registre DSCAutomationHostEnabled ms.date:  16-05-2016 mots clés :  powershell,description DSC:  
ms.topic:  article author:  eslesar manager:  dongill ms.prod:  powershell
---

>S’applique à : Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Clé de Registre DSCAutomationHostEnabled

DSC utilise la clé de Registre **DSCAutomationHostEnabled **sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** pour configurer automatiquement la machine lors du démarrage initial.
DSCAutomationHostEnabled prend en charge trois modes :

|  Valeur de DSCAutomationHostEnabled  |  Description   | 
|---|---| 
0 | Désactive la configuration de la machine au démarrage. |
1 | Active la configuration de la machine au démarrage. |
2 | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s’agit de la valeur par défaut. |

## <a name="see-also"></a>Voir aussi

Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).


