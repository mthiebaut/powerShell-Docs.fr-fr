---
title:  À propos de Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  979654ae-7994-47f8-be43-d79e7a140143
---

# À propos de Windows PowerShell
Windows PowerShell est conçu pour améliorer l’environnement de script et de ligne de commande en éliminant des problèmes connus de longue date et en ajoutant de nouvelles fonctionnalités.

## Détectabilité
Windows PowerShell facilite la découverte de ses fonctionnalités. Par exemple, pour obtenir la liste des applets de commande qui permettent d’afficher et de modifier les services Windows, tapez :

```
Get-Command *-Service
```

Après avoir découvert l’applet de commande qui effectue une tâche, vous pouvez en apprendre davantage sur l’applet de commande à l’aide de l’applet de commande Get-Help. Par exemple, pour afficher l’aide concernant l’applet de commande Get-Service, tapez ce qui suit :

```
Get-Help Get-Service
```
La plupart des applets de commande émettent des objets qui peuvent être manipulés puis rendus sous forme texte pour l’affichage. Pour bien comprendre la sortie de cette applet de commande, canalisez-la vers l’applet de commande Get-Member. Par exemple, la commande suivante affiche des informations sur les membres de l’objet retourné par l’applet de commande Get-Service.

```
Get-Service | Get-Member
```

## Consistency
La gestion de systèmes pouvant être complexe, disposer d’outils dont l’interface est cohérente facilite le contrôle de la complexité intrinsèque. Malheureusement, ni les outils en ligne de commande, ni les objets COM pouvant contenir des scripts ne sont réputés pour leur cohérence.

La cohérence de Windows PowerShell est l’un de ses principaux atouts. Par exemple, si vous apprenez à utiliser l’applet de commande Sort-Object, vous pouvez utiliser cette connaissance pour trier la sortie de toute applet de commande. Vous n’avez pas à apprendre les différentes routines de tri de chaque applet de commande.

En outre, les développeurs d’applets de commande n’ont pas à concevoir de fonctionnalités de tri pour leur applets de commande. Windows PowerShell leur offre une infrastructure qui intègre les fonctionnalités de base et les force à être cohérents pour de nombreux aspects de l’interface. L’infrastructure élimine certains choix généralement laissés à l’appréciation des développeurs mais, en retour, elle simplifie le développement d’applets de commande robustes et simples d’utilisation.

## Environnements interactifs et de scripts
Windows PowerShell est un environnement combiné interactif et de script qui donne accès à des outils en ligne de commande et à des objets COM, et permet d’exploiter la puissance de la bibliothèque de classes .NET Framework.

Cet environnement améliore l’invite de commandes Windows, pour offrir un environnement interactif avec plusieurs outils en ligne de commande. Il améliore également les scripts Windows Script Host (WSH) qui permettent d’utiliser plusieurs outils en ligne de commande et objets Automation COM, mais ne fournissent pas d’environnement interactif.

En combinant l’accès à toutes ces fonctionnalités, Windows PowerShell étend la capacité de l’utilisateur interactif et du writer de script, et facilite l’administration du système.

## Orientation objet
Même si vous interagissez avec Windows PowerShell en tapant des commandes sous forme de texte, Windows PowerShell est basé sur des objets, pas sur du texte. La sortie d’une commande est un objet. Vous pouvez envoyer l’objet de sortie à une autre commande en tant qu’entrée. Par conséquent, Windows PowerShell fournit une interface familière aux personnes ayant l’expérience d’autres interpréteurs de commandes, tout en introduisant un paradigme de ligne de commande nouveau et puissant. Il étend le concept d’échange de données entre commandes en vous permettant d’envoyer des objets, plutôt que du texte.

## Transition aisée vers les scripts
Windows PowerShell facilite la transition de la saisie de commandes de façon interactive vers la création et l’exécution de scripts. Vous pouvez taper des commandes à l’invite de commandes Windows PowerShell pour découvrir les commandes qui effectuent une tâche. Ensuite, vous pouvez enregistrer ces commandes dans une transcription ou un historique avant de les copier dans un fichier afin de les utiliser en tant que script.



<!--HONumber=May16_HO2-->


