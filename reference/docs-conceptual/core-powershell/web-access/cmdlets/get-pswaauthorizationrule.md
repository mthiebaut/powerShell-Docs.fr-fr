---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="fb57f-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="fb57f-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="fb57f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fb57f-104">SYNOPSIS</span></span>

<span data-ttu-id="fb57f-105">Retourne un ensemble des règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="fb57f-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb57f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb57f-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="fb57f-107">ID</span><span class="sxs-lookup"><span data-stu-id="fb57f-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="fb57f-108">Name</span><span class="sxs-lookup"><span data-stu-id="fb57f-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="fb57f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fb57f-109">DESCRIPTION</span></span>

<span data-ttu-id="fb57f-110">L’applet de commande **Get-PswaAuthorizationRule** retourne un ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="fb57f-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="fb57f-111">Si ni le paramètre **Id** ni le paramètre **RuleName** n’est spécifié, cette applet de commande répertorie toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="fb57f-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="fb57f-112">Le paramètre **Id** peut être utilisé pour filtrer les résultats.</span><span class="sxs-lookup"><span data-stu-id="fb57f-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="fb57f-113">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="fb57f-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="fb57f-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="fb57f-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="fb57f-115">Spécifie les identificateurs (ID) des règles que cette applet de commande doit obtenir.</span><span class="sxs-lookup"><span data-stu-id="fb57f-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="fb57f-116">Si aucun ID n’est spécifié, cette applet de commande retourne toutes les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="fb57f-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="fb57f-117">Alias</span><span class="sxs-lookup"><span data-stu-id="fb57f-117">Aliases</span></span>                              | <span data-ttu-id="fb57f-118">none</span><span class="sxs-lookup"><span data-stu-id="fb57f-118">none</span></span>                                 |
| <span data-ttu-id="fb57f-119">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-119">Required?</span></span>                            | <span data-ttu-id="fb57f-120">false</span><span class="sxs-lookup"><span data-stu-id="fb57f-120">false</span></span>                                |
| <span data-ttu-id="fb57f-121">Position ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-121">Position?</span></span>                            | <span data-ttu-id="fb57f-122">2</span><span class="sxs-lookup"><span data-stu-id="fb57f-122">2</span></span>                                    |
| <span data-ttu-id="fb57f-123">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="fb57f-123">Default Value</span></span>                        | <span data-ttu-id="fb57f-124">none</span><span class="sxs-lookup"><span data-stu-id="fb57f-124">none</span></span>                                 |
| <span data-ttu-id="fb57f-125">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="fb57f-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="fb57f-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="fb57f-127">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="fb57f-128">false</span><span class="sxs-lookup"><span data-stu-id="fb57f-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="fb57f-129">-RuleName&lt;Chaîne\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="fb57f-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="fb57f-130">Spécifie les noms des règles d’autorisation à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fb57f-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="fb57f-131">Ce paramètre retourne les règles qui correspondent exactement aux noms de règle des chaînes de ce tableau.</span><span class="sxs-lookup"><span data-stu-id="fb57f-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="fb57f-132">Alias</span><span class="sxs-lookup"><span data-stu-id="fb57f-132">Aliases</span></span>                              | <span data-ttu-id="fb57f-133">none</span><span class="sxs-lookup"><span data-stu-id="fb57f-133">none</span></span>                                 |
| <span data-ttu-id="fb57f-134">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-134">Required?</span></span>                            | <span data-ttu-id="fb57f-135">true</span><span class="sxs-lookup"><span data-stu-id="fb57f-135">true</span></span>                                 |
| <span data-ttu-id="fb57f-136">Position ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-136">Position?</span></span>                            | <span data-ttu-id="fb57f-137">2</span><span class="sxs-lookup"><span data-stu-id="fb57f-137">2</span></span>                                    |
| <span data-ttu-id="fb57f-138">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="fb57f-138">Default Value</span></span>                        | <span data-ttu-id="fb57f-139">none</span><span class="sxs-lookup"><span data-stu-id="fb57f-139">none</span></span>                                 |
| <span data-ttu-id="fb57f-140">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="fb57f-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="fb57f-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="fb57f-142">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="fb57f-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="fb57f-143">false</span><span class="sxs-lookup"><span data-stu-id="fb57f-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="fb57f-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="fb57f-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="fb57f-145">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="fb57f-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="fb57f-146">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fb57f-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="fb57f-147">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fb57f-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="fb57f-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="fb57f-148">int\[\]</span></span>

<span data-ttu-id="fb57f-149">Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.</span><span class="sxs-lookup"><span data-stu-id="fb57f-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="fb57f-150">Chaîne\[\]</span><span class="sxs-lookup"><span data-stu-id="fb57f-150">String\[\]</span></span>

<span data-ttu-id="fb57f-151">Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.</span><span class="sxs-lookup"><span data-stu-id="fb57f-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="fb57f-152">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fb57f-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="fb57f-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="fb57f-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="fb57f-154">Cette applet de commande produit un objet PswaAuthorizationRule en sortie.</span><span class="sxs-lookup"><span data-stu-id="fb57f-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="fb57f-155">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fb57f-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="fb57f-156">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="fb57f-156">EXAMPLE 1</span></span>

<span data-ttu-id="fb57f-157">Cet exemple obtient toutes les règles.</span><span class="sxs-lookup"><span data-stu-id="fb57f-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="fb57f-158">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="fb57f-158">EXAMPLE 2</span></span>

<span data-ttu-id="fb57f-159">Cet exemple obtient une règle avec l’ID *2*.</span><span class="sxs-lookup"><span data-stu-id="fb57f-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="fb57f-160">EXEMPLE 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="fb57f-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="fb57f-161">Cet exemple montre comment l’applet de commande accepte une valeur du pipeline.</span><span class="sxs-lookup"><span data-stu-id="fb57f-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="fb57f-162">Un ID de règle et un nom de règle sont passés à cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fb57f-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="fb57f-163">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="fb57f-163">Related topics</span></span>

- [<span data-ttu-id="fb57f-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="fb57f-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="fb57f-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="fb57f-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="fb57f-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="fb57f-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="fb57f-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="fb57f-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)