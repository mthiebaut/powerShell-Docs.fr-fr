# Ressource WindowsProcess dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **WindowsProcess** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour configurer des processus sur un nœud cible.

## Syntaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Arguments| Indique une chaîne d’arguments à passer au processus en l’état. Si vous devez passer plusieurs arguments, placez-les dans cette chaîne.| 
| Path| Indique le chemin de l’exécutable du processus. Si vous définissez cette propriété sur le nom de l’exécutable, DSC examine la variable __Path__. Si vous donnez un nom de domaine complet, le processus doit exister dans ce dernier, car DSC ne vérifie pas la variable __Path__ dans ce cas.| 
| Credential| Indique les informations d’identification pour démarrer le processus.| 
| Ensure| Indique si le processus existe. Définissez cette propriété sur « Present » pour vous assurer que le package existe. Sinon, donnez-lui la valeur « Absent ». La valeur par défaut est « Present ».| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est « DependsOn = "[ResourceType]ResourceName" ».| 
| StandardErrorPath| Indique le chemin du répertoire dans lequel écrire l’erreur standard. Tout fichier existant est remplacé.| 
| StandardInputPath| Indique l’emplacement d’entrée standard.| 
| StandardOutputPath| Indique l’emplacement où écrire la sortie standard. Tout fichier existant est remplacé.| 
| WorkingDirectory| Indique l’emplacement à utiliser comme répertoire de travail actuel pour le processus.| 
<!--HONumber=Feb16_HO4-->
