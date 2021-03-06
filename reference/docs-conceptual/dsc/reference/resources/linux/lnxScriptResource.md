---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource nxScript dans DSC pour Linux
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953186"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Ressource nxScript dans DSC pour Linux

La ressource **nxScript** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant d’exécuter des scripts Linux sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|GetScript |Fournit un script pour retourner l’état actuel de l’ordinateur. Ce script s’exécute quand vous appelez le script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). Le script doit commencer par un shebang, tel que `#!/bin/bash`. |
|SetScript |Fournit un script qui place l’ordinateur dans l’état correct. Quand vous appelez le script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne un code de sortie différent de 0, le bloc **SetScript** s’exécute. Si **TestScript** retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. Le script doit commencer par un shebang, tel que `#!/bin/bash`. |
|TestScript |Fournit un script qui évalue si le nœud est actuellement dans un état correct. Quand vous appelez le script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), ce script s’exécute. Si la propriété retourne un code de sortie différent de 0, **SetScript** s’exécute. Si la propriété retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. **TestScript** s’exécute également quand vous appelez le script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quel que soit le code de sortie retourné par **TestScript**. **TestScript** doit contenir du contenu et retourner le code de sortie 0 si la configuration réelle correspond à la configuration actuelle de l’état souhaité. Sinon, elle doit retourner un code de sortie différent de 0. La configuration d’état souhaité actuelle est la dernière configuration appliquée sur le nœud qui utilise DSC. Le script doit commencer par un shebang, tel que `#!/bin/bash`. |
|Utilisateur |Nom d’utilisateur utilisé pour exécuter le script. |
|Groupe |Nom de groupe utilisé pour exécuter le script. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="example"></a>Exemple

L’exemple suivant utilise la ressource **nxScript** pour gérer une configuration supplémentaire.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

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
