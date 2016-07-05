---
title: Obtention d'informations sur les commandes
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: a19601bd785ab91f5d8175acd081113e87a62a57

---

# Obtention d'informations sur les commandes
L’applet de commande Windows PowerShell **Get\-Command** permet d’obtenir toutes les commandes disponibles dans la session active. Quand vous tapez **Get\-Command** dans une invite Windows PowerShell, la sortie est similaire à ce qui suit :

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Cette sortie ressemble beaucoup à la sortie Help de Cmd.exe, à savoir un résumé des commandes internes sous forme de tableau. Dans l’extrait de la sortie de la commande **Get\-Command** ci-dessus, chaque commande est de type Cmdlet (« applet de commande »). Une applet de commande est un type de commande fondamental dans Windows PowerShell qui correspond approximativement aux commandes **dir** et **cd** de Cmd.exe et aux commandes intégrées dans les interpréteurs de commandes UNIX tels que BASH.

Dans la sortie de la commande **Get\-Command**, toutes les définitions se terminent par des points de suspension (...). Ceci indique que PowerShell ne peut pas afficher tout le contenu dans l’espace disponible. Quand Windows PowerShell affiche la sortie, il la met en forme en tant que texte et la réorganise pour faire tenir les données dans la fenêtre. Nous aborderons ce sujet plus loin dans la section sur les formateurs.

L’applet de commande **Get\-Command** dispose d’un paramètre **Syntax** qui permet d’obtenir la syntaxe de chaque applet de commande. Pour obtenir la syntaxe de l’applet de commande Get\-Help, utilisez la commande suivante :

**Get\-Command Get\-Help \-Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### Affichage des types de commandes disponibles
La commande **Get\-Command** ne répertorie pas toutes les commandes disponibles dans Windows PowerShell. La commande **Get\-Command** répertorie uniquement les applets de commande dans la session active. Windows PowerShell prend en charge plusieurs autres types de commandes. Les alias, fonctions et scripts sont aussi des commandes Windows PowerShell, bien qu'ils ne soient pas abordés en détail dans le Guide d'utilisation de Windows PowerShell. Les fichiers externes exécutables ou possédant un gestionnaire de type de fichier inscrit sont également considérés comme des commandes.

Pour obtenir toutes les commandes dans la session, tapez :

```
Get-Command *
```

Étant donné que cette liste recense les fichiers externes dans votre chemin de recherche, elle peut contenir des milliers d'éléments. Il est plus judicieux d'examiner un ensemble réduit de commandes.

Pour obtenir les commandes natives d’autres types, utilisez le paramètre **CommandType** de l’applet de commande **Get\-Command**.

> [!NOTE]
> L’astérisque (\*) est utilisé comme caractère générique dans les arguments de commande Windows PowerShell. Le symbole \* représente un ou plusieurs caractères. Pour rechercher toutes les commandes dont le nom commence par la lettre « a », vous pouvez taper **Get\-Command a\&#42;**. Contrairement aux caractères génériques dans Cmd.exe, un caractère générique peut représenter un point dans Windows PowerShell.

Pour obtenir les alias des commandes, c'est-à-dire les surnoms affectés aux commandes, tapez :

```
Get-Command -CommandType Alias
```

Pour obtenir les fonctions dans la session active, tapez :

```
Get-Command -CommandType Function
```

Pour afficher les scripts dans le chemin de recherche de Windows PowerShell, tapez :

```
Get-Command -CommandType Script
```




<!--HONumber=Jun16_HO4-->


