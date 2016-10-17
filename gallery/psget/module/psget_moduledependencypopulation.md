# Logique pour la préparation des dépendances de module au cours de l’opération de publication
1.  Les modules répertoriés dans le cadre de RequiredModules sont considérés comme des dépendances.
2.  Les modules répertoriés dans le cadre de NestedModules, dont la base de modules n’est pas sous la base de modules spécifiée, sont considérés comme des dépendances.

3.  Les dépendances ci-dessus doivent être disponibles dans le même référentiel cible, sinon l’opération de publication entraîne une erreur.
    Par exemple, si 'SnippetPx' n’est pas disponible dans le référentiel, l’erreur ci-dessous est générée.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Certaines dépendances de module peuvent être gérées en externe, auquel cas elles doivent être ajoutées à l’entrée ExternalModuleDependencies dans la section PSData du manifeste du module.
    Partie inférieure du message d’erreur ci-dessus
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Pendant l’installation du module, la liste des dépendances préparée ci-dessus est utilisée pour installer les dépendances.*

*Vérifiez que les dépendances de votre module sont disponibles sous $env:PSModulePath sur votre système lors de l’opération de publication.*


<!--HONumber=Aug16_HO3-->


