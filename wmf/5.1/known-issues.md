---
title: "Problèmes connus dans WMF 5.1 (préversion)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: e2f19ed2fa2d2070860438b128513a463d95adae
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="known-issues-in-wmf-51-preview"></a>Problèmes connus dans WMF 5.1 (préversion) #

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

## <a name="starting-powershell-shortcut-as-administrator"></a>Démarrage de raccourci PowerShell en tant qu’administrateur
Lors de l’installation de WMF, si vous essayez de démarrer PowerShell en tant qu’administrateur à partir du raccourci, vous pouvez obtenir un message « Erreur non spécifiée ».
Rouvrez le raccourci en tant que non administrateur. Le raccourci fonctionnera maintenant même en tant qu’administrateur.

## <a name="pester"></a>Pester
Dans cette version, vous devez savoir qu’il existe deux problèmes quand vous utilisez Pester sur Nano Server :

* L’exécution des tests directement sur Pester peut entraîner des échecs en raison des différences entre la version CLR complète et la version CLR de base. En particulier, la méthode Validate n’est pas disponible sur le type XmlDocument. Six tests qui tentent de valider le schéma des journaux de sortie NUnit échouent systématiquement. 
* Un test de couverture du code échoue, car la ressource DSC *WindowsFeature* n’existe pas dans Nano Server. Toutefois, ces échecs sont généralement sans conséquence et peuvent être ignorés.

## <a name="operation-validation"></a>Validation de l’opération 

* Update-Help échoue pour le module Microsoft.PowerShell.Operation.Validation en raison d’un URI d’aide qui ne fonctionne pas

## <a name="dsc-after-uninstall-wmf"></a>DSC après la désinstallation de WMF 
* La désinstallation de WMF ne supprime pas les documents MOF DSC du dossier de configuration. DSC ne fonctionne pas correctement si les documents MOF contiennent des propriétés récentes qui ne sont pas disponibles sur les anciens systèmes. Dans ce cas, exécutez le script suivant à partir de la console PowerShell avec élévation de privilèges pour nettoyer les états DSC.
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  