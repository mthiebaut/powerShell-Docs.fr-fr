---
title: Ressources GroupSet dans DSC
ms.date: 2016-05-16
keywords: powershell, DSC, built-in, resource
description: "Fournit un mécanisme permettant de gérer des groupes locaux sur le nœud cible."
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: bf36abde6a3bfff4c2e49868465e089cc886d031
ms.openlocfilehash: 45fe96c43a834566d398820e3d94e3be923bb385

---

# Ressources GroupSet dans DSC

> S’applique à : Windows PowerShell 5.0

La ressource **GroupSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant de gérer des groupes locaux sur un nœud cible. Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [Group resource](groupResource.md) pour chaque groupe spécifié dans le paramètre `GroupName`.

Utilisez cette ressource quand vous souhaitez ajouter ou supprimer la même liste de membres dans plusieurs groupes, supprimer plusieurs groupes, ou ajouter plusieurs groupes avec la même liste de membres.

##Syntaxe##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| GroupName| Noms des groupes pour lesquels vous souhaitez garantir un état spécifique.| 
| MembersToExclude| Utilisez cette propriété pour supprimer des membres de l’appartenance existante des groupes. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur.| 
| Credential| Les informations d’identification devant être fournies pour accéder aux ressources distantes. **Remarque** : Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.
| Ensure| Indique si les groupes existent. Affectez la valeur « Absent » à cette propriété pour vous assurer que les groupes n’existent pas. La valeur « Present » (valeur par défaut) permet de s’assurer que les groupes existent.| 
| Members| Utilisez cette propriété pour remplacer l’appartenance à un groupe actuelle avec les membres spécifiés. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas les propriétés **MembersToExclude** et **MembersToInclude**. Cela générera une erreur.| 
| MembersToInclude| Utilisez cette propriété pour ajouter des membres aux appartenances existantes du groupe. La valeur de cette propriété est un tableau de chaînes au format *domaine*\\*nom d’utilisateur*. Si vous définissez cette propriété dans une configuration, n’utilisez pas la propriété **Members**. Cela générera une erreur.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"| 

## Exemple 1

L’exemple suivant montre comment s’assurer que les deux groupes « myGroup » et « myOtherGroup » sont présents. 

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**Remarque :** Cet exemple utilise des informations d’identification en texte clair par souci de simplicité. Pour plus d’informations sur la façon de chiffrer des informations d’identification dans le fichier MOF de configuration, consultez [Sécurisation du fichier MOF](secureMOF.md).





<!--HONumber=Jul16_HO1-->


