# Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres

Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples. Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre. 

Pour plus d’informations, consultez [Configuration du gestionnaire de configuration local](../dsc/metaConfig.md).

<!--HONumber=Jun16_HO4-->


