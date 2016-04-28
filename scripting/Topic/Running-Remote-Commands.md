---
title: Exécution de commandes à distance
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# Exécution de commandes à distance
Vous pouvez exécuter des commandes sur un ordinateur ou plusieurs centaines au moyen d'une seule commande Windows PowerShell. Pour communiquer à distance, Windows PowerShell fait appel à différentes technologies, notamment WMI, RPC et WS-Management.

## Communication à distance sans configuration
De nombreuses applets de commande Windows PowerShell possèdent un paramètre ComputerName qui vous permet de collecter des données et de modifier les paramètres d'un ou de plusieurs ordinateurs distants. Elles utilisent diverses technologies de communication et bon nombre d'entre elles fonctionnent sur tous les systèmes d'exploitation Windows pris en charge par Windows PowerShell, et ce sans configuration particulière.

Ces applets de commande sont les suivantes :

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

En général, les applets de commande qui prennent en charge la communication à distance sans configuration particulière possèdent un paramètre ComputerName. En revanche, elles ne possèdent pas de paramètre Session. Pour trouver ces applets de commande dans votre session, tapez :

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Communication à distance Windows PowerShell
La communication à distance Windows PowerShell, qui utilise le protocole WS-Management, permet d’exécuter n’importe quelle commande Windows PowerShell sur un ou plusieurs ordinateurs distants. Vous pouvez ainsi établir des connexions persistantes, démarrer des sessions interactives 1:1 et exécuter des scripts sur plusieurs ordinateurs.

Pour utiliser la communication à distance Windows PowerShell, l'ordinateur distant doit être configuré pour la gestion à distance. Pour obtenir plus d’informations, y compris des instructions, voir [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd).

Après avoir configuré la communication à distance Windows PowerShell, vous avez le choix entre plusieurs stratégies de communication à distance. Le reste de ce document répertorie quelques-unes d'entre elles. Pour plus d’informations, voir [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) et [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42).

### Démarrer une session interactive
Pour démarrer une session interactive avec un seul ordinateur distant, utilisez l’applet de commande [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c). Par exemple, pour démarrer une session interactive avec l'ordinateur distant Server01, tapez :

```
enter-pssession Server01
```

L'invite de commandes affiche alors le nom de l'ordinateur auquel vous êtes connecté. À partir de là, toutes les commandes que vous tapez à l'invite sont exécutées sur l'ordinateur distant et les résultats sont affichés sur l'ordinateur local.

Pour terminer la session interactive, tapez :

```
exit-pssession
```

Pour plus d’informations sur les applets de commande Enter-PSSession et Exit-PSSession, voir [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) et [Exit-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d).

### Exécuter une commande à distance
Pour exécuter une commande sur un ou plusieurs ordinateurs distants, utilisez l’applet de commande [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462). Par exemple, pour exécuter une commande [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8) sur les ordinateurs distants Server02 et Server01, tapez ce qui suit :

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

La sortie est retournée à votre ordinateur.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Exécuter un script
Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre FilePath de l’applet de commande Invoke-Command. Le script doit être accessible à votre ordinateur local ou se trouver sur celui-ci. Les résultats sont retournés à votre ordinateur local.

Par exemple, la commande suivante exécute le script DiskCollect.ps1 sur les ordinateurs distants Server01 et Server02.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Pour plus d’informations sur l’applet de commande Invoke-Command, voir [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Établir une connexion persistante
Pour exécuter une série de commandes associées qui partagent des données, créez une session sur l’ordinateur distant, puis utilisez l’applet de commande Invoke-Command pour exécuter des commandes dans la session créée. Pour créer une session à distance, utilisez l’applet de commande New-PSSession.

Par exemple, la commande suivante crée une session à distance sur l'ordinateur Server01 et une autre session à distance sur l'ordinateur Server02. Elle enregistre les objets de session dans la variable $s.

```
$s = new-pssession -computername Server01, Server02
```

Une fois les sessions établies, vous pouvez exécuter n'importe quelle commande dans celles-ci. Les sessions étant persistantes, vous pouvez collecter des données en une seule commande et les utiliser dans une commande ultérieure.

Par exemple, la commande suivante exécute une commande Get-Hotfix dans les sessions dans la variable $s et enregistre les résultats dans la variable $h. La variable $h est créée dans chacune des sessions dans $s, mais elle n'existe pas dans la session locale.

```
invoke-command -session $s {$h = get-hotfix}
```

Vous pouvez désormais utiliser les données dans la variable $h dans des commandes ultérieures, comme celle qui suit. Les résultats sont affichés sur l'ordinateur local.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### Communication à distance avancée
Dans Windows PowerShell, la gestion à distance n'est qu'un début. Grâce aux applets de commande installées avec Windows PowerShell, vous pouvez établir et configurer des sessions à distance à partir des extrémités locales et distantes, créer des sessions personnalisées et restreintes, permettre aux utilisateurs d'importer à partir d'une session à distance des commandes qui s'exécutent de manière implicite sur la session à distance, configurer la sécurité d'une session à distance, etc.

Pour faciliter la configuration à distance, Windows PowerShell comprend un fournisseur WSMan. Le lecteur WSMAN: créé par le fournisseur vous permet de parcourir une hiérarchie de paramètres de configuration sur l'ordinateur local et les ordinateurs distants. Pour plus d’informations sur le fournisseur WSMan, voir [WSMan Provider](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) et [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed). Ou, dans la console Windows PowerShell, tapez « get-help wsman ».

Pour plus d’informations, voir [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42), [Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)et [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d). Pour obtenir de l’aide sur les erreurs de communication à distance, voir [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317).

## Voir aussi
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[Fournisseur WSMan](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


