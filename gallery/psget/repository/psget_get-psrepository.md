# Get-PSRepository

Obtient les référentiels enregistrés sur un ordinateur.

## Description

L’applet de commande Get-PSRepository obtient les référentiels de modules PowerShell qui sont enregistrés pour l’utilisateur actuel sur un ordinateur.

Pour chaque référentiel enregistré, Get-PSRepository retourne un objet PSRepository qui peut éventuellement être transmis à Unregister-PSRepository pour annuler l’enregistrement d’un référentiel enregistré.

## Syntaxe de l’applet de commande
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Référence de l’aide en ligne de l’applet de commande

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## Exemples de commandes

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

<!--HONumber=Aug16_HO3-->


