# L’applet de commande Test-DscConfiguration prend en charge les configurations de référence

L’applet de commande Test-DscConfiguration a été mise à jour pour autoriser le test de l’état de configuration souhaitée d’un ou plusieurs nœuds cibles en spécifiant un document de configuration de référence à comparer.

Les nouveaux jeux de paramètres suivants utilisent des configurations DSC dans le chemin spécifié uniquement pour tester et jamais pour appliquer chaque configuration sur les nœuds cibles spécifiés. Comme avec Start-DscConfiguration et d’autres applets de commande DSC, le nom de chaque document MOF est utilisé pour déterminer le nœud cible sur lequel tester la configuration. 

```PowerShell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

Les nouveaux jeux de paramètres suivants utilisent une configuration DSC unique seulement pour tester et jamais pour appliquer la configuration sur les nœuds cibles spécifiés. 

```PowerShell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```<!--HONumber=Mar16_HO2-->
