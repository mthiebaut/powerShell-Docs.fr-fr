---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: de bout en bout   active directory
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="c3dd2-103">De bout en bout - Active Directory</span><span class="sxs-lookup"><span data-stu-id="c3dd2-103">End to End - Active Directory</span></span>
<span data-ttu-id="c3dd2-104">Imaginez que l’étendue de votre programme s’est accrue.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="c3dd2-105">Vous êtes maintenant chargé d’ajouter JEA à des contrôleurs de domaine pour effectuer des actions Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="c3dd2-106">Le personnel du support technique va utiliser JEA pour déverrouiller des comptes, réinitialiser des mots de passe et effectuer d’autres actions similaires.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="c3dd2-107">Vous devez exposer un tout nouvel ensemble de commandes vers un autre groupe de personnes.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="c3dd2-108">En plus de cela, vous avez un ensemble de scripts Active Directory existants que vous devez aussi exposer.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="c3dd2-109">Cette section va vous guider tout au long de la création d’une configuration de session et d’une capacité de rôle pour cette tâche.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3dd2-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c3dd2-110">Prerequisites</span></span>
<span data-ttu-id="c3dd2-111">Pour suivre cette section pas à pas, vous devez utiliser un contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="c3dd2-112">Si vous n’avez pas accès à votre contrôleur de domaine, ne vous inquiétez pas.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="c3dd2-113">Essayez de suivre en travaillant sur un autre scénario ou rôle que vous connaissez bien.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="c3dd2-114">Pour configurer rapidement un nouveau contrôleur de domaine, consultez l’annexe [Création d’un contrôleur de domaine](.\creating-a-domain-controller.md).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="c3dd2-115">Étapes de création d’une capacité de rôle et d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="c3dd2-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="c3dd2-116">Créer une capacité de rôle peut sembler décourageant au premier abord, mais cette procédure peut être divisée en plusieurs étapes relativement simples :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="c3dd2-117">Identifier les tâches que vous devez activer</span><span class="sxs-lookup"><span data-stu-id="c3dd2-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="c3dd2-118">Restreindre ces tâches selon les besoins</span><span class="sxs-lookup"><span data-stu-id="c3dd2-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="c3dd2-119">Vérifier qu’elles fonctionnent avec JEA</span><span class="sxs-lookup"><span data-stu-id="c3dd2-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="c3dd2-120">Les placer dans un fichier de capacité de rôle</span><span class="sxs-lookup"><span data-stu-id="c3dd2-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="c3dd2-121">Inscrire une configuration de session qui expose cette capacité de rôle</span><span class="sxs-lookup"><span data-stu-id="c3dd2-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="c3dd2-122">Étape 1 : Identifier ce qui doit être exposé</span><span class="sxs-lookup"><span data-stu-id="c3dd2-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="c3dd2-123">Avant de créer une capacité de rôle ou une configuration de session, vous devez identifier toutes les actions que les utilisateurs devront effectuer par le biais du point de terminaison JEA, ainsi que la manière de les effectuer par le biais de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="c3dd2-124">Cette identification implique un gros travail de collecte et de recherche de spécifications.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="c3dd2-125">Votre manière de procéder va dépendre de votre organisation et de vos objectifs.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="c3dd2-126">Il est important d’intégrer la collecte et la recherche de spécifications comme un élément essentiel du processus réel.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="c3dd2-127">Il pourra même s’agir de l’étape la plus difficile dans le processus d’adoption de JEA.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="c3dd2-128">Trouver des ressources</span><span class="sxs-lookup"><span data-stu-id="c3dd2-128">Find Resources</span></span>
<span data-ttu-id="c3dd2-129">Voici un ensemble de ressources en ligne qui peuvent émerger au cours de votre recherche sur la création d’un point de terminaison de gestion Active Directory :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="c3dd2-130">Vue d’ensemble d’Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3dd2-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="c3dd2-131">Guide CMD vers PowerShell pour Active Directory</span><span class="sxs-lookup"><span data-stu-id="c3dd2-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="c3dd2-132">Dresser la liste</span><span class="sxs-lookup"><span data-stu-id="c3dd2-132">Make a List</span></span>
<span data-ttu-id="c3dd2-133">Voici l’ensemble des dix actions à partir desquelles vous allez travailler pendant le reste de cette section.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="c3dd2-134">Gardez à l’esprit qu’il s’agit simplement d’un exemple. Les besoins de vos organisations peuvent être différents :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="c3dd2-135">Action</span><span class="sxs-lookup"><span data-stu-id="c3dd2-135">Action</span></span>                                                         |<span data-ttu-id="c3dd2-136">Commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3dd2-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="c3dd2-137">Déverrouillage de compte</span><span class="sxs-lookup"><span data-stu-id="c3dd2-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="c3dd2-138">Réinitialisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="c3dd2-138">Password Reset</span></span>                                                 |<span data-ttu-id="c3dd2-139">`Set-ADAccountPassword` et `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="c3dd2-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="c3dd2-140">Modifier le titre d’un utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3dd2-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="c3dd2-141">Rechercher des comptes AD verrouillés, désactivés, inactifs, etc.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="c3dd2-142">Ajouter un utilisateur au groupe</span><span class="sxs-lookup"><span data-stu-id="c3dd2-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="c3dd2-143">Supprimer un utilisateur du groupe</span><span class="sxs-lookup"><span data-stu-id="c3dd2-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="c3dd2-144">Activer un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3dd2-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="c3dd2-145">Désactiver un compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c3dd2-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="c3dd2-146">Étape 2 : Restreindre les tâches selon les besoins</span><span class="sxs-lookup"><span data-stu-id="c3dd2-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="c3dd2-147">Maintenant que vous avez votre liste d’actions, vous devez réfléchir aux capacités de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="c3dd2-148">Il existe deux raisons importantes à cela :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="c3dd2-149">Vous pouvez facilement donner aux utilisateurs plus de capacités que vous ne le voulez.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="c3dd2-150">Par exemple, `Set-ADUser` est une commande incroyablement puissante et flexible.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="c3dd2-151">Vous pouvez ne pas souhaiter exposer tout ce dont elle est capable aux utilisateurs du support technique.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="c3dd2-152">Pire encore, il est possible d’exposer des commandes qui permettent aux utilisateurs d’échapper aux restrictions de JEA.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="c3dd2-153">Le cas échéant, JEA cesse de fonctionner comme une limite de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="c3dd2-154">Alors soyez prudent lors de la sélection des commandes.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="c3dd2-155">Par exemple, Invoke-Expression permet aux utilisateurs d’exécuter du code non restreint.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="c3dd2-156">Pour plus d’informations à ce sujet, consultez la section Éléments à prendre en compte lors de la restriction des commandes.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="c3dd2-157">Après avoir examiné chaque commande, vous décidez de restreindre les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="c3dd2-158">`Set-ADUser` doit uniquement pouvoir s’exécuter avec le paramètre -Title</span><span class="sxs-lookup"><span data-stu-id="c3dd2-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="c3dd2-159">`Add-ADGroupMember` et `Remove-ADGroupMember` doivent uniquement fonctionner avec certains groupes</span><span class="sxs-lookup"><span data-stu-id="c3dd2-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="c3dd2-160">Étape 3 : Vérifier que les tâches fonctionnent avec JEA</span><span class="sxs-lookup"><span data-stu-id="c3dd2-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="c3dd2-161">En fait, l’utilisation de ces applets de commande risque de ne pas être très simple dans l’environnement JEA restreint.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="c3dd2-162">JEA s’exécute en mode *sans langage* qui, entre autres choses, empêche les utilisateurs d’utiliser des variables.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="c3dd2-163">Pour garantir une expérience sans heurts aux utilisateurs, il est important de vérifier quelques points.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="c3dd2-164">Par exemple, intéressons-nous à `Set-ADAccountPassword`.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="c3dd2-165">Le paramètre -NewPassword exige une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="c3dd2-166">Souvent, les utilisateurs créent une chaîne sécurisée et la transmettent en tant que variable (comme indiqué ci-dessous) :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="c3dd2-167">Toutefois, le mode *sans langage* empêche l’utilisation de variables.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="c3dd2-168">Vous pouvez contourner cette restriction de deux manières :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="c3dd2-169">Vous pouvez exiger que les utilisateurs exécutent la commande sans affecter de variables.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="c3dd2-170">Cette option est facile à configurer, mais peut s’avérer contraignante pour les opérateurs qui utilisent le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="c3dd2-171">Qui voudrait taper cette commande à chaque réinitialisation de mot de passe ?</span><span class="sxs-lookup"><span data-stu-id="c3dd2-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="c3dd2-172">Vous pouvez encapsuler la complexité dans un script ou une fonction que vous exposez aux utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="c3dd2-173">Les scripts et fonctions que vous exposez s’exécutent dans un contexte non restreint ; vous pouvez écrire des fonctions qui utilisent des variables et appellent d’autres commandes sans rencontrer aucun problème.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="c3dd2-174">Cette approche simplifie l’expérience de l’utilisateur final, empêche les erreurs, réduit les connaissances PowerShell requises et réduit l’exposition involontaire d’un excès de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="c3dd2-175">Le seul inconvénient réside dans le coût de création et de maintenance de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="c3dd2-176">Aparté : Ajout d’une fonction à votre module</span><span class="sxs-lookup"><span data-stu-id="c3dd2-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="c3dd2-177">En choisissant l’approche n° 2, vous allez écrire une fonction PowerShell appelée `Reset-ContosoUserPassword`.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="c3dd2-178">Cette fonction va faire tout ce qui doit se produire lorsque vous réinitialisez le mot de passe d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="c3dd2-179">Dans votre organisation, cette opération peut impliquer des tâches compliquées.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="c3dd2-180">Comme il s’agit tout simplement d’un exemple, votre commande va juste réinitialiser le mot de passe et exiger que l’utilisateur change de mot de passe lors de la connexion.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="c3dd2-181">Nous la placerons dans le module Contoso_AD_Module que vous avez créé au cours de la dernière section.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="c3dd2-182">Dans PowerShell ISE, ouvrez « Contoso_AD_Module.psm1 ».</span><span class="sxs-lookup"><span data-stu-id="c3dd2-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="c3dd2-183">Appuyez sur Ctrl+J pour ouvrir le menu des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="c3dd2-184">Faites défiler vers le bas jusqu'à ce que vous trouviez « fonction » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="c3dd2-185">Un squelette super basique de fonction apparaît.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="c3dd2-186">Renommez la fonction « Reset-ContosoUserPassword ».</span><span class="sxs-lookup"><span data-stu-id="c3dd2-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="c3dd2-187">Renommez un des paramètres « Identité » et supprimez le deuxième.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="c3dd2-188">Copiez ce qui suit dans le corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="c3dd2-189">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-189">Save the file.</span></span>
<span data-ttu-id="c3dd2-190">Vous devez obtenir quelque chose qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-190">You should end up with something that looks like this:</span></span>
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
<span data-ttu-id="c3dd2-191">À présent, vos utilisateurs peuvent simplement appeler `Reset-ContosoUserPassword` sans avoir à mémoriser la syntaxe pour créer une chaîne sécurisée intégrée.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="c3dd2-192">Étape 4 : Modifier le fichier de capacité de rôle</span><span class="sxs-lookup"><span data-stu-id="c3dd2-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="c3dd2-193">Dans la section [Création de fonctionnalité de rôle](./role-capabilities.md#role-capability-creation), vous avez créé un fichier de fonctionnalité de rôle vide.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="c3dd2-194">Dans cette section, vous allez renseigner les valeurs dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="c3dd2-195">Commencez par ouvrir le fichier de capacité de rôle dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="c3dd2-196">Mettez à jour le fichier avec les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-196">Update the file with the following changes:</span></span>
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

