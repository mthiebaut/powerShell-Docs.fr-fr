---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 003195457660a18b9bbed065181b6d8c23835348
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Retourne un ensemble des règles d’autorisation d’Accès Web Windows PowerShell®.

## <a name="syntax"></a>Syntaxe

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Name
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPTION

L’applet de commande **Get-PswaAuthorizationRule** retourne un ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.
Si ni le paramètre **Id** ni le paramètre **RuleName** n’est spécifié, cette applet de commande répertorie toutes les règles. Le paramètre **Id** peut être utilisé pour filtrer les résultats.

## <a name="parameters"></a>PARAMÈTRES

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Spécifie les identificateurs (ID) des règles que cette applet de commande doit obtenir. Si aucun ID n’est spécifié, cette applet de commande retourne toutes les règles d’autorisation.

|||  
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue, ByPropertyName)       |
| Accepter les caractères génériques ?          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;Chaîne\[\]&gt;

Spécifie les noms des règles d’autorisation à récupérer. Ce paramètre retourne les règles qui correspondent exactement aux noms de règle des chaînes de ce tableau.

|||  
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue, ByPropertyName)       |
| Accepter les caractères génériques ?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.
Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRÉES

### <a name="int"></a>int\[\]

Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.

### <a name="string"></a>Chaîne\[\]

Cette applet de commande accepte un tableau d’entiers ou un tableau de valeurs de chaîne en entrée.

## <a name="outputs"></a>SORTIES

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Cette applet de commande produit un objet PswaAuthorizationRule en sortie.


## <a name="examples"></a>EXEMPLES

### <a name="example-1"></a>EXEMPLE 1

Cet exemple obtient toutes les règles.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>EXAMPLE 2

Cet exemple obtient une règle avec l’ID *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>EXEMPLE 3 {#example-3 .subHeading}

Cet exemple montre comment l’applet de commande accepte une valeur du pipeline.
Un ID de règle et un nom de règle sont passés à cette applet de commande.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Rubriques connexes

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
