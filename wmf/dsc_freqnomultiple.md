# Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres

Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples, comme expliqué dans [ce blog](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx). Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre. Les tableaux ci-dessous illustrent ce comportement :

Comportement en mode **par extraction** : 

|                                  |**Valeur dans la métaconfiguration**|**Valeur après application de la métaconfiguration**|**Fréquence d’extraction (en minutes)**|**Fréquence d’application de la configuration (en minutes)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

Comportement en mode **par envoi** :

|                                  |**Valeur dans la métaconfiguration**|**Valeur après application de la métaconfiguration**|**Fréquence d’application de la configuration (en minutes)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
