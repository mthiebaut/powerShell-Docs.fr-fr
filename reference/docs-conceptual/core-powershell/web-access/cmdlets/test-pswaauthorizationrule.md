---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="3421d-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3421d-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="3421d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3421d-104">SYNOPSIS</span></span>

<span data-ttu-id="3421d-105">Vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="3421d-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="3421d-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="3421d-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="3421d-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="3421d-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="3421d-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="3421d-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="3421d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3421d-109">DESCRIPTION</span></span>

<span data-ttu-id="3421d-110">L’applet de commande **Test-PswaAuthorizationRule** vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="3421d-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="3421d-111">Cette applet de commande peut également être utilisé pour tester les règles d’autorisation, ou pour vérifier qu’une demande d’accès d’un utilisateur, d’un ordinateur ou d’un point de terminaison particulier est autorisée.</span><span class="sxs-lookup"><span data-stu-id="3421d-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="3421d-112">Par défaut, cette applet de commande évalue toutes les règles du fichier d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="3421d-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="3421d-113">Vous pouvez cependant spécifier un sous-ensemble de règles à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="3421d-114">Vous pouvez utiliser cette applet de commande pour résoudre les problèmes liés aux échecs d’authentification.</span><span class="sxs-lookup"><span data-stu-id="3421d-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="3421d-115">Les paramètres de cette applet de commande correspondent aux champs de la page de connexion d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="3421d-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="3421d-116">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="3421d-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="3421d-117">-ComputerName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="3421d-118">Spécifie le nom de l’ordinateur à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-119">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-119">Aliases</span></span>                              | <span data-ttu-id="3421d-120">none</span><span class="sxs-lookup"><span data-stu-id="3421d-120">none</span></span>                                 |
| <span data-ttu-id="3421d-121">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-121">Required?</span></span>                            | <span data-ttu-id="3421d-122">true</span><span class="sxs-lookup"><span data-stu-id="3421d-122">true</span></span>                                 |
| <span data-ttu-id="3421d-123">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-123">Position?</span></span>                            | <span data-ttu-id="3421d-124">2</span><span class="sxs-lookup"><span data-stu-id="3421d-124">2</span></span>                                    |
| <span data-ttu-id="3421d-125">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-125">Default Value</span></span>                        | <span data-ttu-id="3421d-126">none</span><span class="sxs-lookup"><span data-stu-id="3421d-126">none</span></span>                                 |
| <span data-ttu-id="3421d-127">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-128">false</span><span class="sxs-lookup"><span data-stu-id="3421d-128">false</span></span>                                |
| <span data-ttu-id="3421d-129">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-130">false</span><span class="sxs-lookup"><span data-stu-id="3421d-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="3421d-131">-ConfigurationName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="3421d-132">Spécifie le nom de la configuration de session Windows PowerShell, également appelée point de terminaison ou instance d’exécution, à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-133">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-133">Aliases</span></span>                              | <span data-ttu-id="3421d-134">none</span><span class="sxs-lookup"><span data-stu-id="3421d-134">none</span></span>                                 |
| <span data-ttu-id="3421d-135">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-135">Required?</span></span>                            | <span data-ttu-id="3421d-136">false</span><span class="sxs-lookup"><span data-stu-id="3421d-136">false</span></span>                                |
| <span data-ttu-id="3421d-137">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-137">Position?</span></span>                            | <span data-ttu-id="3421d-138">3</span><span class="sxs-lookup"><span data-stu-id="3421d-138">3</span></span>                                    |
| <span data-ttu-id="3421d-139">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-139">Default Value</span></span>                        | <span data-ttu-id="3421d-140">none</span><span class="sxs-lookup"><span data-stu-id="3421d-140">none</span></span>                                 |
| <span data-ttu-id="3421d-141">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-142">false</span><span class="sxs-lookup"><span data-stu-id="3421d-142">false</span></span>                                |
| <span data-ttu-id="3421d-143">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-144">false</span><span class="sxs-lookup"><span data-stu-id="3421d-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="3421d-145">-ConnectionUri &lt;URI&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="3421d-146">Spécifie l’URI de la connexion à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-147">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-147">Aliases</span></span>                              | <span data-ttu-id="3421d-148">none</span><span class="sxs-lookup"><span data-stu-id="3421d-148">none</span></span>                                 |
| <span data-ttu-id="3421d-149">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-149">Required?</span></span>                            | <span data-ttu-id="3421d-150">true</span><span class="sxs-lookup"><span data-stu-id="3421d-150">true</span></span>                                 |
| <span data-ttu-id="3421d-151">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-151">Position?</span></span>                            | <span data-ttu-id="3421d-152">2</span><span class="sxs-lookup"><span data-stu-id="3421d-152">2</span></span>                                    |
| <span data-ttu-id="3421d-153">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-153">Default Value</span></span>                        | <span data-ttu-id="3421d-154">none</span><span class="sxs-lookup"><span data-stu-id="3421d-154">none</span></span>                                 |
| <span data-ttu-id="3421d-155">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-156">false</span><span class="sxs-lookup"><span data-stu-id="3421d-156">false</span></span>                                |
| <span data-ttu-id="3421d-157">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-158">false</span><span class="sxs-lookup"><span data-stu-id="3421d-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="3421d-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="3421d-160">Spécifie un objet **PSCredential** pour un compte d’utilisateur que vous voulez utiliser pour tester les règles d’autorisation d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3421d-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="3421d-161">Si vous n’ajoutez pas ce paramètre, l’applet de commande utilise le compte d’utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="3421d-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="3421d-162">Pour obtenir un objet **PSCredential**, qui est nécessaire pour tester des règles d’autorisation à distance, exécutez l’applet de commande [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="3421d-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-163">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-163">Aliases</span></span>                              | <span data-ttu-id="3421d-164">none</span><span class="sxs-lookup"><span data-stu-id="3421d-164">none</span></span>                                 |
| <span data-ttu-id="3421d-165">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-165">Required?</span></span>                            | <span data-ttu-id="3421d-166">false</span><span class="sxs-lookup"><span data-stu-id="3421d-166">false</span></span>                                |
| <span data-ttu-id="3421d-167">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-167">Position?</span></span>                            | <span data-ttu-id="3421d-168">nommé</span><span class="sxs-lookup"><span data-stu-id="3421d-168">named</span></span>                                |
| <span data-ttu-id="3421d-169">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-169">Default Value</span></span>                        | <span data-ttu-id="3421d-170">none</span><span class="sxs-lookup"><span data-stu-id="3421d-170">none</span></span>                                 |
| <span data-ttu-id="3421d-171">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-172">false</span><span class="sxs-lookup"><span data-stu-id="3421d-172">false</span></span>                                |
| <span data-ttu-id="3421d-173">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-174">false</span><span class="sxs-lookup"><span data-stu-id="3421d-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="3421d-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="3421d-176">Spécifie un sous-ensemble de règles à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="3421d-177">Si ce paramètre n’est pas spécifié, cette applet de commande teste en prenant en compte toutes les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="3421d-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-178">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-178">Aliases</span></span>                              | <span data-ttu-id="3421d-179">none</span><span class="sxs-lookup"><span data-stu-id="3421d-179">none</span></span>                                 |
| <span data-ttu-id="3421d-180">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-180">Required?</span></span>                            | <span data-ttu-id="3421d-181">false</span><span class="sxs-lookup"><span data-stu-id="3421d-181">false</span></span>                                |
| <span data-ttu-id="3421d-182">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-182">Position?</span></span>                            | <span data-ttu-id="3421d-183">nommé</span><span class="sxs-lookup"><span data-stu-id="3421d-183">named</span></span>                                |
| <span data-ttu-id="3421d-184">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-184">Default Value</span></span>                        | <span data-ttu-id="3421d-185">none</span><span class="sxs-lookup"><span data-stu-id="3421d-185">none</span></span>                                 |
| <span data-ttu-id="3421d-186">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="3421d-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="3421d-188">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-189">false</span><span class="sxs-lookup"><span data-stu-id="3421d-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="3421d-190">-UserName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="3421d-191">Spécifie le nom de l’utilisateur à tester.</span><span class="sxs-lookup"><span data-stu-id="3421d-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3421d-192">Alias</span><span class="sxs-lookup"><span data-stu-id="3421d-192">Aliases</span></span>                              | <span data-ttu-id="3421d-193">none</span><span class="sxs-lookup"><span data-stu-id="3421d-193">none</span></span>                                 |
| <span data-ttu-id="3421d-194">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="3421d-194">Required?</span></span>                            | <span data-ttu-id="3421d-195">true</span><span class="sxs-lookup"><span data-stu-id="3421d-195">true</span></span>                                 |
| <span data-ttu-id="3421d-196">Position ?</span><span class="sxs-lookup"><span data-stu-id="3421d-196">Position?</span></span>                            | <span data-ttu-id="3421d-197">1</span><span class="sxs-lookup"><span data-stu-id="3421d-197">1</span></span>                                    |
| <span data-ttu-id="3421d-198">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3421d-198">Default Value</span></span>                        | <span data-ttu-id="3421d-199">none</span><span class="sxs-lookup"><span data-stu-id="3421d-199">none</span></span>                                 |
| <span data-ttu-id="3421d-200">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="3421d-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3421d-201">false</span><span class="sxs-lookup"><span data-stu-id="3421d-201">false</span></span>                                |
| <span data-ttu-id="3421d-202">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="3421d-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3421d-203">false</span><span class="sxs-lookup"><span data-stu-id="3421d-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="3421d-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="3421d-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="3421d-205">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="3421d-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="3421d-206">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3421d-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="3421d-207">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="3421d-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="3421d-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="3421d-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="3421d-209">Cette applet de commande accepte un tableau d’objets PswaAuthorizationRule en entrée.</span><span class="sxs-lookup"><span data-stu-id="3421d-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="3421d-210">SORTIES</span><span class="sxs-lookup"><span data-stu-id="3421d-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="3421d-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="3421d-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="3421d-212">Cette applet de commande produit un tableau d’objets PswaAuthorizationRule en sortie.</span><span class="sxs-lookup"><span data-stu-id="3421d-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="3421d-213">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="3421d-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="3421d-214">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="3421d-214">EXAMPLE 1</span></span>

<span data-ttu-id="3421d-215">Cet exemple teste toutes les règles d’autorisation pour afficher toutes les règles qui permettent à l’utilisateur *contoso\\mhanson* de se connecter à l’ordinateur *srv2* et d’utiliser une configuration de session Windows PowerShell nommée *test*.</span><span class="sxs-lookup"><span data-stu-id="3421d-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="3421d-216">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="3421d-216">EXAMPLE 2</span></span>

<span data-ttu-id="3421d-217">Cet exemple teste toutes les règles d’autorisation pour déterminer quelles règles s’appliquent à l’utilisateur *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="3421d-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="3421d-218">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3421d-218">Related topics</span></span>

- [<span data-ttu-id="3421d-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3421d-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="3421d-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3421d-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="3421d-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="3421d-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="3421d-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3421d-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
