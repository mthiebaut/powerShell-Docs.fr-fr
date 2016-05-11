# Accès direct aux méthodes de ressources DSC


L’applet de commande `Invoke-DscResource` a été ajoutée pour permettre d’accéder directement aux ressources DSC et à leurs méthodes (Get, Set ou Test). Elle peut être utilisée par des tiers qui souhaitent tirer parti des ressources DSC. Cette applet de commande est généralement utilisée avec `refreshMode = ‘Disabled’`, mais vous pouvez l’utiliser quelle que soit la valeur de refreshMode. Voici quelques exemples d’utilisation de la nouvelle applet de commande :

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


<!--HONumber=Apr16_HO4-->


