# Just Enough Administration
Just Enough Administration (JEA) est la technologie de sécurité qui permet une administration déléguée de tout ce qui peut être géré avec PowerShell.
Avec JEA, vous pouvez :
- **Réduire le nombre d’administrateurs sur vos ordinateurs** en exploitant des comptes virtuels qui exécutent des actions privilégiées au nom d’utilisateurs normaux.
- **Limiter les opérations réalisables par les utilisateurs** en spécifiant les applets de commande, fonctions et commandes externes qu’ils peuvent exécuter.
- **Mieux comprendre ce que font vos utilisateurs** avec les transcriptions de « procuration de privilège » qui vous montrent exactement quelles commandes un utilisateur a exécutées pendant une session.

Pourquoi est-ce important ?
Prenez le scénario courant dans lequel vos serveurs DNS sont colocalisés avec vos contrôleurs de domaine Active Directory.
Vos administrateurs DNS ont besoin de disposer de privilèges d’administrateur local pour résoudre les problèmes liés au serveur DNS, mais pour cela, vous devez les intégrer comme membres au groupe de sécurité « Administrateurs de domaine » disposant de privilèges très élevés.
Ainsi, ils peuvent contrôler tout votre domaine et accéder à toutes les ressources situées sur cet ordinateur.

Avec JEA mis en place, vous pouvez configurer un rôle pour vos administrateurs DNS qui leur donne accès à toutes les commandes dont ils ont besoin pour réaliser leurs tâches, mais c’est tout.
Cela signifie qu’ils peuvent facilement réparer un cache DNS empoisonné sans disposer de droits sur Active Directory, parcourir le système de fichiers ou exécuter des scripts potentiellement dangereux.
Mieux encore, quand la session JEA est configurée pour utiliser des comptes virtuels privilégiés à usage unique, vos administrateurs DNS peuvent se connecter au serveur en utilisant des informations d’identification *non privilégiées* et quand même exécuter des commandes privilégiées.

## Prise en main

### Installation
JEA est en cours de développement en même temps que l’imminente version 2016 de Windows Server et est disponible sur les versions antérieures de Windows par le biais de mises à jour Windows Management Framework.
La version actuelle de JEA est disponible sur les plateformes suivantes :

**Windows Server**
- Windows Server 2016 Technical Preview 4 et versions ultérieures
- Windows Server 2012 R2, 2012 et 2008  R2\* avec [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installé

**Client Windows**
- Windows 10 avec la mise à jour de novembre (1511) installée
- Windows 7, 8 et 8.1\* avec [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installé

\* La prise en charge des comptes virtuels pendant les sessions JEA n’est pas disponible sur Windows Server 2008 R2 ou Windows 7 pour le moment.


### Concepts fondamentaux
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

### Explorer le guide d’expérience
Vous êtes prêt à créer votre premier point de terminaison JEA ?
Consultez le [guide d’expérience JEA](jea-uide.md) pour apprendre à créer, déployer et utiliser votre propre point de terminaison JEA.
Le guide vous assure une prise en main rapide d’un point de terminaison JEA prédéfini pour découvrir l’expérience utilisateur final, puis il vous oriente progressivement dans la création de toutes pièces de ce point de terminaison pour mieux expliquer les configurations de session et les capacités de rôle.

### Commencer à créer vos propres points de terminaison JEA
Il est facile de créer un point de terminaison JEA : tout ce dont vous avez besoin, c’est d’un système compatible JEA et d’un éditeur de texte (comme PowerShell ISE).
Conseil utile pour démarrer : créez des fichiers squelettes à l’aide de `New-PSRoleCapabilityFile -Path <path>` et `New-PSSessionCapabilityFile -Path <Path>` sans aucun autre argument.
Ces fichiers squelettes contiennent tous les champs de configuration applicables, ainsi que des commentaires utiles pour expliquer à quoi peut servir chaque champ.

Pour faciliter encore plus la création de points de terminaison JEA, consultez le blog [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) qui fournit une interface graphique utilisateur avec laquelle vous pouvez créer des fichiers de configuration de session et de capacités de rôle.
La génération de capacités de rôle en fonction des journaux PowerShell est même prise en charge pour faciliter votre démarrage avec les commandes que vos utilisateurs exécutent régulièrement pour accomplir leur travail.


<!--HONumber=Jun16_HO3-->


