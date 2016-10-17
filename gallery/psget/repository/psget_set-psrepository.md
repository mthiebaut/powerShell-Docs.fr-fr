# Set-PSRepository

Set-PSRepository définit des valeurs pour un référentiel enregistré.

## Description

L’applet de commande Set-PSRepository définit des valeurs pour un référentiel de modules enregistré.

## Syntaxe de l’applet de commande

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## Référence de l’aide en ligne de l’applet de commande

[Set-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517128)

## Exemples de commandes

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### Applet de commande Set-PSRepository avec prise en charge du partage de script

Les applets de commande Set-PSRepository permettent d’ajouter **ScriptSourceLocation** et **ScriptPublishLocation** à PSRepository.
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```


<!--HONumber=Aug16_HO3-->


