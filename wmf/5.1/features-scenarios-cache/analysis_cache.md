# Cache d’analyse de module #

À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.

Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.

Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement PSModuleAnalysisCachePath avant de démarrer PowerShell. Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.
La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.
Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Cela définit un appareil non valide comme chemin. Aucune erreur si PowerShell ne peut pas écrire dans le chemin, mais vous pouvez observer la présence d’une erreur signalée par le biais du suivi d’erreur :

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.
Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Cette variable d’environnement prend effet immédiatement dans le processus actif.

<!--HONumber=Jul16_HO1-->


