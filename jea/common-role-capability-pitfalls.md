---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "pièges liés aux capacités de rôle"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### Pièges liés aux capacités de rôle
Vous pouvez tomber dans quelques pièges courants en suivant vous-même ce processus.
Voici un guide rapide qui explique comment identifier et corriger ces problèmes lors de la modification ou la création d’un point de terminaison :

#### Fonctions et applets de commande
Les commandes PowerShell écrites dans PowerShell sont des fonctions PowerShell.
Les commandes PowerShell écrites comme classes .NET spécialisées sont des applets de commande PowerShell.
Vous pouvez déterminer le type de commande en exécutant `Get-Command`.

#### VisibleProviders
Vous devez exposer tous les fournisseurs dont vos commandes ont besoin.
Le plus courant est le fournisseur FileSystem, mais vous aurez peut-être besoin d’en exposer d’autres comme le fournisseur Registry.
Pour une présentation des fournisseurs, consultez le [billet de blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Soyez prudent quand vous exposez des fournisseurs. Souvent, il est préférable de définir votre propre fonction qui utilise les fournisseurs sous-jacents plutôt que d’exposer directement le fournisseur dans une session JEA.
Ainsi, vous pouvez quand même autoriser des utilisateurs à travailler avec des fichiers, des clés de Registre, etc., tout en continuant à déterminer **quels** fichiers et clés de Registre ils peuvent utiliser à l’aide d’une logique de validation personnalisée.




<!--HONumber=Jun16_HO4-->


