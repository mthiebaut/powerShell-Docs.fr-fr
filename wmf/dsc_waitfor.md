# Spécification de dépendances entre nœuds

Avec les ressources WaitFor\* intégrées (WaitForAll, WaitForAny et WaitForSome), vous pouvez maintenant spécifier des dépendances entre ordinateurs lors des exécutions de configuration, sans orchestration externe. Le comportement de chaque ressource WaitFor\* est le suivant :

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> attend que la ressource spécifiée soit à l’état souhaité sur <ctype="x-NOTFOUND" mdpre="*" mdpost="*">tous</ctype="x-NOTFOUND"> les nœuds cibles définis dans la propriété NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> attend que la ressource spécifiée soit à l’état souhaité sur <ctype="x-NOTFOUND" mdpre="*" mdpost="*">n’importe quel</ctype="x-NOTFOUND"> nœud cible défini dans la propriété NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> attend que la ressource spécifiée soit à l’état souhaité sur un nombre spécifique (défini par la propriété NodeCount) de nœuds cibles définis dans la propriété NodeName.

Ces ressources fournissent une synchronisation de nœud à nœud à l’aide de connexions CIM sur le protocole WS-Man. Grâce à ces ressources, une configuration peut attendre que l’état d’une ressource spécifique d’un autre ordinateur change avant de poursuivre sa propre configuration. 

Par exemple, dans la configuration suivante, le nœud cible attend que la ressource <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> se termine sur le nœud <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> avec quelques nouvelles tentatives, avant que le nœud cible puisse joindre le domaine.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">Conseil :</ctype="x-NOTFOUND"> Par défaut, les ressources WaitFor\* essaient une seule fois puis échouent. Même si ce n’est pas obligatoire, vous pouvez spécifier un intervalle et un nombre de nouvelles tentatives.


<!--HONumber=Mar16_HO3-->


