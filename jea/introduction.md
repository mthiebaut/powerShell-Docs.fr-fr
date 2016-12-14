---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: introduction
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="introduction"></a>Introduction

##  <a name="motivation"></a>**Motivation**  
Quand vous accordez à une personne un accès privilégié à vos systèmes, vous étendez votre confiance à cette personne.
Ce n’est pas sans risque, car les administrateurs sont une surface d’attaque.
Les attaques internes et les informations d’identification volées sont à la fois réelles et courantes.

##  <a name="not-a-new-problem"></a>**Le problème n’est pas nouveau**  
Vous connaissez probablement déjà le principe du privilège minimum et vous utilisez peut-être une forme de contrôle d’accès en fonction du rôle (RBAC) avec les applications qui le proposent.
Toutefois, l’efficacité et la facilité de gestion de ces solutions sont souvent limitées par leur large étendue et leur imprécision.
De plus, il existe des lacunes dans la couverture RBAC.
Par exemple, dans Windows, un accès privilégié correspond largement à un commutateur binaire, ce qui vous oblige à accorder des autorisations inutiles lors de l’ajout d’utilisateurs au groupe Administrateurs.

##  <a name="just-enough-administration-jea"></a>**Just Enough Administration (JEA)** 
Fournit une plateforme de contrôle d’accès en fonction du rôle (RBAC) par le biais de la communication à distance PowerShell.
*Elle permet à des utilisateurs spécifiques d’effectuer des tâches administratives spécifiques sur des serveurs sans leur octroyer de droits d’administrateur.*
Cela vous permet de combler les lacunes de vos solutions RBAC existantes et de simplifier la gestion de ces paramètres.

