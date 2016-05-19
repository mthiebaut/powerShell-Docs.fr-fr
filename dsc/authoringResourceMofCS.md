# Création d’une ressource DSC en C`#`

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

En règle générale, une ressource DSC Windows PowerShell personnalisée est implémentée dans un script PowerShell. Toutefois, vous pouvez également implémenter la fonctionnalité d’une ressource DSC personnalisée en écrivant des applets de commande en C#. Pour une introduction à l’écriture des applets de commande en C#, consultez [Écriture d’une applet de commande Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx)..

À part l’implémentation de la ressource en tant qu’applets de commande en langage C#, les processus de création du schéma MOF, de création de la structure de dossiers, et de l’importation et de l’utilisation de votre ressource DSC personnalisée, sont les mêmes que ceux décrits dans [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)..

## Écriture d’une ressource basée sur une applet de commande
Pour cet exemple, nous implémenterons une ressource simple qui gère un fichier texte et son contenu.

### Écriture du schéma MOF

Voici la définition de la ressource MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Configuration du projet Visual Studio
#### Configuration d’un projet d’applet de commande

1. Ouvrez Visual Studio.
1. Créez un projet C# et donnez-lui un nom.
1. Sélectionnez **Bibliothèque de classes** dans les modèles de projet disponibles.
1. Cliquez sur **OK**..
1. Ajoutez une référence d’assembly à System.Automation.Management.dll dans votre projet.
1. Modifiez le nom d’assembly pour qu’il corresponde au nom de la ressource. Dans ce cas, l’assembly doit se nommer **MSFT_XDemoFile**..

### Écriture du code de l’applet de commande

Le code C# suivant implémente les applets de commande **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource**.

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Déploiement de la ressource

Le fichier .dll compilé doit être enregistré dans une structure de fichiers similaire à une ressource de script. Voici la structure de dossiers de cette ressource.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)     
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Voir aussi
#### Concepts
[Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)
#### Autres ressources
[Écriture d’une applet de commande Windows PowerShell](https://msdn.microsoft.com/en-us/library/dd878294.aspx)


<!--HONumber=May16_HO2-->


