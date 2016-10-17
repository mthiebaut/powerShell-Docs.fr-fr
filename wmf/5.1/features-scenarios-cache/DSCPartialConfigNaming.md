---
title: Convention de nommage pour une configuration partielle de collecte
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##Convention de nommage pour une configuration partielle de collecte
Dans les versions précédentes, la convention de nommage pour une configuration partielle précisait que le nom du fichier mof dans le service/serveur collecteur devait correspondre au nom de configuration partielle spécifié dans les paramètres du gestionnaire de configuration local qui, à son tour, devait correspondre au nom de configuration incorporé dans le fichier MOF. Consultez les captures instantanées ci-dessous :- •   Paramètres de configuration locaux qui définissent une configuration partielle qu’un nœud est autorisé à recevoir.

![Exemple de métaconfiguration](../../images/MetaConfigPartialOne.png)

•   Exemple de définition de configuration partielle 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   ConfigurationName incorporé dans le fichier MOF généré.

![Exemple de fichier mof généré](../../images/PartialGeneratedMof.png)

•   FileName dans le dépôt de configuration de collecte 

![FileName dans le dépôt de configuration](../../images/PartialInConfigRepository.png)

Le nom de service Azure Automation a généré des fichiers mof sous la forme ``<ConfigurationName>.<NodeName>.mof``. Par conséquent, la configuration ci-dessous est compilée dans PartialOne.Localhost.mof.  
Il est ainsi impossible de collecter une configuration partielle à partir du service Azure Automation.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

Dans WMF 5.1, une configuration partielle dans le service/serveur collecteur peut être nommée ``<ConfigurationName>.<NodeName>.mof``. En outre, si un ordinateur collecte une seule configuration d’un service/serveur collecteur, le document de configuration dans le référentiel de configuration du serveur collecteur peut avoir n’importe quel nom. Cette souplesse de nommage vous permet de gérer la configuration partielle d’un nœud à la fois en local et à l’aide du service collecteur Azure Automation. Par exemple, vous pouvez avoir une configuration partielle « de base » émise en local et une autre configuration partielle collectée à partir du service Azure Automation.

La métaconfiguration ci-dessous définit un nœud à gérer à la fois localement ainsi que par le service Azure Automation.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


