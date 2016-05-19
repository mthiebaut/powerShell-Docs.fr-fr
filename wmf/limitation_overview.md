# Limitations et problèmes connus

Les raccourcis PowerShell sont rompus lors de la première utilisation
------------------------------------------------------------

**Résolution :** Effectuez l’une des opérations suivantes :

1.  Cliquez avec le bouton droit sur le raccourci PowerShell. Sélectionnez « Windows PowerShell » pour le démarrer sans autorisations élevées.
2.  Cliquez avec le bouton droit sur le raccourci PowerShell. Cliquez avec le bouton droit sur « Windows PowerShell » et sélectionnez « Exécuter en tant qu’administrateur » pour le démarrer en mode élevé.

Les raccourcis PowerShell fonctionneront une fois que vous aurez effectué l’une des actions ci-dessus. Vous ne devez effectuer ces actions qu’une seule fois.


Les modules PowerShell et les ressources DSC signalent des erreurs concernant ExecutionPolicy sur Windows 7
-------------------------------------------------------------------------------------
Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.

**Résolution :** Affectez la valeur RemoteSigned à ExecutionPolicy en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Set-ExecutionPolicy RemoteSigned
```

La connexion à un ancien point de terminaison Exchange distant provoque un blocage
------------------------------------------------------------

L’ancien point de terminaison Exchange redirige vers un nouveau point de terminaison. Un bogue dans la logique de redirection provoque un blocage.

**Résolution :** Connectez-vous directement au nouveau point de terminaison.


La fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation de WMF 5.0 sur Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Quand vous installez WMF 5.0 sur un ordinateur Windows Server 2012 R2 qui exécute déjà SIL, la fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation.

**Résolution :** Exécutez l’applet de commande Start-SilLogging une fois après l’installation de WMF, car le processus d’installation arrête la fonctionnalité de journalisation de l’inventaire logiciel de façon non contrôlée.

Get-ChildItem ne fonctionne pas si -LiteralPath et -Recurse sont utilisés ensemble
--------------------------------------------------------------------------

Si un nom de répertoire contient un caractère non valide, Get-ChildItem ne génère pas les résultats attendus quand
-LiteralPath et -Recurse sont utilisés ensemble.

**Résolution :** La solution de contournement actuelle, qui n’est pas idéale, consiste à implémenter la récursivité dans le script plutôt que de se fier à l’applet de commande.


Sysprep échoue après l’installation de WMF 5.0
----------------------------------------

Il existe deux solutions de contournement pour résoudre ce problème, selon la version de Windows Server que vous exécutez.

**Résolution :**
- Pour les systèmes exécutant **Windows Server 2008 R2**
  1.    Ouvrez PowerShell en tant qu’administrateur.
  2.    Exécutez la commande suivante :
   ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
   ```
  3.    Exécutez la commande et ignorez les erreurs, qui sont normales.
   ```powershell
    Publish-SilData
   ```
  4.    Supprimez les fichiers du répertoire \Windows\System32\Logfiles\SIL\.
  ```powershell
  Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5.    Installez toutes les mises à jour Windows importantes disponibles et lancez l’opération Sysprep normalement.
  
- Pour les systèmes exécutant **Windows Server 2012**
  1.    Après l’installation de WMF 5.0 sur le serveur sur lequel exécuter Sysprep, connectez-vous en tant qu’administrateur.
  2.    Copiez Generize.xml à partir du répertoire \Windows\System32\Sysprep\ActionFiles\ vers un emplacement en dehors du répertoire Windows, C:\ par exemple.
  3.    Ouvrez votre copie de Generalize.xml avec le Bloc-notes.
  4.    Recherchez et supprimez les lignes suivantes. Une instance de chaque doit être supprimée (elles se trouvent vers la fin du document).
    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```
  5.    Enregistrez la copie modifiée de Generalize.xml et fermez le fichier.
  6.    Ouvrez une invite de commandes en tant qu’administrateur.
  7.    Exécutez la commande suivante pour prendre possession du fichier Generalize.xml dans le dossier system32 :
    ```
      Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
  8.    Exécutez la commande suivante pour définir l’autorisation appropriée sur le fichier :
    ```
      Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * Répondez Oui à l’invite de confirmation. 
      * Notez que `<AdministratorUserName>` doit être remplacé par le nom d’utilisateur qui est administrateur sur l’ordinateur. Par exemple, « Administrateur ».
      
  9.    Copiez le fichier que vous avez modifié et enregistré dans le répertoire Sysprep à l’aide de la commande suivante :
      ```
      xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
      ```
      * Répondez Oui pour remplacer (vérifiez le chemin entré en l’absence d’invite de remplacement).
      * Cette commande suppose que votre copie modifiée de Generalize.xml a été copiée dans C:\.
  10.   Generalize.XML est désormais mis à jour grâce à la solution de contournement. Exécutez Sysprep avec l’option generalize activée.



<!--HONumber=May16_HO1-->


