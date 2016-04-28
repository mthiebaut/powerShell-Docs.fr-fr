# Configuration requise

- Installez les dernières mises à jour de Windows avant d’installer WMF 5.0 RTM.
- Vous pouvez installer WMF 5.0 RTM uniquement sur les systèmes d’exploitation suivants :

    | Système d’exploitation       | Éditions         | Conditions préalables        |  Liens de packages |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2012    |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717506)">W2K12-KB3134759-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2008 R2 SP1 | Toutes sauf IA64 | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> et <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou version supérieure</ctype="x-NOTFOUND"> sont installés| <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">|
    | Windows 8.1 | Professionnel, Enterprise | | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64 :</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86 :</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717963)">Win8.1-KB3134758-x86.msu</ctype="x-NOTFOUND">|
    | Windows 7 SP1 | Toutes | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> et <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou version supérieure</ctype="x-NOTFOUND"> sont installés| <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64 :</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">  </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86 :</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717962)">Win7-KB3134760-x86.msu</ctype="x-NOTFOUND">|

# Instructions d’installation

### Pour installer WMF 5.0 à partir de l’Explorateur Windows (ou de l’Explorateur de fichiers)

1. Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.

2. Double-cliquez sur le fichier MSU pour l’exécuter.

### Pour installer WMF 5.0 à partir de l’invite de commandes

1. Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur). Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.

2. Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.0.

3. Exécutez l’une des commandes suivantes :
    - Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1AndW2K12R2-KB3134758-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Sur les ordinateurs qui exécutent Windows Server 2012, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">W2K12-KB3134759-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Sur les ordinateurs qui exécutent Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7AndW2K8R2-KB3134760-x64.msu /quiet</ctype="x-NOTFOUND">.
    - Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1-KB3134758-x86.msu /quiet</ctype="x-NOTFOUND">.
    - Sur les ordinateurs qui exécutent Windows 7 SP1 x86, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7-KB3134760-x86.msu /quiet</ctype="x-NOTFOUND">.

### Notes d’installation supplémentaires pour Windows Server 2008 R2 SP1 et Windows 7 SP1 :

Vérifiez que les conditions préalables suivantes sont remplies :
- Le Service Pack le plus récent est installé.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> est installé.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 ou version ultérieure</ctype="x-NOTFOUND"> est installé.

**Dépendance de WMF 4.0**

Les systèmes Windows Server 2008 R2 SP1 et Windows 7 SP1 ont intégré PowerShell 2.0, WinRM et WMI. Les packages WMF 3.0 et WMF 4.0, qui mettent à jour ces composants intégrés, ont été publiés après la sortie de Windows Server 2008 R2 SP1 et Windows 7 SP1. L’installation et la désinstallation des packages WMF 3.0 et WMF 4.0 ont révélé des problèmes dans le chemin de mise à niveau suivant :

- Intégré --> WMF 4.0
- Intégré --> WMF 3.0 --> WMF4.0. 

Nous avons résolu tous ces problèmes dans les packages WMF 4.0. Par conséquent, WMF 4.0 est nécessaire pour installer WMF 5.0 sur Windows Server 2008 R2 SP1 et Windows 7 SP1. Voici les problèmes spécifiques que vous pouvez rencontrer si vous n’installez pas WMF 4.0 avant la mise à niveau vers WMF 5.0 :

- Le journal des événements transférés n’est pas disponible et le journal EventCollector n’apparaît pas dans l’Observateur d’événements après la désinstallation de WMF 3.0 ou WMF 5.0 (si WMF 4.0 n’est pas installé) dans Windows 7 SP1 et Windows Server 2008 R2 SP1 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2809215)">KB2809215</ctype="x-NOTFOUND">).
- La personnalisation de la variable d’environnement <ctype="x-NOTFOUND" mdpre="*" mdpost="*">PSModulePath</ctype="x-NOTFOUND"> est réinitialisée à sa valeur par défaut quand vous effectuez la mise à niveau directement de PowerShell 2.0 intégré vers WMF 5.0 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872035)">KB2872035</ctype="x-NOTFOUND">) ou de WMF 3.0 vers WMF 5.0. (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872047)">KB2872047</ctype="x-NOTFOUND">) dans Windows 7 SP1 et Windows Server 2008 R2 SP1.

**Dépendance de WinRM**

La Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 SP1 et Windows 7 SP1. Pour activer WinRM, dans une session Windows PowerShell avec élévation des privilèges, exécutez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Set-WSManQuickConfig</ctype="x-NOTFOUND">.

# Instructions de désinstallation

### Utilisation de l’invite de commandes

1.  Ouvrez l’<ctype="x-NOTFOUND" mdpre="**" mdpost="**">invite de commandes</ctype="x-NOTFOUND">.

2.  Exécutez le <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/934307)">Lanceur autonome Windows Update</ctype="x-NOTFOUND"> comme indiqué ci-dessous :

Sur Windows Server 2012 R2 et Windows 8.1 :
```powershell
wusa /uninstall /kb:3134758
```
Sur Windows Server 2012 :
```powershell
wusa /uninstall /kb:3134759
```
Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :
```powershell
wusa /uninstall /kb:3134760
```

### Utilisation du Panneau de configuration

1.  Ouvrez le <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Panneau de configuration</ctype="x-NOTFOUND">.

2.  Ouvrez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Programmes</ctype="x-NOTFOUND">, puis <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Désinstaller un programme</ctype="x-NOTFOUND">.

3.  Cliquez sur <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Afficher les mises à jour installées</ctype="x-NOTFOUND">.

4.  Sélectionnez <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Windows Management Framework 5.0</ctype="x-NOTFOUND"> dans la liste des mises à jour installées. Cela correspond à <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134758</ctype="x-NOTFOUND">, <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134759</ctype="x-NOTFOUND"> ou <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134760</ctype="x-NOTFOUND">. Cliquez sur <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Désinstaller</ctype="x-NOTFOUND">.


<!--HONumber=Mar16_HO4-->


