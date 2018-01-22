# <a name="installing-powershell-core-on-windows"></a>Installation de PowerShell Core sous Windows

## <a name="msi"></a>MSI

Pour installer PowerShell sur un client Windows ou Windows Server (fonctionne sur Windows 7 SP1, Server 2008 R2, et versions ultérieures), téléchargez le package MSI à partir de notre page de [versions][] GitHub.

Le fichier MSI ressemble à ceci : `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Une fois téléchargé, double-cliquez sur le programme d’installation et suivez les invites.

Un raccourci est placé dans le menu Démarrer lors de l’installation.

* Par défaut, le package est installé dans `$env:ProgramFiles\PowerShell\`
* Vous pouvez lancer PowerShell via le menu Démarrer ou `$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Conditions préalables

Pour permettre la communication à distance PowerShell via WSMan, les conditions préalables suivantes doivent être remplies :

* Installer le [runtime C universel](https://www.microsoft.com/download/details.aspx?id=50410) sur les versions de Windows antérieures à Windows 10.
  Il est disponible par téléchargement direct ou sur Windows Update.
  Il est déjà installé sur les systèmes pris en charge où tous les correctifs sont installés (dont les packages facultatifs).
* Installer WMF (Windows Management Framework) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ou une version ultérieure ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) sur Windows 7 et Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Les archives ZIP binaires PowerShell sont fournies afin de permettre des scénarios de déploiement avancés.
Notez que, lors de l’utilisation de l’archive ZIP, les conditions préalables ne sont pas vérifiées comme pour le package MSI.
Ainsi, pour que la communication à distance via WSMan puisse fonctionner correctement sur les versions de Windows antérieures à Windows 10, vous devez vérifier que ces [conditions préalables](#prerequisites) sont remplies.

## <a name="deploying-on-nano-server"></a>Déploiement sur Nano Server

Ces instructions supposent qu’une version de PowerShell est déjà en cours d’exécution sur l’image Nano Server et qu’elle a été générée par le [Générateur d’images Nano Server](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server est un système d’exploitation « sans périphérique de contrôle » et le déploiement des fichiers binaires PowerShell Core peut se dérouler de deux manières différentes :

1. Hors connexion : montez le disque dur virtuel Nano Server et décompressez le contenu du fichier zip à l’emplacement que vous avez choisi dans l’image montée.
1. En ligne : transférez le fichier zip sur une session PowerShell et décompressez-le à l’emplacement que vous avez choisi.

Dans les deux cas, vous avez besoin du package de la version Zip Windows 10 x64 et devez exécuter les commandes dans une instance de PowerShell « Administrateur ».

### <a name="offline-deployment-of-powershell-core"></a>Déploiement hors connexion de PowerShell Core

1. Utilisez votre utilitaire zip favori pour décompresser le package dans un répertoire au sein de l’image Nano Server montée.
1. Démontez l’image et démarrez-la.
1. Connectez-vous à l’instance de boîte de réception de Windows PowerShell.
1. Suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [technique d’une autre instance](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Déploiement en ligne de PowerShell Core

La procédure suivante vous guide tout au long du déploiement de PowerShell Core sur une instance en cours d’exécution de Nano Server et la configuration de son point de terminaison distant.

* Connectez-vous à l’instance de boîte de réception de Windows PowerShell

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Copiez le fichier sur l’instance de Nano Server

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Entrez dans la session

```powershell
Enter-PSSession $session
```

* Extrayez le fichier Zip

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* Si vous voulez une communication à distance via WSMan, suivez les instructions pour créer un point de terminaison de communication à distance à l’aide de la [technique d’une autre instance](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructions pour créer un point de terminaison de communication à distance

PowerShell Core prend en charge le protocole de communication à distance PowerShell sur WSMan et SSH. Pour plus d’informations, voir :

* [Communication à distance SSH dans PowerShell Core][ssh-remoting]
* [Communication à distance WSMan dans PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instructions d’installation des artefacts

Nous publions une archive avec des bits CoreCLR sur chaque build CI avec [AppVeyor][].

## <a name="coreclr-artifacts"></a>Artefacts CoreCLR

* Téléchargez le package zip à partir de l’onglet des **artefacts** de la build particulière.
* Débloquez le fichier zip : cliquez avec le bouton droit dans l’Explorateur de fichiers -> Propriétés -> cochez la case Débloquer -> Appliquer
* Extrayez le fichier zip dans le répertoire `bin`
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versions]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
