---
title: Validations des signatures de configurations et de modules DSC
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##Validations des signatures de configurations et de modules DSC
Dans DSC, les modules et les documents de configuration sont distribués aux ordinateurs gérés à partir du serveur ou service collecteur (dans le cas du service collecteur Azure Automation). Si le serveur/service collecteur est compromis, un attaquant peut potentiellement modifier les configurations et les modules sur le serveur collecteur pour les distribuer à tous les ordinateurs gérés, en compromettant ainsi encore plus d’ordinateurs du client. 

 Cette menace est résolue dans WMF 5.1. DSC prend en charge la validation des signatures numériques sur les modules et fichiers de configuration (.MOF). Cette fonctionnalité empêche les nœuds d’exécuter une configuration ou des fichiers de modules qui ne sont pas signés par un signataire approuvé ou qui ont été falsifiés après avoir été signés par un signataire approuvé. 



###Comment signer des configurations et modules 
***
1. Fichiers de configuration (.MOF) : l’applet de commande PowerShell existante [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) est étendue pour prendre en charge la signature des fichiers MOF.  
2. Modules : la signature de modules s’effectue en signant le catalogue de module correspondant en procédant comme suit : 
    * Créer un fichier catalogue : un fichier catalogue contient une collection de hachages de chiffrement ou d’empreintes numériques. Chaque empreinte correspond à un fichier qui est inclus dans le module.  Une nouvelle applet de commande, [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), a été ajoutée pour permettre aux utilisateurs de créer un fichier catalogue pour leur module. Reportez-vous aux applets de commande de catalogue [lien relatif](catalog-cmdlets.md) pour créer des fichiers catalogue. 
    * Signer le fichier catalogue : utilisez [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) pour signer le fichier catalogue.
    * Placer le fichier catalogue dans le dossier de module.
Par convention, le fichier catalogue de module doit être placé sous le dossier de module portant le même nom que le module.

###Paramètres du gestionnaire de configuration local pour activer les validations des signatures.

####EXTRACTION
Le gestionnaire de configuration local d’un nœud effectue une validation des signatures des modules et des configurations en fonction de ses paramètres actifs. Par défaut, la validation des signatures est désactivée. La validation des signatures peut être activée en ajoutant le bloc SignatureValidation à la définition de métaconfiguration du nœud comme indiqué ci-dessous :

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

La définition de la métaconfiguration ci-dessus sur un nœud active la validation des signatures sur les configurations et modules téléchargés. Le gestionnaire de configuration local effectue les étapes suivantes pour vérifier les signatures numériques.
* Il vérifie que la signature d’un fichier de configuration (.MOF) est valide. Il utilise l’applet de commande PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) qui est étendue dans 5.1 pour prendre en charge la validation des signatures MOF.
* Il vérifie que l’autorité de certification qui a autorisé le signataire est approuvée.
* Il télécharge les dépendances de ressources/modules de la configuration à un emplacement temporaire.
* Il vérifie la signature du catalogue qui figure dans le module.
    * Il recherche un fichier <moduleName>.cat et vérifie sa signature à l’aide de l’applet de commande [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Il vérifie que l’autorité de certification qui a authentifié le signataire est approuvée.
    * Il vérifie que le contenu des modules n’a pas été falsifié à l’aide de la nouvelle applet de commande [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
* Il installe le module dans $env:ProgramFiles\WindowsPowerShell\Modules\
* Il traite la configuration.

Remarque : La validation des signatures sur le catalogue de module et la configuration est effectuée uniquement quand la configuration est appliquée au système pour la première fois ou quand le module est téléchargé et installé. La série de tests de cohérence ne valide pas la signature de Current.mof ni ses dépendances de modules.
Si la vérification a échoué à un stade, par exemple si la configuration collectée à partir du serveur collecteur n’est pas signée, le traitement de la configuration s’arrête avec l’erreur affichée ci-dessous et tous les fichiers temporaires sont supprimés.

![Exemple de configuration de sortie d’erreur](../../images/PullUnsignedConfigFail.PNG)

De la même manière, l’extraction d’un module dont le catalogue n’est pas signé entraîne l’erreur suivante :

![Exemple de module de sortie d’erreur](../../images/PullUnisgnedCatalog.PNG)

####ENVOI
Une configuration transmise par envoi de données peut être falsifiée à sa source avant d’être remise au nœud. Le gestionnaire de configuration local effectue des étapes de validation des signatures similaires pour les configurations envoyées ou publiées.
Voici un exemple complet de validation des signatures pour l’envoi.

* Activez la validation des signatures sur le nœud.

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* Créez un exemple de fichier de configuration.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* Essayez d’envoyer le fichier de configuration non signé au nœud. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* Signez le fichier de configuration avec un certificat de signature de code.

![SignMofFile](../../images/SignMofFile.PNG)

* Essayez d’envoyer le fichier mof signé.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


