---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: install pswawebapplication
ms.technology: powershell
ms.openlocfilehash: c7f7768a41b6784d8c29afa1fccf0b855160b777
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="218c7-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="218c7-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="218c7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="218c7-104">SYNOPSIS</span></span>

<span data-ttu-id="218c7-105">Configure l’application web Accès Web Windows PowerShell® dans IIS.</span><span class="sxs-lookup"><span data-stu-id="218c7-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="218c7-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="218c7-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="218c7-107">Par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="218c7-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="218c7-108">DESCRIPTION</span></span>

<span data-ttu-id="218c7-109">L’applet de commande **Install-PswaWebApplication** configure l’application web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218c7-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="218c7-110">Cette applet de commande installe l’application web, l’associe à un site web et crée éventuellement un certificat de test SSL à l’aide du paramètre **useTestCertificate**.</span><span class="sxs-lookup"><span data-stu-id="218c7-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="218c7-111">Pour des raisons de sécurité, les administrateurs web ne doivent pas utiliser un certificat de test pour les environnements de production.</span><span class="sxs-lookup"><span data-stu-id="218c7-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="218c7-112">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="218c7-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="218c7-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="218c7-113">-UseTestCertificate</span></span>

<span data-ttu-id="218c7-114">Spécifie qu’un certificat de test est créé.</span><span class="sxs-lookup"><span data-stu-id="218c7-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="218c7-115">Si ce paramètre est défini sur true, cette applet de commande crée un certificat de test et configure l’application web Accès Web Windows PowerShell pour qu’elle utilise le certificat pour les requêtes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="218c7-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="218c7-116">Si ce paramètre est défini sur false, aucun certificat ni aucune liaison ne sont créés.</span><span class="sxs-lookup"><span data-stu-id="218c7-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="218c7-117">Définissez cette valeur sur false si un autre certificat est utilisé pour Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218c7-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="218c7-118">Alias</span><span class="sxs-lookup"><span data-stu-id="218c7-118">Aliases</span></span>                              | <span data-ttu-id="218c7-119">none</span><span class="sxs-lookup"><span data-stu-id="218c7-119">none</span></span>                                 |
| <span data-ttu-id="218c7-120">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="218c7-120">Required?</span></span>                            | <span data-ttu-id="218c7-121">false</span><span class="sxs-lookup"><span data-stu-id="218c7-121">false</span></span>                                |
| <span data-ttu-id="218c7-122">Position ?</span><span class="sxs-lookup"><span data-stu-id="218c7-122">Position?</span></span>                            | <span data-ttu-id="218c7-123">nommé</span><span class="sxs-lookup"><span data-stu-id="218c7-123">named</span></span>                                |
| <span data-ttu-id="218c7-124">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-124">Default Value</span></span>                        | <span data-ttu-id="218c7-125">true</span><span class="sxs-lookup"><span data-stu-id="218c7-125">true</span></span>                                 |
| <span data-ttu-id="218c7-126">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="218c7-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="218c7-127">false</span><span class="sxs-lookup"><span data-stu-id="218c7-127">false</span></span>                                |
| <span data-ttu-id="218c7-128">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="218c7-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="218c7-129">false</span><span class="sxs-lookup"><span data-stu-id="218c7-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="218c7-130">-WebApplicationName&lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="218c7-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="218c7-131">Spécifie le nom de votre application web.</span><span class="sxs-lookup"><span data-stu-id="218c7-131">Specifies the name for your web application.</span></span> <span data-ttu-id="218c7-132">Il constitue la dernière partie de l’URL d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218c7-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="218c7-133">Alias</span><span class="sxs-lookup"><span data-stu-id="218c7-133">Aliases</span></span>                              | <span data-ttu-id="218c7-134">none</span><span class="sxs-lookup"><span data-stu-id="218c7-134">none</span></span>                                 |
| <span data-ttu-id="218c7-135">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="218c7-135">Required?</span></span>                            | <span data-ttu-id="218c7-136">false</span><span class="sxs-lookup"><span data-stu-id="218c7-136">false</span></span>                                |
| <span data-ttu-id="218c7-137">Position ?</span><span class="sxs-lookup"><span data-stu-id="218c7-137">Position?</span></span>                            | <span data-ttu-id="218c7-138">1</span><span class="sxs-lookup"><span data-stu-id="218c7-138">1</span></span>                                    |
| <span data-ttu-id="218c7-139">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-139">Default Value</span></span>                        | <span data-ttu-id="218c7-140">pswa</span><span class="sxs-lookup"><span data-stu-id="218c7-140">pswa</span></span>                                 |
| <span data-ttu-id="218c7-141">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="218c7-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="218c7-142">false</span><span class="sxs-lookup"><span data-stu-id="218c7-142">false</span></span>                                |
| <span data-ttu-id="218c7-143">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="218c7-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="218c7-144">false</span><span class="sxs-lookup"><span data-stu-id="218c7-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="218c7-145">-WebSiteName&lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="218c7-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="218c7-146">Spécifie le nom du site web du serveur Web IIS sur lequel installer cette application web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218c7-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="218c7-147">Alias</span><span class="sxs-lookup"><span data-stu-id="218c7-147">Aliases</span></span>                              | <span data-ttu-id="218c7-148">none</span><span class="sxs-lookup"><span data-stu-id="218c7-148">none</span></span>                                 |
| <span data-ttu-id="218c7-149">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="218c7-149">Required?</span></span>                            | <span data-ttu-id="218c7-150">false</span><span class="sxs-lookup"><span data-stu-id="218c7-150">false</span></span>                                |
| <span data-ttu-id="218c7-151">Position ?</span><span class="sxs-lookup"><span data-stu-id="218c7-151">Position?</span></span>                            | <span data-ttu-id="218c7-152">nommé</span><span class="sxs-lookup"><span data-stu-id="218c7-152">named</span></span>                                |
| <span data-ttu-id="218c7-153">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-153">Default Value</span></span>                        | <span data-ttu-id="218c7-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="218c7-154">Default Web Site</span></span>                     |
| <span data-ttu-id="218c7-155">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="218c7-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="218c7-156">false</span><span class="sxs-lookup"><span data-stu-id="218c7-156">false</span></span>                                |
| <span data-ttu-id="218c7-157">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="218c7-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="218c7-158">false</span><span class="sxs-lookup"><span data-stu-id="218c7-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="218c7-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="218c7-159">-Confirm</span></span>

