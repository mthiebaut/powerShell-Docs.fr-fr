---
title:   Ressource Service dans DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Ressource Service dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource **Service** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des services sur un nœud cible.

## Syntaxe

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Name| Indique le nom du service Notez qu’il peut être différent du nom d’affichage. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande Get-Service.| 
| BuiltInAccount| Indique le compte de connexion à utiliser pour le service. Les valeurs autorisées pour cette propriété sont : **LocalService**, **LocalSystem** et **NetworkService**.| 
| Credential| Indique les informations d’identification pour le compte sous lequel s’exécute le service. Cette propriété et la propriété __BuiltinAccount__ ne peuvent pas être utilisées ensemble.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Indique le type de démarrage du service. Les valeurs autorisées pour cette propriété sont : **Automatic**, **Disabled** et **Manual**| 
| State| Indique l’état que vous voulez assurer pour le service.| 

## Exemple

```powershell
Service ServiceExample
{
    Name = "TermService"
    StartupType = "Manual"
    State = "Running"
} 
```



<!--HONumber=May16_HO3-->


