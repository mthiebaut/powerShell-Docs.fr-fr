# Informations détaillées sur l’état du gestionnaire de configuration local

Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local. Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.
<!--HONumber=Mar16_HO2-->
