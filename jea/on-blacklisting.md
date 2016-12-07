---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "à propos de l’inscription sur liste rouge"
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="on-blacklisting"></a>À propos de l’inscription sur liste rouge
Maintenant que vous avez manipulé JEA, vous vous demandez peut-être s’il est possible d’inscrire des commandes sur liste rouge.
Cette demande est compréhensible, mais elle n’est pas actuellement prévue pour JEA pour les raisons suivantes :

1.  Nous avons conçu JEA pour limiter les opérateurs aux actions qu’ils ont besoin d’effectuer.
Une liste rouge fait le contraire.

2.  Les auteurs des commandes PowerShell n’ont pas conçu des commandes PowerShell avec JEA à l’esprit.
Dans une nouvelle installation de Windows Server 2016, environ 1 520 commandes sont disponibles tout de suite.
Les modèles de menace définis pour ces commandes ne comprenaient pas la possibilité qu’un utilisateur les exécutent en tant que compte plus privilégié.
Par exemple, certaines commandes permettent l’injection de code par conception (par exemple, Add-Type et Invoke-Command dans le module PowerShell principal).
JEA peut vous avertir quand vous exposez les commandes spécifiques que nous connaissons, mais nous n’avons pas réévalué toutes les autres commandes dans Windows au regard du nouveau modèle de menace.
Vous devez comprendre les capacités des commandes que vous exposez par le biais de JEA.  

3.  De plus, même si JEA a bloqué toutes les commandes comportant des vulnérabilités d’injection de code, il n’existe aucune garantie qu’un utilisateur malveillant ne serait pas capable d’exécuter une action inscrite sur liste rouge avec une autre commande connexe.
Sauf si vous comprenez toutes les commandes que vous exposez, il vous est impossible de garantir qu’une certaine action n’est pas possible.
Il vous incombe de comprendre les commandes que vous exposez, qu’elles utilisent une liste verte ou une liste rouge.
Le nombre de commandes qu’exposerait une liste rouge serait difficile à gérer, c’est pourquoi JEA est plutôt implémenté avec des listes vertes.

