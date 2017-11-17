---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="3b61d-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="3b61d-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b61d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3b61d-104">SYNOPSIS</span></span>

<span data-ttu-id="3b61d-105">Désinstalle l’application Accès Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="3b61d-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b61d-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3b61d-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="3b61d-107">Par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="3b61d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3b61d-108">DESCRIPTION</span></span>

<span data-ttu-id="3b61d-109">L’applet de commande **Uninstall-PswaWebApplication** désinstalle l’application web Windows PowerShell et supprime le site web d’IIS.</span><span class="sxs-lookup"><span data-stu-id="3b61d-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="3b61d-110">L’applet de commande ne désinstalle pas IIS ni d’autres fonctionnalités installées car elles étaient nécessaires à l’exécution de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b61d-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="3b61d-111">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="3b61d-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="3b61d-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="3b61d-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="3b61d-113">Indique que le certificat de test créé par l’applet de commande **Install\_PswaWebApplication** (avec le paramètre **UseTestCertificate**) est supprimé.</span><span class="sxs-lookup"><span data-stu-id="3b61d-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="3b61d-114">Seul le certificat de test avec le même nom que celui créé par l’applet de commande **Install-PswaWebApplication** est supprimé.</span><span class="sxs-lookup"><span data-stu-id="3b61d-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b61d-115">Alias</span><span class="sxs-lookup"><span data-stu-id="3b61d-115">Aliases</span></span>                              | <span data-ttu-id="3b61d-116">none</span><span class="sxs-lookup"><span data-stu-id="3b61d-116">none</span></span>                                 |
| <span data-ttu-id="3b61d-117">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-117">Required?</span></span>                            | <span data-ttu-id="3b61d-118">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-118">false</span></span>                                |
| <span data-ttu-id="3b61d-119">Position ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-119">Position?</span></span>                            | <span data-ttu-id="3b61d-120">nommé</span><span class="sxs-lookup"><span data-stu-id="3b61d-120">named</span></span>                                |
| <span data-ttu-id="3b61d-121">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-121">Default Value</span></span>                        | <span data-ttu-id="3b61d-122">true</span><span class="sxs-lookup"><span data-stu-id="3b61d-122">true</span></span>                                 |
| <span data-ttu-id="3b61d-123">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b61d-124">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-124">false</span></span>                                |
| <span data-ttu-id="3b61d-125">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b61d-126">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="3b61d-127">-WebApplicationName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="3b61d-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="3b61d-128">Spécifie le nom de l’application web à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="3b61d-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b61d-129">Alias</span><span class="sxs-lookup"><span data-stu-id="3b61d-129">Aliases</span></span>                              | <span data-ttu-id="3b61d-130">none</span><span class="sxs-lookup"><span data-stu-id="3b61d-130">none</span></span>                                 |
| <span data-ttu-id="3b61d-131">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-131">Required?</span></span>                            | <span data-ttu-id="3b61d-132">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-132">false</span></span>                                |
| <span data-ttu-id="3b61d-133">Position ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-133">Position?</span></span>                            | <span data-ttu-id="3b61d-134">1</span><span class="sxs-lookup"><span data-stu-id="3b61d-134">1</span></span>                                    |
| <span data-ttu-id="3b61d-135">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-135">Default Value</span></span>                        | <span data-ttu-id="3b61d-136">pswa</span><span class="sxs-lookup"><span data-stu-id="3b61d-136">pswa</span></span>                                 |
| <span data-ttu-id="3b61d-137">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b61d-138">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-138">false</span></span>                                |
| <span data-ttu-id="3b61d-139">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b61d-140">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="3b61d-141">-WebSiteName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="3b61d-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="3b61d-142">Spécifie le nom du site web où l’application web est installée.</span><span class="sxs-lookup"><span data-stu-id="3b61d-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b61d-143">Alias</span><span class="sxs-lookup"><span data-stu-id="3b61d-143">Aliases</span></span>                              | <span data-ttu-id="3b61d-144">none</span><span class="sxs-lookup"><span data-stu-id="3b61d-144">none</span></span>                                 |
| <span data-ttu-id="3b61d-145">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-145">Required?</span></span>                            | <span data-ttu-id="3b61d-146">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-146">false</span></span>                                |
| <span data-ttu-id="3b61d-147">Position ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-147">Position?</span></span>                            | <span data-ttu-id="3b61d-148">nommé</span><span class="sxs-lookup"><span data-stu-id="3b61d-148">named</span></span>                                |
| <span data-ttu-id="3b61d-149">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-149">Default Value</span></span>                        | <span data-ttu-id="3b61d-150">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="3b61d-150">Default Web Site</span></span>                     |
| <span data-ttu-id="3b61d-151">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b61d-152">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-152">false</span></span>                                |
| <span data-ttu-id="3b61d-153">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b61d-154">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="3b61d-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3b61d-155">-Confirm</span></span>

