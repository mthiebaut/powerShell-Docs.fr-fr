---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Présentation de Windows PowerShell ISE"
ms.openlocfilehash: 75242c20548e2e83397867214417a48806c897ec
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="087bc-103">Présentation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="087bc-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="087bc-104">Windows PowerShell Integrated Scripting Environment (ISE) est une application hôte pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="087bc-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="087bc-105">Dans Windows PowerShell ISE, vous pouvez exécuter des commandes et écrire, tester et déboguer des scripts dans une seule et même interface utilisateur graphique Windows. Celle-ci prend en charge des fonctions d’édition multiligne, la saisie semi-automatique par tabulation, la coloration de la syntaxe, l’exécution sélective, l’aide contextuelle et les langues s’écrivant de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="087bc-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="087bc-106">Des éléments de menu et des raccourcis clavier vous permettent d’effectuer une grande partie des tâches accessibles à partir de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="087bc-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="087bc-107">Par exemple, pour définir un point d’arrêt de ligne dans un script que vous déboguez dans Windows PowerShell ISE, cliquez avec le bouton droit sur la ligne de code, puis cliquez sur **Basculer le point d’arrêt**.</span><span class="sxs-lookup"><span data-stu-id="087bc-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="087bc-108">Essayez ces fonctionnalités dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="087bc-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="087bc-109">Édition multiligne : pour insérer une ligne vide sous la ligne actuelle dans le volet Commande, appuyez sur Maj+Entrée.</span><span class="sxs-lookup"><span data-stu-id="087bc-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

- <span data-ttu-id="087bc-110">Exécution sélective : pour exécuter une partie d’un script, sélectionnez le texte à exécuter, puis cliquez sur le bouton **Exécuter le script**.</span><span class="sxs-lookup"><span data-stu-id="087bc-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="087bc-111">Ou bien, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="087bc-111">Or, press F5.</span></span>

- <span data-ttu-id="087bc-112">Aide contextuelle : tapez **Invoke-Item**, puis appuyez sur F1.</span><span class="sxs-lookup"><span data-stu-id="087bc-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="087bc-113">Le fichier d’aide s’ouvre à la rubrique d’aide de l’applet de commande **Invoke-Item**.</span><span class="sxs-lookup"><span data-stu-id="087bc-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="087bc-114">Windows PowerShell ISE permet de personnaliser certains aspects de son apparence.</span><span class="sxs-lookup"><span data-stu-id="087bc-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="087bc-115">Il possède également son propre profil Windows PowerShell dans lequel vous pouvez stocker les fonctions, alias, variables et commandes que vous utilisez dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="087bc-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="087bc-116">Pour démarrer Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="087bc-116">To start the Windows PowerShell ISE</span></span>

1. <span data-ttu-id="087bc-117">Effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="087bc-117">Do one of the following:</span></span>

    -   <span data-ttu-id="087bc-118">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Windows PowerShell V2**, puis cliquez sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="087bc-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="087bc-119">Dans l’interface Cmd.exe de la console Windows PowerShell ou dans la zone Exécuter, tapez **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="087bc-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="087bc-120">Pour obtenir de l'aide dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="087bc-120">To get Help in the Windows PowerShell ISE</span></span>

- <span data-ttu-id="087bc-121">Dans le menu **Aide**, cliquez sur **Aide Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="087bc-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="087bc-122">Ou bien, appuyez sur F1.</span><span class="sxs-lookup"><span data-stu-id="087bc-122">Or, press F1.</span></span> <span data-ttu-id="087bc-123">Le fichier qui s'ouvre décrit Windows PowerShell ISE et Windows PowerShell. Il comprend aussi l'intégralité de l'aide disponible à partir de l'applet de commande Get-Help.</span><span class="sxs-lookup"><span data-stu-id="087bc-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

