---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: Fichier Lisez-moi
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: bd7f637d0889fd0f56c3fa653389819341d2ccff
ms.openlocfilehash: bfee5ef59a4085f0350ff454f634fc0bf5d6d837

---

# Just Enough Administration
Just Enough Administration (JEA) est une technologie de sécurité qui permet une administration déléguée de tout ce qui peut être géré avec PowerShell.
Avec JEA, vous pouvez :
- **Réduire le nombre d’administrateurs sur vos ordinateurs** en exploitant des comptes virtuels qui exécutent des actions privilégiées au nom d’utilisateurs normaux.
- **Limiter les opérations réalisables par les utilisateurs** en spécifiant les applets de commande, fonctions et commandes externes qu’ils peuvent exécuter.
- **Mieux comprendre ce que font vos utilisateurs** avec les transcriptions de « procuration de privilège » qui vous montrent exactement quelles commandes un utilisateur a exécutées pendant une session.

**Pourquoi est-ce important ?**  
Prenez le scénario courant dans lequel vos serveurs DNS sont colocalisés avec vos contrôleurs de domaine Active Directory.
Vos administrateurs DNS ont besoin de disposer de privilèges d’administrateur local pour résoudre les problèmes liés au serveur DNS, mais pour cela, vous devez les intégrer comme membres au groupe de sécurité « Administrateurs de domaine » disposant de privilèges très élevés.
Cette approche permet effectivement aux administrateurs DNS de contrôler tout votre domaine et d’accéder à toutes les ressources situées sur cet ordinateur.

Avec JEA mis en place, vous pouvez configurer un rôle pour vos administrateurs DNS qui leur donne accès à toutes les commandes dont ils ont besoin pour réaliser leurs tâches, mais c’est tout.
Cela signifie que vous pouvez leur octroyer l’accès approprié pour réparer un cache DNS empoisonné sans leur donner par inadvertance des droits sur Active Directory, de parcourir le système de fichiers, ou d’exécuter des scripts potentiellement dangereux.
Mieux encore, quand la session JEA est configurée pour utiliser des comptes virtuels privilégiés à usage unique, vos administrateurs DNS peuvent se connecter au serveur en utilisant des informations d’identification *non privilégiées* et exécuter quand même des commandes privilégiées.

## Disponibilité
JEA est en cours de développement en parallèle avec Windows Server 2016 et est disponible sur les versions antérieures de Windows par le biais de mises à jour Windows Management Framework.
La version actuelle de JEA est disponible sur les plateformes suivantes :

**Windows Server**
- Windows Server 2016 Technical Preview 4 et versions ultérieures
- Windows Server 2012 R2, 2012 et 2008  R2\* avec [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installé

**Client Windows**
- Windows 10 avec la mise à jour de novembre (1511) installée
- Windows 7, 8 et 8.1\* avec [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installé

\* La prise en charge des comptes virtuels pendant les sessions JEA n’est pas disponible sur Windows Server 2008 R2 ou Windows 7 pour le moment.


## Explorer le guide d’expérience
Prêt à apprendre à créer, déployer et utiliser votre propre point de terminaison JEA ?

Ce guide vous permet de commencer rapidement avec un point de terminaison JEA prédéfini pour vous donner une idée de l’expérience utilisateur final, puis de créer un tout nouveau point de terminaison pour mieux illustrer des concepts comme les configurations de session et les capacités de rôle.

1.  [Introduction](introduction.md)   
Explique brièvement pourquoi JEA devrait vous intéresser

2.  [Conditions préalables](prerequisites.md)  
Explique comment configurer votre environnement

3.  [Utilisation de JEA](using-jea.md)  
Commence par vous faire comprendre l’expérience opérateur dans l’utilisation de JEA

4.  [Refaire la démo](remake-the-demo-endpoint.md)  
Créer une configuration de session JEA ex nihilo

5.  [Capacités de rôle](role-capabilities.md)  
Découvrir comment personnaliser les fonctionnalités JEA avec des fichiers de capacités de rôle

6.  [De bout en bout - Active Directory](end-to-end---active-directory.md)  
Créer un point de terminaison pour gérer Active Directory

7.  [Déploiement et maintenance de plusieurs ordinateurs](multi-machine-deployment-and-maintenance.md)  
Découvrir comment le déploiement et la création évoluent avec l’échelle

8.  [Création de rapports sur JEA](reporting-on-jea.md)  
Découvrir comment auditer et créer des rapports sur toutes les actions et l’infrastructure JEA

9.  Annexes
  - [Concepts clés utilisés dans ce guide](key-concepts-used-throughout-this-guide.md)  
  -  [Création d’un contrôleur de domaine](creating-a-domain-controller.md)  
  -  [À propos de l’inscription sur liste rouge](on-blacklisting.md)  
  -  [Éléments à prendre en considération lors de la limitation des commandes](considerations-when-limiting-commands.md)  
  -  [Pièges liés aux capacités de rôle](common-role-capability-pitfalls.md)

## Commencer à créer vos propres points de terminaison JEA
Il est facile de créer un point de terminaison JEA : tout ce dont vous avez besoin, c’est d’un système compatible JEA et d’un éditeur de texte (comme PowerShell ISE).
Conseil utile pour démarrer : créez des fichiers squelettes à l’aide de `New-PSRoleCapabilityFile -Path <path>` et `New-PSSessionCapabilityFile -Path <Path>` sans aucun autre argument.
Ces fichiers squelettes contiennent tous les champs de configuration applicables, ainsi que des commentaires utiles pour expliquer à quoi peut servir chaque champ.

Pour faciliter encore plus la création de points de terminaison JEA, consultez le blog [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) qui fournit une interface graphique utilisateur avec laquelle vous pouvez créer des fichiers de configuration de session et de capacités de rôle.
La génération de capacités de rôle en fonction des journaux PowerShell est même prise en charge pour faciliter votre démarrage avec les commandes que vos utilisateurs exécutent régulièrement pour accomplir leur travail.




<!--HONumber=Jul16_HO4-->


