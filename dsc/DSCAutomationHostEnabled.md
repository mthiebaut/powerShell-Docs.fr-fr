
DSC utilise la clé de Registre <b>DSCAutomationHostEnabled </b>sous <b>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</b> pour configurer automatiquement la machine au premier démarrage.
DSCAutomationHostEnabled prend en charge trois modes :

|  Valeur de DSCAutomationHostEnabled  |  Description   | 
|---|---| 
0 | Désactive la configuration de la machine au démarrage. |
1 | Active la configuration de la machine au démarrage. |
2 | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s’agit de la valeur par défaut. |




<!--HONumber=Oct16_HO2-->


