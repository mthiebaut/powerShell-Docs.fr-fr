---
title: Accessibilité dans Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
---
# Accessibilité dans Windows PowerShell ISE
Cette rubrique décrit les fonctionnalités d’accessibilité de [!INCLUDE[ise_1](../Token/ise_1_md.md)] qui peuvent être utiles.

[Comment modifier la taille et l’emplacement des volets Console et Script](#bkmk_1)
[Raccourcis clavier pour l’édition de texte](#bkmk_2)
[Raccourcis clavier pour exécuter les scripts](#bkmk_3)
[Raccourcis clavier pour la personnalisation de l’affichage](#bkmk_4)
[Raccourcis clavier pour le débogage des scripts](#bkmk_5)
[Raccourcis clavier pour les onglets Windows PowerShell](#bkmk_6)
[Raccourcis clavier pour le démarrage et la fermeture](#bkmk_7)
Microsoft s'attache à rendre ses produits et services conviviaux. Les rubriques suivantes fournissent des informations sur les fonctionnalités, les produits et les services qui rendent [!INCLUDE[ise_2](../Token/ise_2_md.md)] plus accessible aux personnes handicapées.

[!INCLUDE[ise_2](../Token/ise_2_md.md)] prend en charge l’affichage à contraste élevé. Pour les malvoyants, les informations de point d’arrêt sont disponibles via les applets de commande pour la gestion des points d’arrêt, telles que [Get-PSBreakpoint](assetId:///0bf48936-00ab-411c-b5e0-9b10a812a3c6) et [Set-PSBreakpoint](assetId:///6afd5d2c-a285-4796-8607-3cbf49471420). Pour plus d’informations, voir « Comment gérer des points d’arrêt » dans [Comment déboguer des scripts dans Windows PowerShell ISE](../Topic/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md#bkmk_1). En plus des fonctionnalités et utilitaires d’accessibilité dans Microsoft Windows, les fonctionnalités suivantes rendent Windows PowerShell ISE plus accessible aux personnes handicapées :

-   Raccourcis clavier

-   Table de coloration de la syntaxe et capacité de modifier plusieurs autres paramètres de couleur à l’aide de l’objet de script [$psISE.Options](assetId:///75e2a76f-f3d1-490b-ad5d-e3829946aabb).

-   Modification de la taille du texte

## <a name="bkmk_1"></a>Comment modifier la taille et l’emplacement des volets Console et Script
Pour modifier la taille et l’emplacement des volets Console et Script, vous pouvez procéder comme suit. Lorsque vous rouvrez [!INCLUDE[ise_2](../Token/ise_2_md.md)], les modifications de taille et d’emplacement sont conservées.

### Pour redimensionner les volets Script et Console

1.  Placez le pointeur sur la ligne de séparation entre les volets Script et Console.

2.  Lorsque le pointeur de la souris prend la forme d’une flèche à deux pointes, faites glisser la bordure pour modifier la taille du volet.

### Pour déplacer les volets Script et Console
Effectuez l'une des opérations suivantes :

-   Pour déplacer le volet Script au-dessus des volets Commande et Sortie, appuyez sur **Ctrl+1** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script en haut**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script en haut**.

-   Pour déplacer le volet Script à droite du volet Console, appuyez sur **Ctrl+2** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script à droite**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script à droite**.

-   Pour agrandir le volet Script, appuyez sur **Ctrl+3** ou, dans la barre d’outils, cliquez sur l’icône **Afficher le volet Script agrandi**, ou encore, dans le menu **Affichage**, cliquez sur **Afficher le volet Script agrandi**.

-   Pour agrandir le volet Console et masquer le volet Script, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Masquer le volet Script**, ou, dans le menu **Affichage**, cliquez pour désactiver l’option de menu **Afficher le volet Script**.

-   Pour afficher le volet Script quand le volet Console est agrandi, sur le bord de droit de la ligne d’onglets, cliquez sur l’icône **Afficher le volet Script**, ou, dans le menu **Affichage**, cliquez pour activer l’option de menu **Afficher le volet Script**.

## <a name="bkmk_2"></a>Raccourcis clavier pour l’édition de texte
Lorsque vous éditez un texte, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourcis clavier|Utiliser dans|
|----------|----------------------|----------|
|**Copier**|Ctrl+C|Volets Script, Commande et Sortie|
|**Couper**|Ctrl+X|Volets Script et Commande|
|**Rechercher dans le script**|Ctrl+F|Volet Script|
|**Rechercher suivant dans le script**|F3|Volet Script|
|**Rechercher précédent dans le script**|Maj+F3|Volet Script|
|**Coller**|Ctrl+V|Volets Script et Commande|
|**Rétablir**|Ctrl+Y|Volets Script et Commande|
|**Remplacer dans le script**|Ctrl+H|Volet Script|
|**Enregistrer**|Ctrl+S|Volet Script|
|**Sélectionner tout**|Ctrl+A|Volets Script, Commande et Sortie|
|**Annuler**|Ctrl+Z|Volets Script et Commande|

## <a name="bkmk_3"></a>Raccourcis clavier pour l’exécution des scripts
Lorsque vous exécutez des scripts dans le volet Script, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Nouveau**|Ctrl+N|
|**Ouvrir**|Ctrl+O|
|**Exécuter**|F5|
|**Exécuter la sélection**|F8|
|**Arrêter l’exécution**|Ctrl+Pause. Vous pouvez utiliser Ctrl+C quand le contexte est sans ambiguïté (quand aucun texte n’est sélectionné).|
|**Tab** (pour accéder au script suivant)|Ctrl+Tab **Remarque :** L’usage de la touche Tab pour accéder au script suivant fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script.|
|**Tab** (pour accéder au script précédent)|Ctrl+Maj+Tab **Remarque :** L’usage de la touche Tab pour accéder au script précédent fonctionne uniquement quand un seul onglet PowerShell est ouvert ou, si plusieurs onglets PowerShell sont ouverts, quand le focus est dans le volet Script.|

## <a name="bkmk_4"></a>Raccourcis clavier pour la personnalisation de l’affichage
Pour personnaliser l’affichage dans [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)], vous pouvez utiliser les raccourcis clavier suivants. Ils sont accessibles à partir de tous les volets de l’application.

|Action|Raccourci clavier|
|----------|---------------------|
|**Accéder au volet Commande**|Ctrl+D|
|**Accéder au volet Sortie**|Ctrl+Maj+O|
|**Accéder au volet Script**|Ctrl+I|
|**Afficher le volet Script**|Ctrl+R|
|**Masquer le volet Script**|Ctrl+R|
||
|**Déplacer le volet Script vers le haut**|Ctrl+1|
|**Déplacer le volet Script vers la droite**|Ctrl+2|
|**Maximiser le volet Script**|Ctrl+3|
|**Zoom avant**|Ctrl+Signe plus|
|**Zoom arrière**|Ctrl+Signe moins|

## <a name="bkmk_5"></a>Raccourcis clavier pour le débogage des scripts
Lors du débogage de scripts, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|Utiliser dans|
|----------|---------------------|----------|
|**Exécuter/Continuer**|F5|Volet Script, lors du débogage d’un script|
|**Pas à pas détaillé**|F11|Volet Script, lors du débogage d’un script|
|**Pas à pas principal**|F10|Volet Script, lors du débogage d’un script|
|**Pas à pas sortant**|Maj+F11|Volet Script, lors du débogage d’un script|
|**Afficher la pile des appels**|Ctrl+Maj+D|Volet Script, lors du débogage d’un script|
|**Afficher la liste des points d’arrêt**|Ctrl+Maj+L|Volet Script, lors du débogage d’un script|
|**Basculer le point d’arrêt**|F9|Volet Script, lors du débogage d’un script|
|**Supprimer tous les points d’arrêt**|Ctrl+Maj+F9|Volet Script, lors du débogage d’un script|
|**Arrêter le débogueur**|Maj+F5|Volet Script, lors du débogage d’un script|

> [!NOTE]
> Lors du débogage de scripts dans Windows PowerShell ISE, vous pouvez également utiliser les raccourcis clavier conçus pour la console Windows PowerShell. Pour utiliser ces raccourcis, vous devez les taper dans le volet Commande, puis appuyer sur Entrée.

|Action|Raccourci clavier|Utiliser dans|
|----------|---------------------|----------|
|**Continuer**|C|Volet Commandes, lors du débogage d’un script|
|**Pas à pas détaillé**|S|Volet Commandes, lors du débogage d’un script|
|**Pas à pas principal**|V|Volet Commandes, lors du débogage d’un script|
|**Pas à pas sortant**|O|Volet Commandes, lors du débogage d’un script|
|**Répéter la dernière commande** (pour un pas à pas détaillé ou un pas à pas principal)|ENTRÉE|Volet Commandes, lors du débogage d’un script|
|**Afficher la pile des appels**|K|Volet Commandes, lors du débogage d’un script|
|**Arrêter le débogage**|Q|Volet Commandes, lors du débogage d’un script|
|**Afficher le script**|L|Volet Commandes, lors du débogage d’un script|
|**Afficher les commandes de débogage de la console**|H ou ?|Volet Commandes, lors du débogage d’un script|

## <a name="bkmk_6"></a>Raccourcis clavier pour les onglets Windows PowerShell
Lorsque vous utilisez les onglets Windows PowerShell, vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Fermer l’onglet PowerShell**|Ctrl+W|
|**Nouvel onglet PowerShell**|Ctrl+T|
|**Onglet PowerShell précédent**|Ctrl+Maj+Tab. Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet PowerShell.|
|**Onglet Windows PowerShell suivant**|Ctrl+Tab. Ce raccourci ne fonctionne que si aucun fichier n’est ouvert sous aucun onglet PowerShell.|

## <a name="bkmk_7"></a>Raccourcis clavier pour le démarrage et la fermeture
Pour démarrer la console Windows PowerShell (PowerShell.exe) ou pour quitter [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)], vous pouvez utiliser les raccourcis clavier suivants.

|Action|Raccourci clavier|
|----------|---------------------|
|**Quitter**|ALT+F4|
|**Démarrer PowerShell.exe** ([!INCLUDE[psconsole](../Token/psconsole_md.md)])|Ctrl+Maj+P|

## Voir aussi
[Utilisation de Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


