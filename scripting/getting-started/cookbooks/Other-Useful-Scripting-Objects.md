---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Autres objets de script utiles
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="3534a-103">Autres objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="3534a-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="3534a-104">Les objets suivants fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3534a-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="3534a-105">Ils ne sont pas inclus dans la hiérarchie **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="3534a-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="3534a-106">Objets de script utiles</span><span class="sxs-lookup"><span data-stu-id="3534a-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="3534a-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="3534a-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="3534a-108">Il existe certaines restrictions sur la façon dont Windows PowerShell ISE interagit avec les applications de console.</span><span class="sxs-lookup"><span data-stu-id="3534a-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="3534a-109">Une commande ou un script d’automatisation qui nécessite l’intervention de l’utilisateur peut ne pas fonctionner de la même façon qu’à partir de la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3534a-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="3534a-110">Vous pouvez empêcher l’exécution de ces commandes ou scripts dans le volet Commande de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3534a-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="3534a-111">L’objet **$psUnsupportedConsoleApplications** conserve la liste de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="3534a-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="3534a-112">Si vous essayez d’exécuter les commandes de cette liste, vous obtenez un message indiquant qu’elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3534a-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="3534a-113">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="3534a-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="3534a-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="3534a-114">$psLocalHelp</span></span>
 <span data-ttu-id="3534a-115">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des rubriques d’aide et leurs liens correspondants dans le fichier d’aide HTML compilé local.</span><span class="sxs-lookup"><span data-stu-id="3534a-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="3534a-116">Il est utilisé pour localiser l’aide locale d’une rubrique particulière.</span><span class="sxs-lookup"><span data-stu-id="3534a-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="3534a-117">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="3534a-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="3534a-118">L’exemple de code suivant illustre certaines paires clé-valeur contenues dans **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="3534a-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="3534a-119">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="3534a-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="3534a-120">Clé : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="3534a-120">Key : Add-Computer</span></span>|<span data-ttu-id="3534a-121">Valeur : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="3534a-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="3534a-122">Clé : Add-Content</span><span class="sxs-lookup"><span data-stu-id="3534a-122">Key : Add-Content</span></span>|<span data-ttu-id="3534a-123">Valeur : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="3534a-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="3534a-124">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="3534a-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="3534a-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="3534a-125">$psOnlineHelp</span></span>
 <span data-ttu-id="3534a-126">Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des titres de rubriques d’aide et leurs URL externes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="3534a-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="3534a-127">Il est utilisé pour localiser l’aide d’une rubrique particulière sur le web.</span><span class="sxs-lookup"><span data-stu-id="3534a-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="3534a-128">Vous pouvez ajouter ou supprimer des rubriques dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="3534a-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="3534a-129">Sortie exemple</span><span class="sxs-lookup"><span data-stu-id="3534a-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="3534a-130">Clé : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="3534a-130">Key : Add-Computer</span></span>|<span data-ttu-id="3534a-131">Valeur : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="3534a-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="3534a-132">Clé : Add-Content</span><span class="sxs-lookup"><span data-stu-id="3534a-132">Key : Add-Content</span></span>|<span data-ttu-id="3534a-133">Valeur : http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="3534a-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="3534a-134">Le script suivant ajoute une entrée à la liste.</span><span class="sxs-lookup"><span data-stu-id="3534a-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="3534a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3534a-135">See Also</span></span>
- [<span data-ttu-id="3534a-136">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3534a-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
