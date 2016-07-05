---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "concepts clés utilisés dans ce guide"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 178fea44987b0c457b8e5d23fbe851ee12f03b31

---

# Concepts clés utilisés dans ce guide
**Qu’est-ce que JEA exactement ?**

JEA est une extension des [points de terminaison contraints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) PowerShell qui permet d’ajouter des définitions de rôle, des comptes virtuels et plusieurs autres améliorations pour faciliter encore plus le verrouillage de vos points de terminaison de gestion.
Un point de terminaison JEA se compose d’un fichier de configuration de session PowerShell et d’un ou plusieurs fichiers de capacités de rôle.

**Que sont les fichiers de configuration de session et de capacités de rôle ?**

Les fichiers de configuration de session PowerShell (.pssc) définissent *qui* peut se connecter à un point de terminaison PowerShell et *comment* il est configuré.
C’est là que vous mappez des utilisateurs et groupes de sécurité sur des rôles de gestion spécifiques et que vous configurez des paramètres globaux comme les comptes virtuels et les stratégies de transcription.
Les fichiers de configuration de session sont propres à chaque ordinateur, ce qui vous permet de contrôler l’accès ordinateur par ordinateur si vous le souhaitez.

Les fichiers de capacités de rôle PowerShell (.psrc) définissent *ce que* les utilisateurs appartenant à un rôle sont en mesure de faire sur le système.
Ils vous permettent de restreindre les applets de commande, fonctions, fournisseurs et programmes externes qu’utilisateur peut utiliser pendant sa session JEA.
Les fichiers de capacités de rôle sont souvent génériques pour le rôle servi (administrateur DNS, support technique de niveau 1, audit d’inventaire en lecture seule, etc.) et ils appartiennent à des modules PowerShell, ce qui facilite leur partage au sein de votre environnement et avec d’autres personnes.

**Comment les comptes virtuels sont-ils exploités par JEA ?**

Dans le fichier de configuration de session PowerShell, vous pouvez configurer des sessions JEA pour utiliser des comptes « d’identification » virtuels.
Les comptes virtuels sont des comptes privilégiés à usage unique préparés pour l’utilisateur spécifique qui tente d’établir une connexion au cours de cette session spécifique dans le contexte d’exécution des commandes de l’utilisateur.
Les comptes virtuels appartiennent au groupe de sécurité « Administrateurs » local par défaut, mais ils peuvent éventuellement être configurés pour n'appartenir qu’aux groupes de sécurité que vous spécifiez.

**Communication à distance de PowerShell** : la communication à distance de PowerShell vous permet d’exécuter des commandes PowerShell sur des ordinateurs à distance.
Vous pouvez travailler sur un ou plusieurs ordinateurs et utiliser des connexions temporaires ou permanentes.
Dans cette démonstration, vous avez accédé à distance à votre ordinateur local avec une session interactive.
JEA restreint les fonctionnalités disponibles par le biais de la communication à distance de PowerShell.
Pour plus d'informations sur la communication à distance de PowerShell, exécutez `Get-Help about_Remote`.

**Utilisateur « d’identification » ** : quand vous utilisez JEA, un non-administrateur « s’exécute en tant que » « compte virtuel » privilégié.
Le compte virtuel dure uniquement le temps de la session à distance.
Autrement dit, il est créé lorsqu’un utilisateur se connecte au point de terminaison, puis détruit lorsque l’utilisateur met fin à la session.
Par défaut, le compte virtuel est membre du groupe Administrateurs local.
Sur un contrôleur de domaine, il est membre du groupe Admins du domaine.
Les comptes virtuels sont locaux pour l’ordinateur sur lequel ils sont créés et n’ont pas d’autorisations en dehors de cet ordinateur.
Cela signifie qu’ils ne sont pas inscrits dans Active Directory (aucun RID n’est attribué).
En outre, si un script/une commande autorisé(e) tente d’accéder à des ressources en dehors de l’ordinateur local, il ou elle accède à ces ressources sous l’identité de l’ordinateur, et non pas l’identité du compte virtuel.

**« Utilisateur connecté »** : utilisateur non-administrateur qui se connecte au point de terminaison JEA et auquel des rôles sont attribués.
Toutes les commandes que cet utilisateur exécute sont exécutées dans le contexte de l’utilisateur d’identification ou compte virtuel.




<!--HONumber=Jun16_HO4-->


