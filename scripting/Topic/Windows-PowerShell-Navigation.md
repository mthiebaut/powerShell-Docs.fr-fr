---
title: Navigation dans Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846f5233-43be-496a-9ca1-e3e34207cb49
---
# Navigation dans Windows PowerShell
Les dossiers sont une fonctionnalité organisationnelle bien connue de l'interface de l'Explorateur de fichiers, de Cmd.exe et d'outils UNIX tels que BASH. Les dossiers, aussi communément appelés « répertoires », constituent un moyen pratique d'organiser des fichiers et d'autres répertoires. Les systèmes d’exploitation de la famille UNIX élargissent ce concept en traitant tout élément, dans la mesure du possible, en tant que fichier. Ainsi, le matériel spécifique et des connexions réseau apparaissent en tant que fichiers dans des dossiers particuliers. Cette approche ne garantit pas que le contenu est accessible en lecture ou exploitable par des applications particulières, mais elle permet de trouver plus facilement des éléments spécifiques. Les outils qui énumèrent ou parcourent les fichiers et dossiers fonctionnent aussi avec ces périphériques. Vous pouvez également adresser un élément spécifique en utilisant le chemin d'accès au fichier qui le représente.

De la même façon, l'infrastructure Windows PowerShell expose pratiquement tout élément accessible à la navigation, comme un lecteur de disque Microsoft Windows standard ou un système de fichiers UNIX, en tant que lecteur Windows PowerShell. Un lecteur Windows PowerShell ne représente pas nécessairement un lecteur réel (qu'il soit local ou sur le réseau). Ce chapitre traite principalement de la navigation pour les systèmes de fichiers, mais les concepts s'appliquent aux lecteurs Windows PowerShell qui ne sont pas associés à des systèmes de fichiers.



<!--HONumber=Apr16_HO1-->


