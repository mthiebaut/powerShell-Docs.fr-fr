# Ressource Script dans DSC

 
> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **Script** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour exécuter des blocs de script Windows PowerShell sur des nœuds cibles.

## Syntaxe

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| GetScript| Fournit un bloc de script Windows PowerShell qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx). Ce bloc doit retourner une table de hachage.| 
| SetScript| Fournit un bloc de script Windows PowerShell. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), le bloc **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne **$false**, le bloc **SetScript** s’exécute. Si le bloc **TestScript** retourne **$true**, le bloc **SetScript** ne s’exécute pas.| 
| TestScript| Fournit un bloc de script Windows PowerShell. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), ce bloc s’exécute. Si elle retourne **$false**, le bloc SetScript s’exécute. Si elle retourne **$true**, le bloc SetScript ne s’exécute pas. Le bloc **TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quelle que soit la valeur retournée par le bloc TestScript. Le bloc **TestScript** doit retourner True si la configuration réelle correspond à la configuration d’état souhaité actuelle, sinon False. (La configuration d’état souhaité actuelle est la dernière configuration appliquée sur le nœud qui utilise DSC.)| 
| Credential| Indique les informations d’identification à utiliser pour exécuter ce script, si elles sont nécessaires.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.

## Exemple
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

<!--HONumber=Feb16_HO4-->
