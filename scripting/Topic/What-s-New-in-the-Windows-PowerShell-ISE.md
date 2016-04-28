---
title: Nouveauté dans Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
---
# Nouveauté dans Windows PowerShell ISE
Cette rubrique décrit les fonctionnalités nouvelles et mises à jour qui ont été introduites dans les versions de [!INCLUDE[ise_1](../Token/ise_1_md.md)].

## <a name="overview"></a>Description de la fonctionnalité
[!INCLUDE[ise_2](../Token/ise_2_md.md)] est une application hôte qui permet d’écrire, d’exécuter et de tester des scripts et des modules dans un environnement graphique et intuitif. Ses fonctionnalités clés, telles que la coloration de la syntaxe, la saisie semi-automatique via la touche Tab, le débogage visuel, la compatibilité avec Unicode et l’aide contextuelle, fournissent une riche expérience d’écriture de scripts.

Pour une vue d’ensemble de [!INCLUDE[ise_2](../Token/ise_2_md.md)], voir [Vue d’ensemble de l’environnement d’écriture de scripts intégré de Windows PowerShell (Windows PowerShell ISE)](assetId:///3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="versions"></a>Fonctionnalités nouvelles et modifiées dans Windows PowerShell ISE
Le tableau suivant répertorie les fonctionnalités nouvelles et modifiées pour cette version de [!INCLUDE[ise_2](../Token/ise_2_md.md)] dans [!INCLUDE[wps_2](../Token/wps_2_md.md)].

|Fonction/Fonctionnalité|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 4.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense](#BKMK_Intellisense)**|X|X||
|**[Extraits de code](#bkmk_snippets)**|X|X||
|**[Outils complémentaires](#BKMK_AddOnTools)**|X|X||
|**[Gestionnaire de démarrage et enregistrement automatique](#BKMK_RestartMgr)**|X|X||
|**[Volet Console](#BKMK_ConsolePane)**|X|X||
|**[Liste Utilisé(s) récemment](#BKMK_MRU)**|X|X||
|**[Commutateurs de ligne de commande](#BKMK_CommandLine)**|X|X||
|**[Nouvelles fonctionnalités de l’éditeur](#BKMK_NewEditorFeatures)**|X|X||
|**[Nouvelle fenêtre de visionneuse d’aide](#BKMK_NewHelpViewer)**|X|X||
|**[Applet de commande Show-Command](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>IntelliSense
**Ajouté dans ISE 3.0**

IntelliSense est une fonctionnalité d’assistance de saisie semi-automatique qui fait partie de [!INCLUDE[ise_2](../Token/ise_2_md.md)]. Au fur et à mesure de la saisie, IntelliSense affiche des menus interactifs suggérant des applets de commande, des paramètres, des valeurs de paramètre, des fichiers ou des dossiers potentiellement appropriés.

**Quels avantages cette modification procure-t-elle ?**

L’ajout d’IntelliSense facilite la découverte d’applets de commande et de syntaxe lorsque vous utilisez [!INCLUDE[ise_2](../Token/ise_2_md.md)] pour créer des scripts. Vous pouvez également utiliser [!INCLUDE[ise_2](../Token/ise_2_md.md)] pour apprendre le fonctionnement de [!INCLUDE[wps_2](../Token/wps_2_md.md)] lorsque vous créez des scripts.

**En quoi le fonctionnement est-il différent ?**

Lorsque vous tapez des applets de commande dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]3.0 ou version ultérieure, un menu déroulant interactif s’affiche, dans lequel vous pouvez parcourir et sélectionner les commandes appropriées.

### <a name="BKMK_Snippets"></a>Extraits de code
**Ajoutés dans ISE 3.0**

Les *extraits de code* sont de courtes sections de code [!INCLUDE[wps_2](../Token/wps_2_md.md)] que vous pouvez insérer dans les scripts que vous créez dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]. [!INCLUDE[ise_2](../Token/ise_2_md.md)] est fourni avec un ensemble par défaut d’extraits de code. Vous pouvez ajouter des extraits de code en utilisant l’applet de commande **New-Snippet** tout en travaillant dans [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**Quels avantages cette modification procure-t-elle ?**

Les extraits de code vous permettent d’assembler et de créer rapidement des scripts pour automatiser votre environnement.

**En quoi le fonctionnement est-il différent ?**

Pour utiliser des extraits de code dans [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 ou version ultérieure, dans le menu **Modifier**, cliquez sur **Démarrer les extraits** ou appuyez sur **Ctrl-J**.

### <a name="BKMK_AddOnTools"></a>Outils complémentaires
**Ajout dans PowerShell 3.0**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] prend désormais en charge des outils complémentaires qui sont des contrôles Windows Presentation Foundation (WPF) ajoutés à l’aide du modèle d’objet. Les outils complémentaires peuvent être affichés sur la console dans un volet vertical ou horizontal. Plusieurs outils complémentaires dans un volet sont affichés sous la forme d’un contrôle à onglets. Vous pouvez également ajouter ou supprimer des outils complémentaires produits par des éditeurs autres que Microsoft. Pour plus d’informations sur la manière d’importer ou de supprimer des outils complémentaires, voir [Opérations Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).

**Quels avantages cette modification procure-t-elle ?**

Les modules complémentaires vous permettent d’étendre et personnaliser [!INCLUDE[ise_2](../Token/ise_2_md.md)] avec des outils pouvant améliorer votre expérience de création de scripts ou ajouter des fonctionnalités à [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**En quoi le fonctionnement est-il différent ?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 et versions ultérieures sont fournis avec le module complémentaire **Commandes**. Le module complémentaire **Commandes** permet de parcourir les applets de commande et d’accéder à l’aide sur les applets de commande, conjointement avec les volets **Script** et **Console**.

Les modules complémentaires sont accessibles via la commande **Ouvrir le site web des outils additionnels** du menu **Modules complémentaires**.

### <a name="BKMK_RestartMgr"></a>Gestionnaire de démarrage et enregistrement automatique
**Ajout dans PowerShell 3.0**

Désormais, [!INCLUDE[ise_2](../Token/ise_2_md.md)] enregistre automatiquement vos scripts ouverts toutes les deux minutes dans un emplacement distinct.  Si [!INCLUDE[ise_2](../Token/ise_2_md.md)] cesse de fonctionner ou si le système d’exploitation est redémarré, après redémarrage, [!INCLUDE[ise_2](../Token/ise_2_md.md)] récupère les scripts qui étaient ouverts dans la dernière session, même si ceux-ci n’ont pas été enregistrés.

Pour modifier l’intervalle d’enregistrement automatique, exécutez la commande suivante dans le volet Console : **$psise.Options.AutoSaveMinuteInterval**.

**Quels avantages cette modification procure-t-elle ?**

Vous pouvez désormais travailler dans [!INCLUDE[ise_2](../Token/ise_2_md.md)], en sachant que vos scripts ouverts seront automatiquement enregistrés en cas de redémarrage inattendu.

**En quoi le fonctionnement est-il différent ?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)]2.0 n’enregistre pas les scripts automatiquement en cas de redémarrage.

### <a name="BKMK_MRU"></a>Liste Utilisé(s) récemment
**Ajout dans PowerShell 3.0**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] offre désormais une liste des derniers fichiers utilisés. Lorsque vous ouvrez un fichier dans [!INCLUDE[ise_2](../Token/ise_2_md.md)], celui-ci est ajouté à la liste des dernières utilisations dans le menu **Fichier**.

Pour modifier le nombre par défaut de fichiers répertoriés dans la liste des dernières utilisations, exécutez la commande suivante dans le volet Console : **$psise. Options.MruCount**.

**Quels avantages cette modification procure-t-elle ?**

Vous pouvez désormais utiliser la liste des dernières utilisations pour accéder facilement aux fichiers que vous utilisez fréquemment.

**En quoi le fonctionnement est-il différent ?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 d’offre pas de liste des dernières utilisations.

### <a name="BKMK_ConsolePane"></a>Volet Console.
**Ajout dans PowerShell 3.0**

Les volets de commande et de sortie distincts qui étaient disponibles dans la première version de [!INCLUDE[ise_2](../Token/ise_2_md.md)] ont été combinés dans un volet de console unique. Le volet Console est similaire, par sa fonction et son aspect, à une console [!INCLUDE[wps_2](../Token/wps_2_md.md)] classique, mais il inclut les améliorations suivantes, dont la plupart sont décrites dans cette rubrique.

-   Coloration de la syntaxe pour le texte d’entrée (pas le texte de sortie), incluant la syntaxe XML

-   Intellisense

-   Accolades correspondantes

-   Indication des erreurs

-   Prise en charge complète d’Unicode

-   Aide contextuelle accessible via la touche **F1**

-   Commande d’affichage contextuel accessible via la touche **Ctrl+F1**

-   Scripts complexes et prise en charge de la saisie de droite à gauche

-   Prise en charge des polices

-   Zoom

-   Modes de sélection de ligne et de bloc

-   Préservation du contenu saisi dans la ligne de commande lorsque vous appuyez sur la touche **Haut** pour afficher l’historique dans la console

**Quels avantages cette modification procure-t-elle ?**

L’apport de ces modifications au volet Console offre une expérience d’écriture de script plus cohérente avec l’interface de la console.

**En quoi le fonctionnement est-il différent ?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 offre des volets de commande et de sortie distincts.

### <a name="BKMK_CommandLine"></a>Commutateurs de ligne de commande
**Ajout dans PowerShell 3.0**

Si vous démarrez [!INCLUDE[ise_2](../Token/ise_2_md.md)] à partir de la ligne de commande (en tapant **Powershell_ise.exe**), vous pouvez ajouter les nouveaux commutateurs de ligne de commande suivants :

-   *-NoProfile* : démarre [!INCLUDE[ise_2](../Token/ise_2_md.md)] sans exécuter **$profile**

-   *-Help* : affiche une fenêtre d’aide

-   *-mta* : démarre [!INCLUDE[ise_2](../Token/ise_2_md.md)] en mode de cloisonnement multithread. Le mode d’opération par défaut pour [!INCLUDE[ise_2](../Token/ise_2_md.md)] est un mode de cloisonnement monothread, ou *-sta*.

**Quels avantages cette modification procure-t-elle ?**

L’ajout de ces commutateurs de ligne de commande permet de contrôler l’environnement dans lequel [!INCLUDE[ise_2](../Token/ise_2_md.md)] s’exécute.

**En quoi le fonctionnement est-il différent ?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)]2.0 ne reconnaît pas ces commutateurs de ligne de commande.

### <a name="BKMK_NewEditorFeatures"></a>Nouvelles fonctionnalités de l’éditeur
**Ajout dans PowerShell 3.0**

Les autres fonctionnalités d’édition de [!INCLUDE[ise_2](../Token/ise_2_md.md)]sont les suivantes :

-   **Coloration de la syntaxe XML** [!INCLUDE[ise_2](../Token/ise_2_md.md)] colore désormais la syntaxe XML de la même façon que la syntaxe [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   **Correspondance d’accolade** [!INCLUDE[ise_2](../Token/ise_2_md.md)] inclut des fonctions de correspondance et de mise en surbrillance des accolades, utilisables comme suit : par exemple, la commande **Accéder à Match** ou la combinaison de touches **Ctrl+]** permettent de localiser l’accolade fermante, si une accolade ouvrante est sélectionnée.

-   **Mode Plan** Le volet Script prend en charge le mode Plan qui permet de réduire ou de développer des sections de code en cliquant sur les signes plus ou moins dans la marge gauche. Vous pouvez utiliser des accolades ou les balises **#region** et **#endregion** pour marquer le début ou la fin d’une section réductible. Pour développer ou réduire toutes les régions, appuyez sur **Ctrl+M**.

-   **Édition du texte par glisser-déplacer** Désormais, [!INCLUDE[ise_2](../Token/ise_2_md.md)] prend en charge l’édition de texte par glisser-déplacer. Vous pouvez sélectionner un bloc de texte et faire glisser ce texte vers un autre emplacement dans l’éditeur ou la console afin de le déplacer. Si vous maintenez la touche Ctrl enfoncée pendant que vous faites glisser le texte sélectionné, lorsque vous relâchez le bouton de la souris, le texte est copié dans le nouvel emplacement. Dans cette version de [!INCLUDE[ise_2](../Token/ise_2_md.md)], ainsi que dans la version précédente de [!INCLUDE[ise_2](../Token/ise_2_md.md)], lorsque vous glissez-déplacez un fichier vers [!INCLUDE[ise_2](../Token/ise_2_md.md)], [!INCLUDE[ise_2](../Token/ise_2_md.md)] ouvre le fichier.

-   **Affichage des erreurs d’analyse** Les erreurs d’analyse sont indiquées par des soulignements rouges. Lorsque vous pointez sur une erreur indiquée, le texte d’info-bulle affiche le problème détecté dans le code.

-   **Zoom** Le pourcentage de zoom du contenu de la console peut être défini à l’aide du curseur de zoom (dans le coin inférieur droit de la fenêtre de [!INCLUDE[ise_2](../Token/ise_2_md.md)]) ou en tapant la commande **$psise.options.Zoom** dans le volet Console.

-   **Copie et collage de texte enrichi** La copie dans le Presse-papiers dans [!INCLUDE[ise_2](../Token/ise_2_md.md)] préserve les informations de police, de taille et de couleur de la sélection d’origine.

-   **Sélection de bloc** Vous pouvez sélectionner un bloc de texte en maintenant la touche Alt enfoncée tout en sélectionnant du texte dans le volet Script à l’aide de la souris, ou en appuyant sur **Alt+Maj+Flèche**.

**Quels avantages cette modification procure-t-elle ?**

Les fonctionnalités d’édition supplémentaires renforcent la cohérence et la puissance de l’environnement d’édition.

**En quoi le fonctionnement est-il différent ?**

Ces améliorations des fonctionnalités d’édition ne figuraient pas dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]2.0.

### <a name="BKMK_NewHelpViewer"></a>Nouvelle fenêtre de visionneuse d’aide
**Ajout dans PowerShell 3.0**

Si vous appuyez sur **F1** lorsque le curseur est dans une applet de commande ou si une partie d’une applet de commande est en surbrillance, la nouvelle visionneuse d’aide ouvre une aide contextuelle sur l’applet de commande n surbrillance. Pour afficher la rubrique d’aide « À propos de » de [!INCLUDE[wps_2](../Token/wps_2_md.md)], tapez les **operators** dans le volet Console, puis appuyez sur **F1**.

Avant d’utiliser cette fonctionnalité, téléchargez la dernière version des rubriques d’aide de [!INCLUDE[wps_2](../Token/wps_2_md.md)] depuis le site Web Microsoft. La méthode la plus simple pour télécharger les rubriques d’aide consiste à exécuter l’applet de commande **Update-Help** dans le volet Console lors de l’exécution de [!INCLUDE[ise_2](../Token/ise_2_md.md)] en tant qu’administrateur.

Vous pouvez modifier l’emplacement dans lequel la touche **F1** recherche de l’aide. Dans le menu **Outils**/**Options**, sous l’onglet **Paramètres généraux**, sous **Autres paramètres**, vous pouvez définir ou désactivez la case à cocher **Utiliser le contenu de l’aide locale au lieu du contenu en ligne**. Si la case à cocher est activée, le client recherche de l’aide sur l’applet de commande dans l’aide téléchargée figurant dans le dossier modules.  Si la case à cocher est désactivée, le client recherche de l’aide sur l’applet de commande dans la bibliothèque TechNet.

**Quels avantages cette modification procure-t-elle ?**

L’aide contextuelle accessible sans quitter votre applet de commande ou script actifs vous permet de bénéficier d’une expérience d’apprentissage transparente.

**En quoi le fonctionnement est-il différent ?**

Dans les versions précédentes de [!INCLUDE[ise_2](../Token/ise_2_md.md)], l’appui sur la touche F1 ouvrait le fichier d’aide sur l’ordinateur local. Dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]3.0 et versions ultérieures, une fenêtre s’ouvre, affichant l’aide sur l’applet de commande, qui est consultable et configurable. Cette expérience d’aide est une nouveauté pour [!INCLUDE[ise_2](../Token/ise_2_md.md)]3.0, et l’aide actualisable est une nouveauté pour [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0.

### <a name="BKMK_ShowCommand"></a>Applet de commande Show-Command
**Ajout dans PowerShell 3.0**

L’applet de commande **Show-Command** permet de composer ou d’exécuter une applet de commande ou une fonction en remplissant un formulaire graphique. Le formulaire permet aux utilisateurs d’utiliser [!INCLUDE[wps_2](../Token/wps_2_md.md)] dans un environnement graphique. L’applet de commande **Show-Command** permet également aux créateurs de scripts chevronnés de créer une interface graphique utilisateur rapide basée sur [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**Quels avantages cette modification procure-t-elle ?**

En utilisant l’applet de commande **Show-Command** dans vos scripts [!INCLUDE[wps_2](../Token/wps_2_md.md)], vous pouvez fournir à vos utilisateurs un environnement graphique familier. L’applet de commande **Show-Command** peut également faciliter l’apprentissage de [!INCLUDE[wps_2](../Token/wps_2_md.md)] pour des utilisateurs débutants.

**En quoi le fonctionnement est-il différent ?**

L’applet de commande Show-Command est une nouveauté dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]3.0.

## <a name="BKMK_LINKS"></a>Voir aussi
Pour plus d’informations sur l’utilisation de [!INCLUDE[ise_2](../Token/ise_2_md.md)] dans [!INCLUDE[wps_2](../Token/wps_2_md.md)], voir les liens suivants.

-   [Utilisation de l’environnement d’écriture de scripts intégré de Windows PowerShell](assetId:///777ea82b-dd73-4269-b61a-69a17e6ff16f)

-   [ISE sur le wiki TechNet](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Centre de scripts](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=Apr16_HO1-->


