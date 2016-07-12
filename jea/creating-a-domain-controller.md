---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "création d’un contrôleur de domaine"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d4a72a7c5883b1d3ba8de3dbc9cfe016a6fb3498
ms.openlocfilehash: 8473eb668e4da5bab01c2f2b7647cbced413bd22

---

### Création d’un contrôleur de domaine

Ce document part du principe que votre ordinateur est joint à un domaine.
Si vous n’avez pas de domaine à rejoindre, cette section peut vous aider à rapidement mettre en place un contrôleur de domaine à l’aide de DSC.

#### Conditions préalables

1.  L’ordinateur se trouve sur un réseau interne.
2.  L’ordinateur n’est pas joint à un domaine existant.
3.  L’ordinateur exécute Windows Server 2016 ou WMF 5.0 y est installé.

#### Installer xActiveDirectory
Si votre ordinateur a une connexion Internet active, exécutez la commande suivante dans une fenêtre PowerShell avec élévation de privilèges :
```PowerShell
Install-Module xActiveDirectory -Force
```
Si vous n’avez pas de connexion Internet, installez xActiveDirectory sur un autre ordinateur, puis copiez le dossier xActiveDirectory dans le dossier « C:\Program Files\WindowsPowerShell\Modules » sur votre ordinateur.

Pour confirmer la réussite de l’installation, exécutez la commande suivante :
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### Configurer un domaine avec DSC
Copiez le script suivant dans PowerShell pour que votre ordinateur devienne un contrôleur de domaine dans un nouveau domaine.
**NOTE DE L’AUTEUR : IL EXISTE UN PROBLÈME CONNU LIÉ AUX INFORMATIONS D’IDENTIFICATION FOURNIES QUI NE SONT PAS UTILISÉES.  POUR PLUS DE SÉCURITÉ, N’OUBLIEZ PAS VOTRE MOT DE PASSE D’ADMINISTRATEUR LOCAL.**

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
Votre ordinateur va redémarrer plusieurs fois.
Vous savez que le processus est terminé une fois que vous voyez un fichier appelé « C:\temp.txt » indiquant que le domaine a été créé.

#### Configurer des utilisateurs et groupes
Les commandes suivantes configurent un groupe Opérateur et support technique dans votre domaine et un utilisateur non-administrateur correspondant qui est membre de ce groupe.
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




<!--HONumber=Jul16_HO1-->


