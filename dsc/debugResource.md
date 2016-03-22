# Débogage des ressources DSC

> S’applique à : Windows PowerShell 5.0

Dans PowerShell 5.0, DSC contient une nouvelle fonctionnalité qui permet de déboguer une ressource DSC pendant qu’une configuration est appliquée.

## Activation du débogage DSC
Avant de pouvoir déboguer une ressource, vous devez activer le débogage en appelant l’applet de commande [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx). Cette applet de commande prend un paramètre obligatoire : **BreakAll**. Vous pouvez vérifier que le débogage a été activé en examinant le résultat d’un appel à [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx). La sortie PowerShell suivante montre le résultat de l’activation du débogage :


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## Démarrage d’une configuration avec le débogage activé
Pour déboguer une ressource DSC, démarrez une configuration qui appelle cette ressource. Pour cet exemple, nous allons étudier une configuration simple qui appelle la ressource [WindowsFeature](windowsfeatureResource.md) pour vérifier que la fonctionnalité « WindowsPowerShellWebAccess » est bien installée :

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
Après la compilation de la configuration, démarrez-la en appelant [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). La configuration s’arrête quand
le gestionnaire de configuration local appelle la première ressource de la configuration. Si vous utilisez les paramètres `-Verbose` et `-Wait`, la sortie affiche les lignes que vous devez entrer
pour démarrer le débogage.

```powershell
PS C:\DebugTest> Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will 
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.  Use the follow
ing commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
À ce stade, le gestionnaire de configuration local a appelé la ressource et arrive au premier point d’arrêt. Les trois dernières lignes de la sortie vous montrent comment attacher au processus et commencer à déboguer le script de ressource.

## Débogage du script de la ressource

Démarrez une nouvelle instance de PowerShell ISE. Dans le volet console, entrez les trois dernières lignes de la sortie `Start-DscConifiguration` sous forme de commandes, en remplaçant `<credentials>` par
des informations d’identification valides. Voici la sortie obtenue :



<!--HONumber=Feb16_HO4-->
