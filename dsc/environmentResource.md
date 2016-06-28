---
title: Ressource Environment DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 20a7711604033b5ff1484dbb526df2642a9a1738

---

# Ressource Environment DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource __Environment__ dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système.

## Syntaxe
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.| 
| Ensure| Indique si une variable existe. Définissez cette propriété sur __Present__ pour créer la variable d’environnement s’il n’en existe pas ou pour vérifier que sa valeur correspond à celle fournie par la propriété __Value__ si la variable existe déjà. Affectez-lui la valeur __Absent__ pour supprimer la variable, si elle existe.| 
| Path| Définit la variable d’environnement actuellement configurée. Définissez cette propriété sur __$true__ si la variable est une variable __Path__ ; sinon, affectez-lui la valeur __$false__. La valeur par défaut est __$false__. Si la variable actuellement configurée est une variable __Path__, la valeur fournie par la propriété __Value__ est adjointe à la valeur existante.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID __ResourceName__ et le type __ResourceType__, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| Valeur à attribuer à la variable d’environnement.| 

## Exemple

L’exemple suivant vérifie que __TestEnvironmentVariable__ est présent et que sa valeur est __TestValue__. S’il n’est pas présent, il le crée.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```




<!--HONumber=Jun16_HO4-->


