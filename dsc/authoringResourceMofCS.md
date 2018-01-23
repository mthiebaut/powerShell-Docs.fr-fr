---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Création d’une ressource DSC en C#"
ms.openlocfilehash: 2fc6b8c127bca29e8f66fc7bd8d2828fdfe39f3c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="dacff-103">Création d’une ressource DSC en C#</span><span class="sxs-lookup"><span data-stu-id="dacff-103">Authoring a DSC resource in C#</span></span>

> <span data-ttu-id="dacff-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dacff-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="dacff-105">En règle générale, une ressource DSC Windows PowerShell personnalisée est implémentée dans un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dacff-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="dacff-106">Toutefois, vous pouvez également implémenter la fonctionnalité d’une ressource DSC personnalisée en écrivant des applets de commande en C#.</span><span class="sxs-lookup"><span data-stu-id="dacff-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="dacff-107">Pour une introduction à l’écriture des applets de commande en C#, consultez [Écriture d’une applet de commande Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span><span class="sxs-lookup"><span data-stu-id="dacff-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span></span>

<span data-ttu-id="dacff-108">À part l’implémentation de la ressource en tant qu’applets de commande en langage C#, les processus de création du schéma MOF, de création de la structure de dossiers, et de l’importation et de l’utilisation de votre ressource DSC personnalisée, sont les mêmes que ceux décrits dans [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="dacff-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="dacff-109">Écriture d’une ressource basée sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="dacff-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="dacff-110">Pour cet exemple, nous implémenterons une ressource simple qui gère un fichier texte et son contenu.</span><span class="sxs-lookup"><span data-stu-id="dacff-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="dacff-111">Écriture du schéma MOF</span><span class="sxs-lookup"><span data-stu-id="dacff-111">Writing the MOF schema</span></span>

<span data-ttu-id="dacff-112">Voici la définition de la ressource MOF.</span><span class="sxs-lookup"><span data-stu-id="dacff-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="dacff-113">Configuration du projet Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dacff-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="dacff-114">Configuration d’un projet d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dacff-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="dacff-115">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dacff-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="dacff-116">Créez un projet C# et donnez-lui un nom.</span><span class="sxs-lookup"><span data-stu-id="dacff-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="dacff-117">Sélectionnez **Bibliothèque de classes** dans les modèles de projet disponibles.</span><span class="sxs-lookup"><span data-stu-id="dacff-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="dacff-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dacff-118">Click **Ok**.</span></span>
1. <span data-ttu-id="dacff-119">Ajoutez une référence d’assembly à System.Automation.Management.dll dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="dacff-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="dacff-120">Modifiez le nom d’assembly pour qu’il corresponde au nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="dacff-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="dacff-121">Dans ce cas, l’assembly doit se nommer **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="dacff-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="dacff-122">Écriture du code de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dacff-122">Writing the cmdlet code</span></span>

<span data-ttu-id="dacff-123">Le code C# suivant implémente les applets de commande **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="dacff-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties 
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content 
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }
    
    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]
        
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed 
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }
            
            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */     

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
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
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path)) 
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }        
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="dacff-124">Déploiement de la ressource</span><span class="sxs-lookup"><span data-stu-id="dacff-124">Deploying the resource</span></span>

<span data-ttu-id="dacff-125">Le fichier .dll compilé doit être enregistré dans une structure de fichiers similaire à une ressource de script.</span><span class="sxs-lookup"><span data-stu-id="dacff-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="dacff-126">Voici la structure de dossiers de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="dacff-126">The following is the folder structure for this resource.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="dacff-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dacff-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="dacff-128">Concepts</span><span class="sxs-lookup"><span data-stu-id="dacff-128">Concepts</span></span>
[<span data-ttu-id="dacff-129">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="dacff-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="dacff-130">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="dacff-130">Other Resources</span></span>
[<span data-ttu-id="dacff-131">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dacff-131">Writing a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/library/dd878294.aspx)

