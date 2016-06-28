---
title: Ressource Group DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: f6e33f82f495a89a4aa28c64b7974c170d50cfe1
ms.openlocfilehash: 446c9036989c47c03664d978a1dea4e0234ada8d

---

# Ressource Group DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource Group dans DSC Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible.

##Syntaxe##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| GroupName| Le nom du groupe pour lequel vous souhaitez garantir un état spécifique.| 
| Credential| Les informations d’identification devant être fournies pour accéder aux ressources distantes. **Remarque** : Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.
| Description| La description du groupe.| 
| Ensure| Indique si le groupe existe. Définissez cette propriété sur Absent pour vous assurer que le groupe n’existe pas. Si vous la définissez sur Present (la valeur par défaut), vous pouvez vous assurer que le groupe existe.| 
| Membres| Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**. Cela générera une erreur.| 
| MembersToExclude| Utilisez cette propriété pour supprimer des appartenances existantes du groupe. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur.| 
| MembersToInclude| Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"| 

## Exemple 1

L’exemple suivant montre comment s’assurer qu’un groupe nommé « TestGroup » est absent. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## Exemple 2
L’exemple suivant montre comment ajouter un utilisateur Active Directory au groupe Administrateurs local dans le cadre d’une build de laboratoire avec plusieurs ordinateurs où vous utilisez déjà un PSCredential pour le compte d’administrateur Local. Comme il est également utilisé pour le compte d’administrateur de domaine (après la promotion de domaine), nous devons convertir ce PSCredential existant en informations d’identification conviviales du domaine pour pouvoir ajouter un utilisateur de domaine au groupe Administrateurs local sur le serveur membre.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```




<!--HONumber=Jun16_HO4-->


