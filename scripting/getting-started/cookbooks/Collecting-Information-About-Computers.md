---
title: Collecte d’informations sur les ordinateurs
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
---
# Collecte d’informations sur les ordinateurs
L’applet de commande **Get-WmiObject** est la plus importante pour les tâches générales de gestion du système. Tous les paramètres critiques du sous-système sont exposés via WMI. En outre, WMI traite les données en tant qu’objets figurant dans des collections d’un ou plusieurs éléments. Étant donné que Windows PowerShell fonctionne également avec des objets et dispose d’un pipeline permettant de traiter un ou plusieurs objets de la même façon, l’accès générique à WMI permet d’effectuer des tâches avancées sans grand effort.

Les exemples suivants montrent comment collecter des informations spécifiques en appliquant l’applet de commande **Get-WmiObject** à un ordinateur arbitraire. Nous spécifions le paramètre **ComputerName** avec la valeur de point (**.**) qui représente l’ordinateur local. Vous pouvez spécifier un nom ou une adresse IP associés à tout ordinateur accessible via WMI. Pour récupérer des informations sur l’ordinateur local, vous pourriez omettre le paramètre **-ComputerName**.

### Affichage de la liste des paramètres de bureau
Nous allons commencer par une commande qui collecte des informations concernant les postes de travail sur l’ordinateur local.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Cette commande retourne des informations sur tous les postes de travail, qu’ils soient en cours d’utilisation ou non.

> [!NOTE]
> Les informations retournées par certaines classes WMI peuvent être très détaillées, et incluent souvent des métadonnées sur la classe WMI. Étant donné que la plupart de ces propriétés de métadonnées portent des noms commençant par un trait de soulignement double, vous pouvez filtrer les propriétés à l’aide de l’applet de commande Select-Object. Spécifiez uniquement les propriétés commençant par des caractères alphabétiques en utilisant **[a-z] &#42;** comme valeur de propriété. Par exemple :

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Pour exclure les métadonnées, utilisez un opérateur de pipeline (|) pour envoyer les résultats de la commande Get-WmiObject à **Select-Object -Property [a-z]& #42 ;**.

### Affichage d’informations sur le BIOS
La classe WMI Win32_BIOS retourne des informations relativement compactes et complètes sur le BIOS de l’ordinateur local :

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### Affichage d’informations sur le processeur
Vous pouvez récupérer des informations générales sur le processeur à l’aide de la classe **Win32_Processor** de WMI, même si vous pouvez filtrer les informations :

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Pour une chaîne de description générique de la famille de processeurs, vous pouvez simplement retourner la propriété **Win32_ComputerSystemSystemType** :

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### Affichage du modèle et du fabricant de l’ordinateur
Des informations sur le modèle d’ordinateur sont également accessibles via l’applet de commande **Win32_ComputerSystem**. La sortie standard affichée ne nécessite pas de filtrage pour fournir des données OEM :

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

La qualité de la sortie de telles commandes, qui retournent des informations directement à partir de certains composants matériels, dépend des données dont vous disposez. Il se peut que des informations mal configurées par certains fabricants de matériel ne soient pas être disponibles.

### Affichage de la liste des correctifs installés
Vous pouvez afficher la liste de tous les correctifs à l’aide de la classe **Win32_QuickFixEngineering** :

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Cette classe retourne une liste des correctifs ressemblant à ceci :

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Pour une sortie plus concise, vous pouvez exclure certaines propriétés. Vous pouvez utiliser le paramètre **Get-WmiObject Property** pour choisir uniquement le **HotFixID**. Cela permet d’obtenir plus d’informations, car toutes les métadonnées sont affichées par défaut :

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Les données supplémentaires sont retournées, car le paramètre Property dans l’applet de commande **Get-WmiObject** restreint les propriétés retournées par les instances de classe WMI, pas l’objet retourné à Windows PowerShell. Pour réduire la sortie, utilisez l’applet de commande **Select-Object** :

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### Affichage d’informations sur la version du système d’exploitation
Les propriétés de la classe **Win32_OperatingSystem** incluent des informations sur la version et le Service Pack. Vous ne pouvez sélectionner explicitement que ces propriétés pour obtenir un résumé d’informations sur la version résumé à partir de la classe **Win32_OperatingSystem** :

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Vous pouvez également utiliser des caractères génériques avec le paramètre **Select-Object Property**. Étant donné que l’utilisation de toutes les propriétés commençant par **Build** ou **ServicePack** est importante ici, nous pouvons raccourcir cela en utilisant la forme suivante :

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### Affichage des utilisateurs locaux et du propriétaire
Vous pouvez trouver des informations générales sur l’utilisateur local (nombre d’utilisateurs sous licence, nombre actuel d’utilisateurs et nom du propriétaire) avec une sélection de propriétés de la classe **Win32_OperatingSystem**. Vous pouvez sélectionner explicitement les propriétés à afficher comme suit :

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Une version plus concise utilisant des caractères génériques est la suivante :

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### Obtention de l’espace disque disponible
Pour afficher l’espace disque et l’espace libre sur les lecteurs locaux, vous pouvez utiliser la classe WMI Win32_LogicalDisk. Vous ne devez voir que les instances dont DriveType a la valeur 3 (valeur que WMI utilise pour les disques durs fixes).

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### Obtention d’informations sur l’ouverture de session
Vous pouvez obtenir des informations générales sur les ouvertures de session associées aux utilisateurs via la classe WMI Win32_LogonSession :

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### Obtention de l’utilisateur connecté à un ordinateur
Vous pouvez afficher l’utilisateur connecté à système informatique particulier à l’aide de la commande Win32_ComputerSystem. Cette commande retourne uniquement l’utilisateur connecté au bureau du système :

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### Obtention de l’heure locale d’un ordinateur
Vous pouvez récupérer l’heure locale actuelle sur un ordinateur spécifique à l’aide de la classe WMI Win32_LocalTime. Cette classe par défaut affichant toutes les métadonnées, il est souhaitable de la filtrer à l’aide de l’applet de commande **Select-Object** :

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### Affichage de l’état du service
Pour afficher l’état de tous les services sur un ordinateur spécifique, vous pouvez utiliser localement l’applet de commande **Get-Service**, comme indiqué précédemment. Pour des systèmes distants, vous pouvez utiliser la classe WMI Win32_Service. Si vous utilisez également l’applet de commande **Select-Object** pour filtrer les résultats pour **Status**, **Name** et **DisplayName**, le format de sortie est quasiment identique à celui de l’applet de commande **Get-Service** :

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Pour permettre l’affichage complet des noms des services occasionnels portant des noms très longs, vous pouvez utiliser l’applet de commande **Format-Table** avec les paramètres **AutoSize** et **Wrap**, pour optimiser la largeur des colonnes et permettre le retour à la ligne plutôt que la troncation des noms longs :

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```



<!--HONumber=Apr16_HO1-->


