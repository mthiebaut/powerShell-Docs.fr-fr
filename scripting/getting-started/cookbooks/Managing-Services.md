---
title: Gestion des services
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: a9d6ece1df3b66090b2abf9d85019fee4db946b5

---

# Gestion des services
Il existe huit principales applets de commande Service, conçues pour un vaste éventail de tâches de service. Nous examinons ici uniquement le listage et la modification de l’état en cours d’exécution des services, mais vous pouvez obtenir une liste des applets de commande Service à l’aide de l’applet de commande **Get\-Help \&#42;\-Service**. Vous pouvez également trouver des informations sur chaque applet de commande Service à l’aide de la commande **Get\-Help<Nom\-Applet>**, par exemple, **Get\-Help New\-Service**.

## Obtention de services
Vous pouvez obtenir les services sur un ordinateur local ou distant à l’aide de l’applet de commande **Get\-Service**. Comme avec la commande **Get\-Process**, l’utilisation de la commande **Get\-Service** sans paramètre a pour effet de retourner tous les services. Vous pouvez filtrer par nom, même en utilisant un astérisque comme caractère générique :

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Comme il n’est pas toujours évident d’identifier le nom réel d’un service, il se peut que vous deviez rechercher des services par nom d’affichage. À cette fin, vous pouvez utiliser un nom spécifique, des caractères génériques ou une liste de noms d’affichage :

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

Vous pouvez utiliser le paramètre ComputerName de l’applet de commande Get\-Service pour obtenir les services sur des ordinateurs distants. Le paramètre ComputerName acceptant plusieurs valeurs et caractères génériques, vous pouvez obtenir les services sur plusieurs ordinateurs à l’aide d’une seule commande. Par exemple, la commande suivante obtient les services sur l’ordinateur distant Server01.

```
Get-Service -ComputerName Server01
```

## Obtention de services requis et dépendants
L’applet de commande Get\-Service dispose de deux paramètres très utiles dans l’administration des services. Le paramètre DependentServices obtient les services dépendant de ce service. Le paramètre RequiredServices obtient les services dont ce service dépend.

Ces paramètres affichent simplement les valeurs des propriétés DependentServices et ServicesDependedOn (alias\=RequiredServices) de l’objet System.ServiceProcess.ServiceController que l’applet de commande Get\-Service retourne, mais ils simplifient les commandes et facilitent sensiblement l’obtention de ces informations.

La commande suivante obtient les services que le service LanmanWorkstation requiert.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

La commande suivante obtient les services qui requièrent le service LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Vous pouvez même obtenir tous les services qui ont des dépendances. C’est précisément ce que fait la commande suivante. Ensuite, elle utilise l’applet de commande Format\-Table pour afficher les propriétés State, Name, RequiredServices et DependentServices des services sur l’ordinateur.

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## Arrêt, démarrage, interruption et redémarrage de services
Les applets de commande Service ont toutes la même forme générale. Les services peuvent être spécifiés par un nom commun ou nom d’affichage, et prennent des listes et des caractères génériques pour valeurs. Pour arrêter le spouleur d’impression, utilisez ce qui suit :

```
Stop-Service -Name spooler
```

Pour démarrer le spouleur d’impression suite à un arrêt, utilisez ce qui suit :

```
Start-Service -Name spooler
```

Pour interrompre le spouleur d’impression, utilisez ce qui suit :

```
Suspend-Service -Name spooler
```

L’applet de commande **Restart\-Service** fonctionne de la même manière que les autres applets de commande Service, mais nous allons présenter quelques exemples plus complexes pour celle-ci. Dans le cas d’utilisation le plus simple, vous spécifiez le nom du service :

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Vous pouvez remarquer que vous obtenez un message d’avertissement répété sur le démarrage du spouleur d’impression. Lorsque vous effectuez une opération de service qui prend un certain temps, Windows PowerShell vous informe qu’il tente toujours d’effectuer la tâche.

Si vous souhaitez redémarrer plusieurs services, vous pouvez obtenir la liste des services, filtrer ceux-ci, puis effectuer le redémarrage :

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Ces applets de commande Service ne dispose pas de paramètre ComputerName, mais vous pouvez les exécuter sur un ordinateur distant à l’aide de l’applet de commande Invoke\-Command. Par exemple, la commande suivante redémarre le service Spouleur sur l’ordinateur distant Server01.

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## Définition des propriétés d’un service
L’applet de commande Set\-Service modifie les propriétés d’un service sur un ordinateur local ou distant. Étant donné que l’état d’un service est une propriété, vous pouvez utiliser cette applet de commande pour démarrer, arrêter et suspendre un service. L’applet de commande Set\-Service dispose également d’un paramètre StartupType qui permet de modifier le type de démarrage du service.

Pour utiliser l’applet de commande Set\-Service sur Windows Vista et des versions ultérieures de Windows, ouvrez Windows PowerShell avec l’option Exécuter en tant qu’administrateur.

Pour plus d’informations, voir [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## Voir aussi
[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)




<!--HONumber=Jun16_HO4-->


