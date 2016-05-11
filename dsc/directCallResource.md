# Appel direct de méthodes de ressources DSC

>S’applique à : Windows PowerShell 5.0

Vous pouvez utiliser l’applet de commande [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) pour appeler directement les fonctions ou méthodes d’une ressource DSC (les fonctions **Get-TargetResource**,
**Set-TargetResource** et **Test-TargetResource** d’une ressource basée sur MOF, ou les méthodes **Get**, **Set** et **Test** d’une ressource basée sur la classe). 
Elle peut être utilisée par des tiers qui veulent utiliser des ressources DSC, ou comme un outil très utile lors du développement de ressources. 

Cette applet de commande est généralement utilisée avec une propriété de métaconfiguration `refreshMode = 'Disabled'`, mais vous pouvez l’utiliser quelle que soit la valeur de **refreshMode**.

Lors de l’appel de l’applet de commande **Invoke-DscResource**, vous spécifiez la méthode ou fonction à appeler à l’aide du paramètre **Method**. Vous spécifiez les propriétés de la ressource en passant une 
table de hachage comme valeur du paramètre **Property**.

Voici quelques exemples d’appels directs de méthodes de ressources :

## S’assurer de la présence d’un fichier

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Tester la présence d’un fichier

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Obtenir le contenu du fichier

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

## Voir aussi
- [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md) 
- [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md)
- [Débogage des ressources DSC](debugResource.md)

<!--HONumber=Apr16_HO4-->