<span data-ttu-id="218c7-160">Votre confirmation sera requise avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="218c7-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="218c7-161">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="218c7-161">Required?</span></span>                            | <span data-ttu-id="218c7-162">false</span><span class="sxs-lookup"><span data-stu-id="218c7-162">false</span></span>                                |
| <span data-ttu-id="218c7-163">Position ?</span><span class="sxs-lookup"><span data-stu-id="218c7-163">Position?</span></span>                            | <span data-ttu-id="218c7-164">nommé</span><span class="sxs-lookup"><span data-stu-id="218c7-164">named</span></span>                                |
| <span data-ttu-id="218c7-165">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-165">Default Value</span></span>                        | <span data-ttu-id="218c7-166">false</span><span class="sxs-lookup"><span data-stu-id="218c7-166">false</span></span>                                |
| <span data-ttu-id="218c7-167">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="218c7-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="218c7-168">false</span><span class="sxs-lookup"><span data-stu-id="218c7-168">false</span></span>                                |
| <span data-ttu-id="218c7-169">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="218c7-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="218c7-170">false</span><span class="sxs-lookup"><span data-stu-id="218c7-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="218c7-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="218c7-171">-WhatIf</span></span>

<span data-ttu-id="218c7-172">Présente les conséquences éventuelles de l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="218c7-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="218c7-173">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="218c7-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="218c7-174">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="218c7-174">Required?</span></span>                            | <span data-ttu-id="218c7-175">false</span><span class="sxs-lookup"><span data-stu-id="218c7-175">false</span></span>                                |
| <span data-ttu-id="218c7-176">Position ?</span><span class="sxs-lookup"><span data-stu-id="218c7-176">Position?</span></span>                            | <span data-ttu-id="218c7-177">nommé</span><span class="sxs-lookup"><span data-stu-id="218c7-177">named</span></span>                                |
| <span data-ttu-id="218c7-178">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="218c7-178">Default Value</span></span>                        | <span data-ttu-id="218c7-179">false</span><span class="sxs-lookup"><span data-stu-id="218c7-179">false</span></span>                                |
| <span data-ttu-id="218c7-180">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="218c7-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="218c7-181">false</span><span class="sxs-lookup"><span data-stu-id="218c7-181">false</span></span>                                |
| <span data-ttu-id="218c7-182">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="218c7-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="218c7-183">false</span><span class="sxs-lookup"><span data-stu-id="218c7-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="218c7-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="218c7-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="218c7-185">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="218c7-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="218c7-186">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="218c7-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="218c7-187">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="218c7-187">INPUTS</span></span>

<span data-ttu-id="218c7-188">Cette applet de commande ne prend pas d’entrée.</span><span class="sxs-lookup"><span data-stu-id="218c7-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="218c7-189">SORTIES</span><span class="sxs-lookup"><span data-stu-id="218c7-189">OUTPUTS</span></span>

<span data-ttu-id="218c7-190">Cette applet de commande ne produit pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="218c7-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="218c7-191">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="218c7-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="218c7-192">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="218c7-192">EXAMPLE 1</span></span>

<span data-ttu-id="218c7-193">Cet exemple installe l’application web PSWA en utilisant les valeurs par défaut pour les paramètres **WebApplicationName** (*pswa*) et **WebSiteName** (*Default Web Site*).</span><span class="sxs-lookup"><span data-stu-id="218c7-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="218c7-194">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="218c7-194">EXAMPLE 2</span></span>

<span data-ttu-id="218c7-195">Cet exemple installe l’application web PSWA avec un certificat de test, en utilisant les valeurs par défaut pour les paramètres **WebApplicationName** et **WebSiteName**.</span><span class="sxs-lookup"><span data-stu-id="218c7-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="218c7-196">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="218c7-196">Related topics</span></span>

- [<span data-ttu-id="218c7-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="218c7-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="218c7-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="218c7-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="218c7-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="218c7-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="218c7-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="218c7-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)