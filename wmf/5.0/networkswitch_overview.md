# Gestion du commutateur réseau avec PowerShell

L’applet de commande **Get-NetworkSwitchEthernetPort** retourne les informations supplémentaires suivantes avec les instances :
-   IPAddress : adresse IP associée au port
-   PortMode : mode du port (accès, itinéraire ou trunk)
-   AccessVLAN : ID du réseau local virtuel associé à ce port en mode accès
-   TrunkedVLANList : liste des ID des réseaux locaux virtuels associés à ce port en mode trunk

## Gestion fondamentale du commutateur réseau avec Windows PowerShell
Les applets de commande du commutateur réseau, introduites dans la première version WMF 5.0 Preview, permettent d’appliquer une configuration de port de commutateur, de réseau local virtuel (VLAN) et de commutateur réseau de base de couche 2 à des commutateurs réseau certifiés par logo Windows Server 2012 R2. Microsoft s’engage à prendre en charge la vision DAL ([Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) Layer) et à démontrer la valeur à nos clients et partenaires dans cet espace. Ces applets de commande vous permettent d’effectuer les opérations suivantes :

-   Configuration globale du commutateur, par exemple :
    -   Définir le nom d’hôte
    -   Définir la bannière de commutateur
    -   Conserver la configuration
    -   Activer ou désactiver une fonctionnalité

-   Configuration de réseau local virtuel :
    -   Créer ou supprimer un réseau local virtuel
    -   Activer ou désactiver un réseau local virtuel
    -   Énumérer les réseaux locaux virtuels
    -   Définir le nom convivial d’un réseau local virtuel

-   Configuration de port de couche 2 :
    -   Énumérer les ports
    -   Activer ou désactiver des ports
    -   Définir les propriétés et les modes des ports
    -   Ajouter ou associer un réseau local virtuel à Trunk ou Accès sur le port

Commencez à explorer en recherchant toutes les applets de commande NetworkSwitch !

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Vous trouverez des informations supplémentaires dans le billet de blog de Jeffrey Snover sur WMF 5.0 Preview : <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>


<!--HONumber=Jun16_HO4-->


