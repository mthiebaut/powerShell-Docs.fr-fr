---
title: Comment utiliser des profils dans Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# Comment utiliser des profils dans Windows PowerShell ISE
Cette rubrique explique comment utiliser des profils dans [!INCLUDE[ise_1](../Token/ise_1_md.md)]. Avant d’effectuer les tâches décrites dans cette section, nous vous recommandons de consulter [about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054) ou, dans le volet Console, de taper « get-help about_profiles », puis d’appuyer sur **Entrée**.

Un profil est un script [!INCLUDE[ise_2](../Token/ise_2_md.md)] qui s’exécute automatiquement lorsque vous démarrez une nouvelle session.  Vous pouvez créer un ou plusieurs profils [!INCLUDE[wps_2](../Token/wps_2_md.md)] pour [!INCLUDE[ise_2](../Token/ise_2_md.md)], et les utiliser pour ajouter la configuration à l’environnement [!INCLUDE[wps_2](../Token/wps_2_md.md)] ou [!INCLUDE[ise_2](../Token/ise_2_md.md)], en le préparant pour votre utilisation, avec les variables, alias, fonctions et préférences de police et de couleur dont vous voulez disposer. Un profil affecte chaque session [!INCLUDE[ise_2](../Token/ise_2_md.md)] que vous démarrez.

> [!NOTE]
> La stratégie d’exécution de [!INCLUDE[wps_2](../Token/wps_2_md.md)] détermine si vous pouvez exécuter des scripts et charger un profil. La stratégie d’exécution par défaut, « Restricted », empêche l’exécution de tous les scripts, y compris des profils. Si vous utilisez la stratégie « Restricted », le profil ne peut pas se charger. Pour plus d’informations sur la stratégie d’exécution, voir [about_Execution_Policies [v4]](assetId:///347708dc-1515-4d74-978b-8334603472e6).

## Sélection d’un profil à utiliser dans Windows PowerShell ISE
[!INCLUDE[ise_2](../Token/ise_2_md.md)] prend en charge les profils pour l’utilisateur actuel et tous les utilisateurs. Il prend également en charge les profils [!INCLUDE[wps_2](../Token/wps_2_md.md)] qui s’appliquent à tous les ordinateurs hôtes.

Le profil que vous utilisez est déterminé par la façon dont vous utilisez [!INCLUDE[wps_2](../Token/wps_2_md.md)] et [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Si vous utilisez uniquement [!INCLUDE[ise_2](../Token/ise_2_md.md)] pour exécuter Windows PowerShell, puis enregistrez tous vos éléments dans un des profils spécifiques d’ISE, tel le profil CurrentUserCurrentHost pour [!INCLUDE[ise_2](../Token/ise_2_md.md)], ou le profil AllUsersCurrentHost pour [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Si vous utilisez plusieurs programmes hôtes pour exécuter Windows PowerShell, enregistrez vos fonctions, alias, variables, et commandes dans un profil qui affecte tous les programmes hôtes, tel le profil CurrentUserAllHosts ou le profil AllUsersAllHosts, et enregistrez les fonctionnalités spécifiques d’ISE, telle la personnalisation de la couleur et de la police, dans le profil CurrentUserCurrentHost pour [!INCLUDE[ise_2](../Token/ise_2_md.md)] profil ou le profil AllUsersCurrentHost pour [!INCLUDE[ise_2](../Token/ise_2_md.md)].

Les éléments suivants sont des profils qui peuvent être créés et utilisés dans [!INCLUDE[ise_2](../Token/ise_2_md.md)]. Chaque profil est enregistré dans son chemin d’accès spécifique.

|Type de profil|Chemin d’accès du profil|
|----------------|----------------|
|« Utilisateur actuel, PowerShell ISE »|$profile.CurrentUserCurrentHost ou $profile|
|« Tous les utilisateurs, PowerShell ISE »|$profile.AllUsersCurrentHost|
|« Utilisateur actuel, Tous les ordinateurs hôtes »|$profile.CurrentUserAllHosts|
|« Tous les utilisateurs, Tous les ordinateurs hôtes »|$profile.AllUsersAllHosts|

## Pour créer un profil
Pour créer un profil « Utilisateur actuel, Windows PowerShell ISE », exécutez la commande suivante :

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

Pour créer un profil « Tous les utilisateurs, Windows PowerShell ISE », exécutez la commande suivante :

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

Pour créer un profil « Utilisateur actuel, Tous les ordinateurs hôtes », exécutez la commande suivante :

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

Pour créer un profil « Tous les utilisateurs, Tous les ordinateurs hôtes », tapez :

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## Pour modifier un profil

1.  Pour ouvrir le profil, exécutez la commande psedit avec la variable qui spécifie le profil que vous souhaitez modifier. Par exemple, pour ouvrir le profil « Utilisateur actuel, Windows PowerShell ISE », tapez : `psEdit $profile`

2.  Ajoutez des éléments à votre profil. Voici quelques exemples pour vous aider à démarrer :

    -   Pour modifier la couleur d’arrière-plan par défaut du volet Console en bleu, dans le type de fichier de profil : `$psISE.Options.OutputPaneBackground = 'blue'`. Pour plus d’informations sur la variable $psISE, voir [Référence de modèle objet Windows PowerShell ISE](assetId:///e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   Pour modifier la taille de police en 20, dans le type de fichier de profil : `$psISE.Options.FontSize =20`

3.  Pour enregistrer votre fichier de profil, dans le menu **Fichier**, cliquez sur **Enregistrer**. Lors de l’ouverture suivante de [!INCLUDE[ise_2](../Token/ise_2_md.md)], vos personnalisations sont appliquées.

## Voir aussi
[about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Utilisation de Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