<span data-ttu-id="3b61d-156">Votre confirmation sera requise avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3b61d-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b61d-157">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-157">Required?</span></span>                            | <span data-ttu-id="3b61d-158">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-158">false</span></span>                                |
| <span data-ttu-id="3b61d-159">Position ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-159">Position?</span></span>                            | <span data-ttu-id="3b61d-160">nommé</span><span class="sxs-lookup"><span data-stu-id="3b61d-160">named</span></span>                                |
| <span data-ttu-id="3b61d-161">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-161">Default Value</span></span>                        | <span data-ttu-id="3b61d-162">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-162">false</span></span>                                |
| <span data-ttu-id="3b61d-163">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b61d-164">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-164">false</span></span>                                |
| <span data-ttu-id="3b61d-165">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b61d-166">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="3b61d-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3b61d-167">-WhatIf</span></span>

<span data-ttu-id="3b61d-168">Présente les conséquences éventuelles de l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3b61d-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3b61d-169">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="3b61d-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b61d-170">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-170">Required?</span></span>                            | <span data-ttu-id="3b61d-171">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-171">false</span></span>                                |
| <span data-ttu-id="3b61d-172">Position ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-172">Position?</span></span>                            | <span data-ttu-id="3b61d-173">nommé</span><span class="sxs-lookup"><span data-stu-id="3b61d-173">named</span></span>                                |
| <span data-ttu-id="3b61d-174">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3b61d-174">Default Value</span></span>                        | <span data-ttu-id="3b61d-175">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-175">false</span></span>                                |
| <span data-ttu-id="3b61d-176">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b61d-177">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-177">false</span></span>                                |
| <span data-ttu-id="3b61d-178">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3b61d-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b61d-179">false</span><span class="sxs-lookup"><span data-stu-id="3b61d-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="3b61d-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="3b61d-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="3b61d-181">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="3b61d-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="3b61d-182">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3b61d-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="3b61d-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3b61d-183">INPUTS</span></span>

<span data-ttu-id="3b61d-184">Cette applet de commande ne prend pas d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3b61d-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="3b61d-185">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3b61d-185">OUTPUTS</span></span>

<span data-ttu-id="3b61d-186">Cette applet de commande ne retourne pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="3b61d-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="3b61d-187">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3b61d-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="3b61d-188">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="3b61d-188">EXAMPLE 1</span></span>

<span data-ttu-id="3b61d-189">Cette commande désinstalle l’application web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b61d-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="3b61d-190">Vous pouvez utiliser cette applet de commande pour désinstaller l’application web Windows PowerShell si vous l’avez installée en utilisant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="3b61d-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="3b61d-191">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="3b61d-191">EXAMPLE 2</span></span>

<span data-ttu-id="3b61d-192">Cette commande désinstalle l’application web Windows PowerShell et supprime le certificat de test associé à l’application.</span><span class="sxs-lookup"><span data-stu-id="3b61d-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="3b61d-193">Vous pouvez utiliser cette applet de commande pour désinstaller l’application web Windows PowerShell si vous l’avez installée en utilisant les valeurs par défaut et que vous avez créé un certificat de test.</span><span class="sxs-lookup"><span data-stu-id="3b61d-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="3b61d-194">EXEMPLE 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="3b61d-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="3b61d-195">Cette commande désinstalle l’application web Windows PowerShell quand un site web personnalisé et une application ont été spécifiés lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="3b61d-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="3b61d-196">La commande supprime le site Web nommé *MySite* et l’application nommée *TestApplication*, et spécifie que les certificats de test associés à l’application sont également supprimés.</span><span class="sxs-lookup"><span data-stu-id="3b61d-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="3b61d-197">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3b61d-197">Related topics</span></span>

- [<span data-ttu-id="3b61d-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b61d-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="3b61d-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b61d-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="3b61d-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="3b61d-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="3b61d-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b61d-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="3b61d-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b61d-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