<span data-ttu-id="c3dd2-197">Il est bon de noter quelques points sur ce qui précède :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="c3dd2-198">PowerShell va tenter de charger automatiquement les modules nécessaires à votre capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="c3dd2-199">Vous devrez peut-être répertorier explicitement les noms de module dans le champ « ModulesToImport » si vous rencontrez des problèmes avec un module qui ne se charge pas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="c3dd2-200">Si vous ne savez pas si une commande est une applet de commande ou une fonction, exécutez `Get-Command` et examinez la propriété « CommandType ».</span><span class="sxs-lookup"><span data-stu-id="c3dd2-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="c3dd2-201">ValidatePattern vous permet d’utiliser une expression régulière pour restreindre des arguments de paramètre s’il n’est pas facile de définir un ensemble de valeurs autorisées.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="c3dd2-202">Vous ne pouvez pas définir à la fois ValidatePattern et ValidateSet pour un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="c3dd2-203">Étape 5 : Inscrire une nouvelle configuration de session</span><span class="sxs-lookup"><span data-stu-id="c3dd2-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="c3dd2-204">Ensuite, vous allez créer un fichier de configuration de session qui va exposer votre capacité de rôle aux membres du groupe AD « JEA_NonAdmin_HelpDesk ».</span><span class="sxs-lookup"><span data-stu-id="c3dd2-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="c3dd2-205">Commencez par créer et ouvrir un nouveau fichier de configuration de session vierge dans PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="c3dd2-206">Modifiez les champs suivants dans le fichier PSSC.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="c3dd2-207">Si vous travaillez dans votre propre environnement, vous devez remplacer « CONTOSO\JEA_NonAdmins_Helpdesk » par votre propre utilisateur ou groupe non-administrateur.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="c3dd2-208">Enregistrer et inscrire la configuration de session</span><span class="sxs-lookup"><span data-stu-id="c3dd2-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="c3dd2-209">Faites le test !</span><span class="sxs-lookup"><span data-stu-id="c3dd2-209">Test It Out!</span></span>
<span data-ttu-id="c3dd2-210">Obtenez vos informations d’identification d’utilisateur non-administrateur :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="c3dd2-211">Si vous avez suivi la section [Configurer des utilisateurs et des groupes](creating-a-domain-controller.md#set-up-users-and-groups), celles-ci sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="c3dd2-212">Nom d’utilisateur = « HelpDeskUser »</span><span class="sxs-lookup"><span data-stu-id="c3dd2-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="c3dd2-213">Mot de passe = « pa$$w0rd »</span><span class="sxs-lookup"><span data-stu-id="c3dd2-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="c3dd2-214">Accédez à distance au point de terminaison du support technique AD à l’aide des informations d’identification de non-administrateur :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="c3dd2-215">Utilisez Set-ADUser pour réinitialiser le titre d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="c3dd2-216">Vérifiez que le titre a changé.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="c3dd2-217">À présent, utilisez Add-ADGroupMember pour ajouter un utilisateur à TestGroup.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="c3dd2-218">Remarque : Vérifiez que vous avez créé TestGroup au préalable.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="c3dd2-219">Quittez la session :</span><span class="sxs-lookup"><span data-stu-id="c3dd2-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="c3dd2-220">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="c3dd2-220">Key Concepts</span></span>
<span data-ttu-id="c3dd2-221">**Mode NoLanguage** : quand PowerShell est en mode « NoLanguage », les utilisateurs peuvent uniquement exécuter des commandes ; ils ne peuvent pas utiliser des éléments de langage.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="c3dd2-222">Pour plus d’informations, exécuter `Get-Help about_Language_Modes`.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="c3dd2-223">**Fonctions PowerShell** : les fonctions PowerShell sont des morceaux de code PowerShell que vous pouvez appeler par leur nom.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="c3dd2-224">Pour plus d’informations, exécuter `Get-Help about_Functions`.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="c3dd2-225">**ValidateSet/ValidatePattern** : lors de l’exposition d’une commande, vous pouvez restreindre les arguments valides de paramètres spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="c3dd2-226">ValidateSet correspond à la liste spécifique des arguments valides.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="c3dd2-227">ValidatePattern est une expression régulière à laquelle doivent correspondre les arguments de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

