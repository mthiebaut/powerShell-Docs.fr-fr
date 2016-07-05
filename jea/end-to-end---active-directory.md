---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: de bout en bout   active directory
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0a262e2c83174db7041d3cf35d97542b1cac4386

---

# De bout en bout - Active Directory
Imaginez que l’étendue de votre programme s’est accrue.
Vous êtes maintenant chargé d’ajouter JEA à des contrôleurs de domaine pour effectuer des actions Active Directory.
Le personnel du support technique va utiliser JEA pour déverrouiller des comptes, réinitialiser des mots de passe et effectuer d’autres actions similaires.

Vous devez exposer un tout nouvel ensemble de commandes vers un autre groupe de personnes.
En plus de cela, vous avez un ensemble de scripts Active Directory existants que vous devez aussi exposer.
Cette section va vous guider tout au long de la création d’une configuration de session et d’une capacité de rôle pour cette tâche.

## Conditions préalables
Pour suivre cette section pas à pas, vous devez utiliser un contrôleur de domaine.
Si vous n’avez pas accès à votre contrôleur de domaine, ne vous inquiétez pas.
Essayez de suivre en travaillant sur un autre scénario ou rôle que vous connaissez bien.
Pour configurer rapidement un nouveau contrôleur de domaine, consultez la section [Création d’un contrôleur de domaine](#creating-a-domain-controller) en annexe.

## Étapes de création d’une capacité de rôle et d’une configuration de session

Créer une capacité de rôle peut sembler décourageant au premier abord, mais cette procédure peut être divisée en plusieurs étapes relativement simples :

1.  Identifier les tâches que vous devez activer
2.  Restreindre ces tâches selon les besoins
3.  Vérifier qu’elles fonctionnent avec JEA
4.  Les placer dans un fichier de capacité de rôle
5.  Inscrire une configuration de session qui expose cette capacité de rôle

## Étape 1 : Identifier ce qui doit être exposé
Avant de créer une capacité de rôle ou une configuration de session, vous devez identifier toutes les actions que les utilisateurs devront effectuer par le biais du point de terminaison JEA, ainsi que la manière de les effectuer par le biais de PowerShell.
Cette identification implique un gros travail de collecte et de recherche de spécifications.
Votre manière de procéder va dépendre de votre organisation et de vos objectifs.
Il est important d’intégrer la collecte et la recherche de spécifications comme un élément essentiel du processus réel.
Il pourra même s’agir de l’étape la plus difficile dans le processus d’adoption de JEA.

### Trouver des ressources
Voici un ensemble de ressources en ligne qui peuvent émerger au cours de votre recherche sur la création d’un point de terminaison de gestion Active Directory :
-   [Vue d’ensemble d’Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [Guide CMD vers PowerShell pour Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### Dresser la liste
Voici l’ensemble des dix actions à partir desquelles vous allez travailler pendant le reste de cette section.
Gardez à l’esprit qu’il s’agit simplement d’un exemple. Les besoins de vos organisations peuvent être différents :

|Action                                                         |Commande PowerShell                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Déverrouillage de compte                                                 |`Unlock-ADAccount`                                             |
|Réinitialisation de mot de passe                                                 |`Set-ADAccountPassword` et `Set-ADUser -ChangePasswordAtLogon`|
|Modifier le titre d’un utilisateur                                          |`Set-ADUser -Title`                                            |  
|Rechercher des comptes AD verrouillés, désactivés, inactifs, etc. |`Search-ADAccount`                                             |
|Ajouter un utilisateur au groupe                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|Supprimer un utilisateur du groupe                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|Activer un compte d’utilisateur                                          |`Enable-ADAccount`                                             |
|Désactiver un compte d’utilisateur                                         |`Disable-ADAccount`                                            |

## Étape 2 : Restreindre les tâches selon les besoins

Maintenant que vous avez votre liste d’actions, vous devez réfléchir aux capacités de chaque commande.
Il existe deux raisons importantes à cela :

1.  Vous pouvez facilement donner aux utilisateurs plus de capacités que vous ne le voulez.
Par exemple, `Set-ADUser` est une commande incroyablement puissante et flexible.
Vous pouvez ne pas souhaiter exposer tout ce dont elle est capable aux utilisateurs du support technique.  

2.  Pire encore, il est possible d’exposer des commandes qui permettent aux utilisateurs d’échapper aux restrictions de JEA.
Le cas échéant, JEA cesse de fonctionner comme une limite de sécurité.
Alors soyez prudent lors de la sélection des commandes.
Par exemple, Invoke-Expression permet aux utilisateurs d’exécuter du code non restreint.
Pour plus d’informations à ce sujet, consultez la section Éléments à prendre en compte lors de la restriction des commandes.

Après avoir examiné chaque commande, vous décidez de restreindre les suivantes :

1.  `Set-ADUser` doit uniquement s’exécuter avec le paramètre « -Title »

2.  `Add-ADGroupMember` et `Remove-ADGroupMember` doit uniquement fonctionner avec certains groupes

### Étape 3 : Vérifier que les tâches fonctionnent avec JEA
En fait, l’utilisation de ces applets de commande risque de ne pas être très simple dans l’environnement JEA restreint.
JEA s’exécute en mode *sans langage* qui, entre autres choses, empêche les utilisateurs d’utiliser des variables.
Pour garantir une expérience sans heurts aux utilisateurs, il est important de vérifier quelques points.

Par exemple, intéressons-nous à `Set-ADAccountPassword`.
Le paramètre « -NewPassword » exige une chaîne sécurisée.
Souvent, les utilisateurs créent une chaîne sécurisée et la transmettent en tant que variable (comme indiqué ci-dessous) :

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

Toutefois, le mode sans langage empêche l’utilisation de variables.
Vous pouvez contourner cette restriction de deux manières :

1.  Vous pouvez exiger que les utilisateurs exécutent la commande sans affecter de variables.
Cette option est facile à configurer, mais peut s’avérer contraignante pour les opérateurs qui utilisent le point de terminaison.
Qui voudrait taper cette commande à chaque réinitialisation de mot de passe ?
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  Vous pouvez encapsuler la complexité dans un script ou une fonction que vous exposez aux utilisateurs finaux.
Les scripts et fonctions que vous exposez s’exécutent dans un contexte non restreint ; vous pouvez écrire des fonctions qui utilisent des variables et appellent d’autres commandes sans rencontrer aucun problème.
Cette approche simplifie l’expérience de l’utilisateur final, empêche les erreurs, réduit les connaissances PowerShell requises et réduit l’exposition involontaire d’un excès de fonctionnalités.
Le seul inconvénient réside dans le coût de création et de maintenance de la fonction.

### Aparté : Ajout d’une fonction à votre module
En choisissant l’approche n° 2, vous allez écrire une fonction PowerShell appelée `Reset-ContosoUserPassword`.
Cette fonction va faire tout ce qui doit se produire lorsque vous réinitialisez le mot de passe d’un utilisateur.
Dans votre organisation, cette opération peut impliquer des tâches compliquées.
Comme il s’agit tout simplement d’un exemple, votre commande va juste réinitialiser le mot de passe et exiger que l’utilisateur change de mot de passe lors de la connexion.
Nous la placerons dans le module Contoso_AD_Module que vous avez créé au cours de la dernière section.

1. Dans PowerShell ISE, ouvrez « Contoso_AD_Module.psm1 ».
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. Appuyez sur Ctrl+J pour ouvrir le menu des extraits de code.

3. Faites défiler vers le bas jusqu'à ce que vous trouviez « fonction » et appuyez sur Entrée.
Un squelette super basique de fonction apparaît.

4. Renommez la fonction « Reset-ContosoUserPassword ».  

5. Renommez un des paramètres « Identité » et supprimez le deuxième.

6. Copiez ce qui suit dans le corps de la fonction.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Enregistrez le fichier.
Vous devez obtenir quelque chose qui ressemble à ceci :
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
À présent, vos utilisateurs peuvent simplement appeler `Reset-ContosoUserPassword` sans avoir à mémoriser la syntaxe pour créer une chaîne sécurisée intégrée.

## Étape 4 : Modifier le fichier de capacité de rôle
Dans la section [Création de capacité de rôle](#role-capability-creation), vous avez créé un fichier de capacité de rôle vierge.
Dans cette section, vous allez renseigner les valeurs dans ce fichier.

Commencez par ouvrir le fichier de capacité de rôle dans ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
Mettez à jour le fichier avec les modifications suivantes :
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

Il est bon de noter quelques points sur ce qui précède :
1.  PowerShell va tenter de charger automatiquement les modules nécessaires à votre capacité de rôle.
Vous devrez peut-être répertorier explicitement les noms de module dans le champ « ModulesToImport » si vous rencontrez des problèmes avec un module qui ne se charge pas automatiquement.

2.  Si vous ne savez pas si une commande est une applet de commande ou une fonction, exécutez `Get-Command` et examinez « CommandType ».

3.  ValidatePattern vous permet d’utiliser une expression régulière pour restreindre des arguments de paramètre s’il n’est pas facile de définir un ensemble de valeurs autorisées.
Vous ne pouvez pas définir à la fois ValidatePattern et ValidateSet pour un seul paramètre.

## Étape 5 : Inscrire une nouvelle configuration de session
Ensuite, vous allez créer un fichier de configuration de session qui va exposer votre capacité de rôle aux membres du groupe AD « JEA_NonAdmin_HelpDesk ».

Commencez par créer et ouvrir un nouveau fichier de configuration de session vierge dans PowerShell ISE.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Modifiez les champs suivants dans le fichier PSSC.
Si vous travaillez dans votre propre environnement, vous devez remplacer « CONTOSO\JEA_NonAdmins_Helpdesk » par votre propre utilisateur ou groupe non-administrateur.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
Enregistrer et inscrire la configuration de session
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## Faites le test !
Obtenez vos informations d’identification d’utilisateur non-administrateur :
```PowerShell
$HelpDeskCred = Get-Credential
```
Si vous avez suivi la section [Configurer des utilisateurs et des groupes](creating-a-domain-controller.md#set-up-users-and-groups), celles-ci sont les suivantes :
-   Nom d’utilisateur = « HelpDeskUser »
-   Mot de passe = « pa$$w0rd »

Accédez à distance au point de terminaison du support technique AD à l’aide des informations d’identification de non-administrateur :
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
Utilisez Set-ADUser pour réinitialiser le titre d’un utilisateur.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
Vérifiez que le titre a changé.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
À présent, utilisez Add-ADGroupMember pour ajouter un utilisateur à TestGroup.
Remarque : Vérifiez que vous avez créé TestGroup au préalable.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
Quittez la session :
```PowerShell
Exit-PSSession
```
## Concepts clés
**Mode NoLanguage** : quand PowerShell est en mode « NoLanguage », les utilisateurs peuvent uniquement exécuter des commandes ; ils ne peuvent pas utiliser des éléments de langage.
Pour plus d’informations, exécuter `Get-Help about_Language_Modes`.

**Fonctions PowerShell** : les fonctions PowerShell sont des morceaux de code PowerShell que vous pouvez appeler par leur nom.
Pour plus d’informations, exécuter `Get-Help about_Functions`.

**ValidateSet/ValidatePattern** : lors de l’exposition d’une commande, vous pouvez restreindre les arguments valides de paramètres spécifiques.
ValidateSet correspond à la liste spécifique des commandes valides.
ValidatePattern est une expression régulière à laquelle doivent correspondre les arguments de ce paramètre.




<!--HONumber=Jun16_HO4-->


