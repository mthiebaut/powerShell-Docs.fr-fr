---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Démarrage de la version 32 bits de Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="24ce3-103">Démarrage de la Version 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24ce3-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="24ce3-104">Quand vous installez Windows PowerShell sur un ordinateur 64 bits, **Windows PowerShell (x86)**, version 32 bits de Windows PowerShell, est installé en plus de la version 64 bits.</span><span class="sxs-lookup"><span data-stu-id="24ce3-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="24ce3-105">Quand vous exécutez Windows PowerShell, la version 64 bits s’exécute par défaut.</span><span class="sxs-lookup"><span data-stu-id="24ce3-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="24ce3-106">Toutefois, il se peut que vous deviez occasionnellement exécuter **Windows PowerShell (x86)**, par exemple, lorsque vous utilisez un module nécessitant la version 32 bits ou lorsque vous vous connectez à distance à un ordinateur 32 bits.</span><span class="sxs-lookup"><span data-stu-id="24ce3-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="24ce3-107">Pour démarrer une version 32 bits de Windows PowerShell, procédez de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="24ce3-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="24ce3-108">Dans Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="24ce3-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="24ce3-109">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="24ce3-110">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="24ce3-111">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-112">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-113">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="24ce3-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="24ce3-114">Dans Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="24ce3-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="24ce3-115">Dans l’écran **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-116">Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-117">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **recherche**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-118">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="24ce3-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="24ce3-119">Dans Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="24ce3-119">In Windows® 8.1</span></span>

- <span data-ttu-id="24ce3-120">Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="24ce3-121">Cliquez sur la vignette **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="24ce3-122">Si vous exécutez les [Outils d’Administration de serveur distant](http://go.microsoft.com/fwlink/?LinkID=304145) pour Windows 8.1, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="24ce3-123">Sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-124">Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="24ce3-125">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="24ce3-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="24ce3-126">Dans Windows® 8</span><span class="sxs-lookup"><span data-stu-id="24ce3-126">In Windows® 8</span></span>

- <span data-ttu-id="24ce3-127">Dans l’écran **Démarrer**, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Paramètres**, **Vignettes**, puis positionnez le curseur **Afficher les outils d’administration** sur Oui.</span><span class="sxs-lookup"><span data-stu-id="24ce3-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="24ce3-128">Ensuite, tapez **PowerShell** puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-129">Si vous exécutez les [Outils d’Administration de serveur distant](http://www.microsoft.com/download/details.aspx?id=28972) pour Windows 8, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="24ce3-130">Sélectionnez **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-131">Dans l’écran **Démarrer** ou sur le Bureau, tapez **PowerShell (x86)**, puis cliquez sur **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="24ce3-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="24ce3-132">Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="24ce3-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

