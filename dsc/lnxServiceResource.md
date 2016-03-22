# Ressource nxService dans DSC pour Linux

La ressource **nxService** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des services sur un nœud Linux.

## Syntaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés
|  Propriété |  Description | 
|---|---|
| Name| Nom du service/démon à configurer.| 
| Controller| Type de contrôleur de service à utiliser lors de la configuration du service.| 
| Enabled| Indique si le service s’exécute au démarrage du système.| 
| State| Indique si le service est en cours d’exécution. Définissez cette propriété sur « Stopped » pour vous assurer que le service n’est pas en cours d’exécution. Définissez cette propriété sur « Running » pour vous assurer que le service est en cours d’exécution.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 


## Informations supplémentaires

La ressource **nxService** ne crée pas de fichier de définition ni de script pour le service si celui-ci n’existe pas. Vous pouvez utiliser la ressource **nxFile** dans DSC PowerShell pour gérer l’existence ou le contenu du fichier de définition ou script du service.

## Exemple

L’exemple suivant configure le service « httpd » (pour Apache HTTP Server) qui est inscrit auprès du contrôleur de service **SystemD**.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```
<!--HONumber=Mar16_HO1-->
