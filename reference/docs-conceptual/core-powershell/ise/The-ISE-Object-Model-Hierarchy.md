---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Hiérarchie du modèle objet ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>Hiérarchie du modèle objet ISE
Cette rubrique présente la hiérarchie des objets qui font partie de l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE). Windows PowerShell ISE est inclus dans Windows PowerShell 3.0 et Windows PowerShell 4.0. Cliquez sur un objet pour accéder à la documentation de référence de la classe qui définit l’objet.

## <a name="psise-object"></a>Objet $psISE

L’objet **$psISE** est l’[objet racine](The-ObjectModelRoot-Object.md) de la hiérarchie d’objets Windows PowerShell ISE.
Cet objet de premier niveau fournit les objets de script suivants :

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

L’objet **$psISE.CurrentFile** est une instance de la classe [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

L’objet **$psISE.CurrentPowerShellTab** est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord supérieur de la fenêtre Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord droit de la fenêtre Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

L’objet **$psISE.Options** est une instance de la classe [ISEOptions](The-ISEOptions-Object.md).
L’objet ISEOptions représente différents paramètres pour Windows PowerShell ISE.
Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

L’objet **$psISE.PowerShellTabs** est une instance de la classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).
Cet objet est une collection de tous les onglets PowerShell ouverts qui représentent les environnements d’exécution Windows PowerShell disponibles sur l’ordinateur local ou sur les ordinateurs distants connectés. Chaque membre de la collection est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Voir aussi
- [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Informations de référence sur le modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
