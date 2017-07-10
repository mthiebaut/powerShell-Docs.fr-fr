---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxScript dans DSC pour Linux
ms.openlocfilehash: 381d8d214654641a34eeebcb54a81a25d61ee644
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-for-linux-nxscript-resource" class="xliff"></a>
# Ressource nxScript dans DSC pour Linux

La ressource **nxScript** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant d’exécuter des scripts Linux sur un nœud Linux.

<a id="syntax" class="xliff"></a>
## Syntaxe

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

<a id="properties" class="xliff"></a>
## Propriétés

|  Propriété |  Description | 
|---|---|
| GetScript| Fournit un script qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx). Le script doit commencer par un shebang, tel que #!/bin/bash.| 
| SetScript| Fournit un script. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne un code de sortie différent de 0, le bloc **SetScript** s’exécute. Si **TestScript** retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. Le script doit commencer par un shebang, tel que `#!/bin/bash`.| 
| TestScript| Fournit un script. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), ce script s’exécute. Si la propriété retourne un code de sortie différent de 0, SetScript s’exécute. Si la propriété retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. **TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quel que soit le code de sortie retourné par **TestScript**. **TestScript** doit retourner le code de sortie 0 si la configuration réelle correspond à la configuration actuelle de l’état souhaité. Sinon, elle doit retourner un code de sortie différent de 0. (La configuration actuelle de l’état souhaité est la dernière configuration appliquée sur le nœud qui utilise DSC.) Le script doit commencer par un shebang, tel que 1#!/bin/bash.1| 
| User| Nom d’utilisateur utilisé pour exécuter le script.| 
| Group| Nom de groupe utilisé pour exécuter le script.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.| 

<a id="example" class="xliff"></a>
## Exemple

L’exemple suivant utilise la ressource **nxScript** pour gérer une configuration supplémentaire.

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```

