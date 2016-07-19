---
title: Ressources ServiceSet dans DSC
ms.date: 2016-05-23
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 12438bc9c6e4211b6a31550fa25334a20fde6846
ms.openlocfilehash: 871d697626a0376e8f1f27bdbbf16d8612a56a79

---

# Ressources ServiceSet dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource **ServiceSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible. Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la [ressource Service](serviceResource.md) pour chaque service spécifié dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certains services au même état.

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

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Name| Indique les noms des services. Notez qu’ils peuvent être différents des noms d’affichages. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx).|
| StartupType| Indique le type de démarrage du service. Les valeurs autorisées pour cette propriété sont : **Automatic**, **Disabled** et **Manual**|  
| BuiltInAccount| Indique le compte de connexion à utiliser pour les services. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**.| 
| State| Indique l’état que vous voulez assurer pour les services : **Arrêté** ou **En cours d’exécution**.| 
| Ensure| Indique si les services existent sur le système. Affectez la valeur **Absent** à cette propriété pour vous assurer que les services n’existent pas. La valeur **Present** (valeur par défaut) permet de s’assurer que le services cibles existent.|
| Credential| Indique les informations d’identification pour le compte sous lequel s’exécute la ressource de service. Cette propriété et la propriété **BuiltinAccount** ne peuvent pas être utilisées ensemble.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource *ResourceName* de type *ResourceType*, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 



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




<!--HONumber=Jul16_HO1-->


