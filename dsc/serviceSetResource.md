---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressources ServiceSet dans DSC
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-serviceset-resource" class="xliff"></a>
# Ressources ServiceSet dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible. Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certains services au même état.

<a id="syntax" class="xliff"></a>
## Syntaxe

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

<a id="properties" class="xliff"></a>
## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique les noms des services. Notez qu’ils peuvent être différents des noms d’affichages. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx).|
| StartupType| Indique le type de démarrage du service. Les valeurs autorisées pour cette propriété sont : **Automatic**, **Disabled** et **Manual**|  
| BuiltInAccount| Indique le compte de connexion à utiliser pour les services. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**.| 
| State| Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **En cours d’exécution**.| 
| Ensure| Indique si les services existent sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas. La valeur **Present** (valeur par défaut) permet de s’assurer que le services cibles existent.|
| Credential| Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service. Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource *ResourceName* de type *ResourceType*, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 



<a id="example" class="xliff"></a>
## Exemple

La configuration suivante démarre les services « Audio Windows » et « Services Bureau à distance ».

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

