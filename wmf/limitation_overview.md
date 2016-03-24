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
<!--HONumber=Mar16_HO2-->
