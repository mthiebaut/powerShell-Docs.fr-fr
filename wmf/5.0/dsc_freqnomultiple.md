---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other" class="xliff"></a>
# Les fréquences pour RefreshMode et ConfigurationMode ne doivent pas nécessairement être des multiples les unes des autres

Dans la version précédente de DSC, le gestionnaire de configuration local traitait `RefreshFrequencyMins` et `ConfigurationModeFrequencyMins` comme des multiples. Dans WMF 5.0 RTM, ces propriétés sont traitées indépendamment l’une de l’autre. 

Pour plus d’informations, consultez [Configuration du Gestionnaire de configuration local](https://msdn.microsoft.com/powershell/dsc/metaconfig).

