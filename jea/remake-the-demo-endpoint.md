---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "refaire le point de terminaison de démonstration"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="48be7-103">Refaire le point de terminaison de démonstration</span><span class="sxs-lookup"><span data-stu-id="48be7-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="48be7-104">Dans cette section, vous allez apprendre à générer un réplica exact du point de terminaison de démonstration que vous avez utilisé dans la section ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="48be7-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="48be7-105">Des concepts essentiels à la compréhension de JEA vont ainsi être présentés, notamment les configurations de session PowerShell et les capacités de rôle.</span><span class="sxs-lookup"><span data-stu-id="48be7-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="48be7-106">Configurations de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="48be7-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="48be7-107">Quand vous avez utilisé JEA dans la section ci-dessus, vous avez démarré en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="48be7-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="48be7-108">Même si les noms des paramètres sont explicites, le paramètre *ConfigurationName* peut sembler déroutant dans un premier temps.</span><span class="sxs-lookup"><span data-stu-id="48be7-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="48be7-109">Ce paramètre spécifiait la configuration de session PowerShell à laquelle vous vous connectiez.</span><span class="sxs-lookup"><span data-stu-id="48be7-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="48be7-110">Une *configuration de session PowerShell* est une locution technique qui désigne un point de terminaison PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="48be7-111">Métaphoriquement, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="48be7-112">Selon la façon dont vous paramétrez une configuration de session, elle peut fournir des fonctionnalités différentes aux utilisateurs qui se connectent.</span><span class="sxs-lookup"><span data-stu-id="48be7-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="48be7-113">Pour JEA, nous utilisons des configurations de session afin de restreindre PowerShell à un ensemble limité de fonctionnalités et pour une exécution en tant que compte virtuel privilégié.</span><span class="sxs-lookup"><span data-stu-id="48be7-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="48be7-114">Vous avez déjà plusieurs configurations de session PowerShell inscrites sur votre ordinateur, chacune étant configurée de façon légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="48be7-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="48be7-115">La plupart d’entre elles sont fournies avec Windows, mais la configuration de session « JEA_Demo » a été configurée pendant la section [Conditions préalables](prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="48be7-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="48be7-116">Vous pouvez voir toutes les configurations de session inscrites en exécutant la commande suivante depuis une invite PowerShell d’administrateur :</span><span class="sxs-lookup"><span data-stu-id="48be7-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="48be7-117">Fichiers de configuration de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="48be7-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="48be7-118">Vous pouvez créer des configurations de session en inscrivant de nouveaux *fichiers de configuration de session PowerShell*.</span><span class="sxs-lookup"><span data-stu-id="48be7-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="48be7-119">Les fichiers de configuration de session portent une extension de fichier « .pssc ».</span><span class="sxs-lookup"><span data-stu-id="48be7-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="48be7-120">Vous pouvez générer des fichiers de configuration de session avec l’applet de commande New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="48be7-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="48be7-121">Ensuite, vous allez créer et inscrire une configuration de session pour JEA.</span><span class="sxs-lookup"><span data-stu-id="48be7-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="48be7-122">Générer et modifier votre configuration de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="48be7-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="48be7-123">Exécutez la commande suivante pour générer un fichier « squelette » de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="48be7-124">**Conseil :** Seuls les paramètres de configuration les plus courants sont inclus dans le fichier squelette par défaut.</span><span class="sxs-lookup"><span data-stu-id="48be7-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="48be7-125">Utilisez le paramètre `-Full` pour inclure tous les paramètres applicables dans le fichier PSSC généré.</span><span class="sxs-lookup"><span data-stu-id="48be7-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="48be7-126">Ouvrez le fichier dans PowerShell ISE ou votre éditeur de texte favori.</span><span class="sxs-lookup"><span data-stu-id="48be7-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="48be7-127">Mettez à jour les champs suivants dans le fichier à l’aide des valeurs ci-dessous (pensez à les remplacer dans votre propre groupe de sécurité non-administrateur) :</span><span class="sxs-lookup"><span data-stu-id="48be7-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="48be7-128">Voici la signification de chacune de ces entrées :</span><span class="sxs-lookup"><span data-stu-id="48be7-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="48be7-129">Le champ *SessionType* définit des paramètres prédéfinis par défaut à utiliser avec ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="48be7-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="48be7-130">*RestrictedRemoteServer* définit les paramètres minimum nécessaires à la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="48be7-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="48be7-131">Par défaut, un point de terminaison *RestrictedRemoteServer* expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host et Out-Default.</span><span class="sxs-lookup"><span data-stu-id="48be7-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="48be7-132">Il définit *ExecutionPolicy* sur *RemoteSigned* et *LanguageMode* sur *NoLanguage*.</span><span class="sxs-lookup"><span data-stu-id="48be7-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="48be7-133">L’effet net de ces paramètres est un point de départ sécurisé et minimal pour la configuration de votre point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="48be7-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="48be7-134">Le champ *RoleDefinitions* affecte des capacités de rôle à des groupes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="48be7-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="48be7-135">Il définit qui peut faire quoi en tant que compte privilégié.</span><span class="sxs-lookup"><span data-stu-id="48be7-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="48be7-136">Avec ce champ, vous pouvez spécifier les capacités disponibles pour tout utilisateur qui tente d’établir une connexion en fonction de son appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="48be7-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="48be7-137">Là est l’essence de la fonctionnalité RBAC de JEA.</span><span class="sxs-lookup"><span data-stu-id="48be7-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="48be7-138">Dans cet exemple, vous exposez le champ RoleCapability « Maintenance » prédéfini aux membres du groupe « Contoso\JEA_NonAdmin_Operator ».</span><span class="sxs-lookup"><span data-stu-id="48be7-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="48be7-139">Le champ *RunAsVirtualAccount* indique que PowerShell doit « s’exécuter en tant que » compte virtuel sur ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="48be7-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="48be7-140">Par défaut, le compte virtuel est membre du groupe Administrateurs prédéfini.</span><span class="sxs-lookup"><span data-stu-id="48be7-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="48be7-141">Sur un contrôleur de domaine, il est également membre du groupe Administrateurs du domaine par défaut.</span><span class="sxs-lookup"><span data-stu-id="48be7-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="48be7-142">Plus loin dans ce guide, vous allez apprendre à personnaliser les privilèges du compte virtuel.</span><span class="sxs-lookup"><span data-stu-id="48be7-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="48be7-143">Le champ *TranscriptDirectory* définit l’emplacement auquel sont enregistrées les transcriptions PowerShell « de procuration de privilège » après chaque session à distance.</span><span class="sxs-lookup"><span data-stu-id="48be7-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="48be7-144">Ces transcriptions vous permettent d’inspecter les actions effectuées dans chaque session de façon lisible.</span><span class="sxs-lookup"><span data-stu-id="48be7-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="48be7-145">Pour plus d’informations sur les transcriptions PowerShell, consultez ce [billet de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="48be7-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="48be7-146">Remarque : Windows Eventing capture également des informations sur ce que chaque utilisateur a exécuté avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="48be7-147">Les transcriptions sont juste un peu plus faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="48be7-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="48be7-148">Enfin, enregistrez vos modifications dans *JEADemo2.pssc*.</span><span class="sxs-lookup"><span data-stu-id="48be7-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="48be7-149">Appliquer la configuration de session PowerShell</span><span class="sxs-lookup"><span data-stu-id="48be7-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="48be7-150">Pour créer un point de terminaison à partir d’un fichier de configuration de session, vous devez inscrire ce fichier.</span><span class="sxs-lookup"><span data-stu-id="48be7-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="48be7-151">Quelques éléments d’information sont alors nécessaires :</span><span class="sxs-lookup"><span data-stu-id="48be7-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="48be7-152">Le chemin du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="48be7-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="48be7-153">Le nom de votre configuration de session inscrite.</span><span class="sxs-lookup"><span data-stu-id="48be7-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="48be7-154">Il s’agit du même nom que celui que les utilisateurs fournissent pour le paramètre « ConfigurationName » quand ils se connectent à votre point de terminaison avec `Enter-PSSession` ou `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="48be7-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="48be7-155">Pour inscrire la configuration de session sur votre ordinateur local, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="48be7-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="48be7-156">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="48be7-156">Congratulations!</span></span> <span data-ttu-id="48be7-157">Vous avez configuré votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="48be7-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="48be7-158">Tester votre point de terminaison</span><span class="sxs-lookup"><span data-stu-id="48be7-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="48be7-159">Réexécutez les étapes répertoriées dans la section [Utilisation de JEA](using-jea.md) pour votre nouveau point de terminaison afin de vérifier qu’il fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="48be7-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="48be7-160">Veillez à utiliser le nouveau nom de point de terminaison (JEADemo2) quand vous indiquez le nom de la configuration dans l’applet de commande `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="48be7-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="48be7-161">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="48be7-161">Key Concepts</span></span>
<span data-ttu-id="48be7-162">**Configuration de session PowerShell** : parfois appelée *point de terminaison PowerShell*, il s’agit de l’endroit où les utilisateurs se connectent et accèdent aux fonctionnalités de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="48be7-163">Vous pouvez répertorier les configurations de session inscrites sur votre système en exécutant `Get-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="48be7-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="48be7-164">Paramétrée de manière spécifique, une configuration de session PowerShell peut être appelée *point de terminaison JEA*.</span><span class="sxs-lookup"><span data-stu-id="48be7-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="48be7-165">**Fichier de configuration de session PowerShell (.pssc)** : fichier qui, une fois inscrit, définit les paramètres d’une configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="48be7-166">Il contient des spécifications pour les rôles d’utilisateurs qui peuvent se connecter au point de terminaison, le compte d’identification virtuel, etc.</span><span class="sxs-lookup"><span data-stu-id="48be7-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="48be7-167">**Définitions de rôles** : champ dans un fichier de configuration de session qui définit les capacités de rôle accordées aux utilisateurs qui tentent d’établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="48be7-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="48be7-168">Ce champ définit *qui* peut faire *quoi* en tant que compte privilégié.</span><span class="sxs-lookup"><span data-stu-id="48be7-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="48be7-169">Là est l’essence des fonctionnalités RBAC de JEA.</span><span class="sxs-lookup"><span data-stu-id="48be7-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="48be7-170">**SessionType** : champ dans un fichier de configuration de session qui représente les paramètres par défaut d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="48be7-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="48be7-171">Pour les points de terminaison JEA, ce champ doit avoir la valeur RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="48be7-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="48be7-172">**Transcription PowerShell** : fichier contenant une vue par procuration de privilège d’une session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48be7-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="48be7-173">Vous pouvez définir PowerShell de sorte à générer des transcriptions pour les sessions JEA à l’aide du champ TranscriptDirectory.</span><span class="sxs-lookup"><span data-stu-id="48be7-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="48be7-174">Pour plus d’informations sur les transcriptions, consultez ce [billet de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span><span class="sxs-lookup"><span data-stu-id="48be7-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

