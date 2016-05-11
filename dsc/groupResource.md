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
| GroupName| Spécifie le nom du groupe pour lequel vous souhaitez garantir un état spécifique.| 
| Credential| Indique les informations d’identification devant être fournies pour accéder aux ressources distantes. **Remarque** : Ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non locaux au groupe. Dans le cas contraire, une erreur se produit.
| Description| Spécifie la description du groupe.| 
| Ensure| Indique si le groupe existe. Définissez cette propriété sur Absent pour vous assurer que le groupe n’existe pas. Si vous la définissez sur Present (la valeur par défaut), vous pouvez vous assurer que le groupe existe.| 
| Members| Indique que vous voulez vous assurer que ces membres constituent le groupe.| 
| MembersToExclude| Spécifie les utilisateurs qui ne doivent pas faire partie du groupe.| 
| MembersToInclude| Spécifie les utilisateurs qui doivent faire partie du groupe.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"| 

## Exemple 1

L’exemple suivant montre comment s’assurer qu’un groupe nommé TestGroup est absent. 

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

<!--HONumber=Apr16_HO3-->


