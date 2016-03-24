# Remettre un document de configuration sans l’appliquer

L’applet de commande **Publish-DscConfiguration** copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration. Cette configuration est appliquée lors de la passe de cohérence suivante, ou quand vous exécutez l’applet de commande `Update-DscConfiguration`.

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
