---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "création d’un contrôleur de domaine"
ms.technology: powershell
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="a0da1-103">Création d’un contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="a0da1-103">Creating a Domain Controller</span></span>

<span data-ttu-id="a0da1-104">Ce document part du principe que votre ordinateur est joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="a0da1-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="a0da1-105">Si vous n’avez pas de domaine à rejoindre, cette section peut vous aider à rapidement mettre en place un contrôleur de domaine à l’aide de DSC.</span><span class="sxs-lookup"><span data-stu-id="a0da1-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="a0da1-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a0da1-106">Prerequisites</span></span>

1.  <span data-ttu-id="a0da1-107">L’ordinateur se trouve sur un réseau interne.</span><span class="sxs-lookup"><span data-stu-id="a0da1-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="a0da1-108">L’ordinateur n’est pas joint à un domaine existant.</span><span class="sxs-lookup"><span data-stu-id="a0da1-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="a0da1-109">L’ordinateur exécute Windows Server 2016 ou WMF 5.0 y est installé.</span><span class="sxs-lookup"><span data-stu-id="a0da1-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="a0da1-110">Installer xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="a0da1-110">Install xActiveDirectory</span></span>
<span data-ttu-id="a0da1-111">Si votre ordinateur a une connexion Internet active, exécutez la commande suivante dans une fenêtre PowerShell avec élévation de privilèges :</span><span class="sxs-lookup"><span data-stu-id="a0da1-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="a0da1-112">Si vous n’avez pas de connexion Internet, installez xActiveDirectory sur un autre ordinateur, puis copiez le dossier xActiveDirectory dans le dossier « C:\Program Files\WindowsPowerShell\Modules » sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0da1-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="a0da1-113">Pour confirmer la réussite de l’installation, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="a0da1-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="a0da1-114">Configurer un domaine avec DSC</span><span class="sxs-lookup"><span data-stu-id="a0da1-114">Set up a domain with DSC</span></span>
<span data-ttu-id="a0da1-115">Copiez le script suivant dans PowerShell pour que votre ordinateur devienne un contrôleur de domaine dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="a0da1-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="a0da1-116">**NOTE DE L’AUTEUR : IL EXISTE UN PROBLÈME CONNU LIÉ AUX INFORMATIONS D’IDENTIFICATION FOURNIES QUI NE SONT PAS UTILISÉES.  POUR PLUS DE SÉCURITÉ, N’OUBLIEZ PAS VOTRE MOT DE PASSE D’ADMINISTRATEUR LOCAL.**</span><span class="sxs-lookup"><span data-stu-id="a0da1-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
<span data-ttu-id="a0da1-117">Votre ordinateur va redémarrer plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="a0da1-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="a0da1-118">Vous savez que le processus est terminé une fois que vous voyez un fichier appelé « C:\temp.txt » indiquant que le domaine a été créé.</span><span class="sxs-lookup"><span data-stu-id="a0da1-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="a0da1-119">Configurer des utilisateurs et groupes</span><span class="sxs-lookup"><span data-stu-id="a0da1-119">Set up Users and Groups</span></span>
<span data-ttu-id="a0da1-120">Les commandes suivantes configurent un groupe Opérateur et support technique dans votre domaine et un utilisateur non-administrateur correspondant qui est membre de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="a0da1-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

