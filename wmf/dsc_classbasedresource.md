# Ressources DSC basées sur une classe

## Définition de ressources DSC avec des classes

Suite à vos commentaires, nous avons simplifié la création et la compréhension des ressources DSC basées sur des classes. 
Les principales différences entre une ressource DSC basée sur une classe et un fournisseur de ressources DSC d’applet de commande sont les suivantes :

* Aucun fichier MOF pour le schéma n’est nécessaire.
* Aucun sous-dossier **DSCResource** dans le dossier de module n’est nécessaire.
* Un fichier de module PowerShell peut contenir plusieurs classes de ressources DSC.

Voici un exemple de ressource DSC basée sur une classe qui étend l’autre ressource DSC de classe dans le même fichier. Elle est enregistrée en tant que module nommé **MyDSCResource.psm1**. 
Notez que vous devez toujours inclure au moins une propriété clé et une méthode Get, Set ou Test dans une ressource DSC définie par une classe ou ses classes de base.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
This resource manages the file in a specific path.
[DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class BaseFileResource
{
<#
This property is the fully qualified path to the file that is expected to be present or absent.

The [DscProperty(Key)] attribute indicates the property is a key and its value uniquely identifies a resource instance. Defining this attribute also means the property is required and DSC will ensure a value is set before calling the resource.

A DSC resource must define at least one key property.
#>

[DscProperty(Key)]
[string]$Path

<#
This property indicates if the settings should be present or absent on the system.

For present, the resource ensures the file pointed to by $Path exists. For absent, it ensures the file that $Path points to does not exist.

The [DscProperty(Mandatory)] attribute indicates the property is required and DSC will guarantee it is set.

If Mandatory is not specified or if it is defined as Mandatory=$false, the value is not guaranteed to be set when DSC calls the resource. This is appropriate for optional properties.
#>

[DscProperty(Mandatory)]
[Ensure] $Ensure

<#
This property defines the fully qualified path to a file that will be placed on the system if $Ensure = Present and $Path does not exist.
NOTE: This property is required because [DscProperty(Mandatory)] is set.
#>

[DscProperty(Mandatory)]
[string] $SourcePath

<#
This property reports the file's creation timestamp.

[DscProperty(NotConfigurable)] attribute indicates the property is not configurable in a DSC configuration. Properties marked this way are populated by the Get() method to report additional details about the resource when it is present.
#>

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime

<#
This method is equivalent of the Set-TargetResource script function.
It sets the resource to the desired state.
#>

[void] Set()
{
    $fileExists = $this.TestFilePath($this.Path)
    if($this.ensure -eq [Ensure]::Present)
    {
        if(-not $fileExists)
        {
            $this.CopyFile()
        }
    }

    else
    {
        if($fileExists)
        {
            Write-Verbose -Message "Deleting the file $($this.Path)"
            Remove-Item -LiteralPath $this.Path -Force
        }
    }
}

<#
This method is equivalent of the Test-TargetResource script function.
It should return True or False, showing whether the resource is in a desired state.
#>

[bool] Test()
{
    $present = $this.TestFilePath($this.Path)

    if($this.Ensure -eq [Ensure]::Present)
    {
        return $present
    }

    else
    {
        return -not $present
    }
}

<#
This method is equal to the Get-TargetResource script function.
The implementation should use the keys to find appropriate resources.
This method returns an instance of this class with the updated key properties.
#>

[BaseFileResource] Get()
{
    $present = $this.TestFilePath($this.Path)

    if ($present)
    {
        $file = Get-ChildItem -LiteralPath $this.Path
        $this.CreationTime = $file.CreationTime
        $this.Ensure = [Ensure]::Present
    }

    else
    {
        $this.CreationTime = $null
        $this.Ensure = [Ensure]::Absent
    }
    
    return $this
}

<#
Helper method to check if the file exists and it is the right file
#>

[bool] TestFilePath([string] $location)
{
    $present = $true
    $item = Get-ChildItem -LiteralPath $location -ea Ignore
    
    if ($item -eq $null)
    {
        $present = $false
    }
    elseif($item.PSProvider.Name -ne "FileSystem")
    {
        throw "Path $($location) is not a file path."
    }
    elseif($item.PSIsContainer)
    {
        throw "Path $($location) is a directory path."
    }

return $present
}

<#
Helper method to copy the file from source to path
#>

[void] CopyFile()
{
    if(-not $this.TestFilePath($this.SourcePath))
    {
        throw "SourcePath $($this.SourcePath) is not found."
    }

    [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
    if (-not $destFileInfo.Directory.Exists)
    {
        Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"
    
        # use CreateDirectory instead of New-Item to avoid code
        # to handle the non-terminating error
        [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
    }

    if(Test-Path -LiteralPath $this.Path -PathType Container)
    {
        throw "Path $($this.Path) is a directory path"
    }

    Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"
    # DSC engine catches and reports any error that occurs
    Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
}
}

<#
This resource inherits from the [BaseFileResource]
It reports additional information in Get method
#>

[DscResource()]
class FileResource : BaseFileResource
{
    <#
    This property reports if it is a readonly file
    #>
    [DscProperty(NotConfigurable)]
    [bool] $IsReadOnly

    <#
    This property reports the file's LastAccessTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastAccessTime

    <#
    This property reports the file's LastWriteTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastWriteTime

    <#
    This method overrides the Get method in the base class.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)
        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.IsReadOnly = $file.IsReadOnly
            $this.LastAccessTime = $file.LastAccessTime
            $this.LastWriteTime = $file.LastWriteTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.LastAccessTime = $null
            $this.LastWriteTime = $null
            $this.Ensure = [Ensure]::Absent
        }

    return $this
}

}
```

Après avoir créé le fournisseur de ressources DSC défini par une classe et l’avoir enregistré en tant que module, créez un manifeste de module pour ce module. Dans cet exemple, le manifeste de module suivant est enregistré en tant que **MyDscResource.psd1**.

```powershell
@{
# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to identify this module uniquely
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2015 User01. All rights reserved.'

# Description of the functionality provided by this module
Description = 'DSC resource provider for FileResource.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Required for DSC to detect PS class-based resources.
DscResourcesToExport = @('BaseFileResource','FileResource')
}
```

Déployez le nouveau fournisseur de ressources DSC en créant un dossier **MyDscResource** sous `$env:SystemDrive\Program Files\WindowsPowerShell\Modules`.
Il est inutile de créer un sous-dossier DSCResource.
Copiez les fichiers de module et de manifeste de module (**MyDscResource.psm1** et **MyDscResource.psd1**) dans le dossier **MyDscResource**.

Désormais, vous pouvez créer et exécuter un script de configuration comme vous le feriez avec n’importe quelle ressource DSC. 
Voici une configuration qui fait référence au module MyDSCResource. 
Enregistrez-la en tant que script nommé **MyResource.ps1**.

```powershell
Configuration MyConfig
{
    Import-Dscresource -ModuleName MyDscResource
    BaseFileResource file
    {
        Path = "C:\test\baseFile.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }

    FileResource file
    {
        Path = "C:\test\File.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}

MyConfig
```

Exécutez ce script comme vous le feriez pour n’importe quel script de configuration DSC. Pour démarrer la configuration, dans une console Windows PowerShell avec élévation de privilèges, exécutez l’applet de commande suivante. 
Vous constaterez que la sortie Get-DscConfiguration de FileResource contient davantage d’informations que BaseFileResource.

```powershell
.\MyResource.ps1
Start-DscConfiguration c:\test\MyConfig –Wait –Verbose
Get-DscConfiguration
```

## Problèmes connus

Voici une liste des problèmes connus avec les ressources DSC basées sur des classes dans cette version :

* Get-DscConfiguration peut retourner des valeurs vides (null) ou des erreurs si un type complexe est retourné par la fonction Get() d’une ressource DSC basée sur une classe.
* Les ressources composites ne peuvent pas être écrites en tant que ressources basées sur des classes.
<!--HONumber=Mar16_HO2-->
