# Séparation des ID de nœud et de configuration

## Vue d’ensemble

Afin d’offrir une expérience plus flexible et rationalisée lors de l’utilisation de DSC en mode par extraction, nous avons ajouté un certain nombre de fonctionnalités dans cette version. Ces fonctionnalités ont pour but de vous aider à configurer et à déployer des configurations sur plusieurs nœuds de manière simple et flexible, tout en assurant le suivi et en fournissant des informations pour chaque nœud. Il s’agit des fonctionnalités suivantes :

* Un nom de configuration qui identifie la configuration d’un ordinateur. Ce nom peut être partagé par plusieurs nœuds cibles. 
* Un ID d’agent qui identifie de façon unique un nœud unique.
* Une étape d’inscription qui est exécutée uniquement la première fois qu’un nœud cible se connecte à un serveur collecteur.

**Remarque :** Ces fonctionnalités ont été ajoutées et ne remplacent pas les fonctionnalités et les concepts d’extraction existants. Vous pouvez utiliser ces nouvelles fonctionnalités ou les anciennes avec le nouveau serveur collecteur fourni avec cette version.

## ID d’agent

Cette fonctionnalité s’adresse aux utilisateurs qui ne souhaitent pas configurer et gérer des identificateurs uniques pour chaque nœud cible. Désormais, plus aucune comptabilité des GUID n’est nécessaire. DSC génère automatiquement un ID d’agent qu’il utilise pour communiquer avec le serveur collecteur. Cet ID est utilisé par le serveur collecteur pour identifier de manière unique toutes les informations avec un nœud donné. Cela signifie également que vous n’avez pas besoin de configurer chaque nœud cible avec une métaconfiguration unique contenant un ID unique. Une même métaconfiguration peut être utilisée par plusieurs nœuds cibles tout en conservant l’identité unique de chaque nœud. 

## Nom de la configuration

Le nom de la configuration est un nom convivial qui définit la configuration qu’un nœud cible appliquera. Les modifications associées sont les suivantes :  

### Nom convivial

Il peut s’agir de n’importe quelle chaîne. Il n’est pas nécessaire qu’elle soit au format GUID. Ainsi, une configuration qui configure SQL Server peut se nommer simplement « SQL_Server ». Il est ainsi beaucoup plus facile d’identifier ce que fait une configuration donnée.

### Affectation

La configuration affectée à un nœud cible est gérée de façon centralisée sur le serveur collecteur. Vous pouvez l’initialiser en définissant la propriété ConfigurationName dans la métaconfiguration, mais elle est utilisée uniquement lors de l’inscription. Après l’inscription, le serveur indique au nœud cible la configuration qu’il recevra. Pour le serveur collecteur local, ce mappage entre les configurations et les nœuds cibles peut être effectué uniquement pendant l’inscription, mais dans Azure Automation ces modifications peuvent être apportées facilement dans l’interface utilisateur ou par le biais des applets de commande. Pour modifier la configuration affectée à un nœud cible pour le serveur collecteur local, vous pouvez réexécuter l’inscription.

### Configurations multiples/partielles

Si plusieurs noms de configurations sont affectés à un nœud cible, elles sont traitées comme des configurations partielles. Pour que cela fonctionne, la métaconfiguration sur le nœud cible doit être configurée pour accepter les configurations partielles. **Remarque :** Cela est pris en charge uniquement sur le serveur collecteur local. Azure Automation ne prend pas en charge les configurations partielles.

## Inscription

Les noms des configurations n’étant plus des GUID (il s’agit désormais de noms conviviaux), n’importe qui peut les deviner. Pour atténuer le risque de sécurité inhérent, nous avons ajouté une étape d’inscription avant qu’un nœud puisse commencer à demander des configurations à un serveur. Un nœud s’inscrit auprès du serveur collecteur avec un secret partagé (que le nœud et le serveur connaissent déjà) et, éventuellement, le nom de la configuration demandée. Il n’est pas obligatoire que ce secret partagé soit unique pour chaque ordinateur. Supposition : le secret partagé est un identificateur difficile à deviner, comme un GUID. Ce secret partagé est défini par la propriété **RegistrationKey** dans la métaconfiguration du nœud cible.

### Exemple de métaconfiguration

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

La valeur de RegistrationKey doit être définie sur le serveur collecteur. Pour cela, lors de la configuration du serveur collecteur, créez un fichier texte nommé **RegistrationKeys.txt** dans un emplacement spécifique, puis définissez cet emplacement dans le fichier web.config du serveur collecteur, comme indiqué ci-dessous.  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

Utilisez la version la plus récente de la ressource DSC xDSCWebService pour déployer intégralement un serveur collecteur local. Pour obtenir une configuration complète, consultez [Exemple de configuration](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1).

**Remarque :** Cette fonctionnalité n’est pas prise en charge quand le serveur collecteur est configuré comme partage de fichiers. Elle est prise en charge uniquement pour le serveur collecteur basé sur le web.<!--HONumber=Mar16_HO2-->
