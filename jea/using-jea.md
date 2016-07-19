---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: utilisation de JEA
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 88ce340c09efdbb3d81a72fe6113c1187a9152f2
ms.openlocfilehash: 9db7a5a91d25d459313117da34af63016f03c241

---

# Utilisation de JEA
Cette section se concentre sur l’expérience de l’utilisateur final lors de *l’utilisation de JEA*.
Dans la section Conditions préalables, vous avez créé un point de terminaison JEA de démonstration.
Nous allons utiliser cette démonstration pour voir JEA en action.
Dans les sections ultérieures, le guide reviendra en arrière en présentant les actions et fichiers qui ont rendu possible cette expérience de l’utilisateur final.

## Utilisation de JEA en tant que non-administrateur
Pour voir JEA en action, vous devez utiliser la communication à distance de PowerShell comme si vous étiez un utilisateur non-administrateur.
Dans une nouvelle fenêtre PowerShell, exécutez la commande suivante :   

```PowerShell
$NonAdminCred = Get-Credential
```

Entrez les informations d’identification de votre compte de non-administrateur quand vous y êtes invité.
Si vous avez suivi la section [Configurer des utilisateurs et des groupes](creating-a-domain-controller.md#set-up-users-and-groups), celles-ci sont les suivantes :
-   Nom d’utilisateur = « OperatorUser »
-   Mot de passe = « pa$$w0rd »

Ensuite, exécutez la commande suivante pour vous connecter au point de terminaison de démonstration à l’aide des informations d’identification que vous avez fournies :

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Vous avez maintenant démarré une session PowerShell à distance interactive sur l’ordinateur local.
En utilisant le paramètre « Credential », vous vous êtes connecté *comme si vous étiez* OperatorUser (ou le compte que vous avez utilisé).
La modification de l’invite par `[localhost]: PS>` indique que vous travaillez sur une session à distance.  

Exécutez la commande suivante dans votre invite de commandes à distance pour afficher les commandes disponibles :

```PowerShell
Get-Command
```

Comme vous pouvez le voir, il s’agit d’une toute petite partie des commandes disponibles dans une fenêtre PowerShell normale (qui peut souvent en inclure plusieurs milliers).
Plus précisément, seules figurent les huit commandes JEA par défaut (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object) et les deux commandes explicitement incluses dans le fichier de capacité de rôle de maintenance.

Ensuite, intéressons-nous au contexte utilisateur dans lequel fonctionne cette session en appelant la fonction personnalisée incluse dans le fichier de capacité de rôle de maintenance :

```PowerShell
Get-UserInfo
```

La sortie de cette fonction indique le « ConnectedUser » et le « RunAsUser ».
L’utilisateur connecté est le compte connecté à la session à distance (par exemple, votre compte).
Il n’a pas besoin de privilèges d’administrateur.
Le compte « d’identification » est le compte qui effectue réellement les actions privilégiées.
La connexion en tant qu’utilisateur et l’exécution en tant qu’utilisateur privilégié nous permettent d’autoriser des utilisateurs non privilégiés à effectuer des tâches administratives spécifiques sans leur octroyer des droits d’administration.

À titre d’illustration, exécutez la commande suivante :

```PowerShell
Restart-Service -Name Spooler -Verbose
```

Normalement, Restart-Service exige des privilèges d’administrateur pour s’exécuter.
Mais avec le compte virtuel JEA, nous sommes en mesure de l’exécuter à l’aide d’informations d’identification non privilégiées.

Ainsi, JEA vous permet de réaliser vos tâches en utilisant les commandes que vous utilisez déjà.
Mais qu’en est-il des commandes que vous *ne devriez pas* être autorisé à utiliser ?
Essayez d’exécuter une commande différente dans la session JEA, comme `Restart-Computer`, puis remarquez que JEA empêche l’exécution de ces commandes.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Enfin, pour quitter le point de terminaison JEA contraint, exécutez la commande suivante :

```PowerShell
Exit-PSSession
```

Vous vous déconnectez ainsi de la session PowerShell à distance.




<!--HONumber=Jul16_HO1-->


