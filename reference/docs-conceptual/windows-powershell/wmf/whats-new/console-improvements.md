---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Améliorations de la console dans WMF 5.1
ms.openlocfilehash: ae3d08a34a09bc32d40a8a45788999ee9c54a562
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808985"
---
# <a name="console-improvements-in-wmf-51"></a>Améliorations de la console dans WMF 5.1

## <a name="powershell-console-improvements"></a>Améliorations de la console PowerShell

Les modifications suivantes ont été apportées à powershell.exe dans WMF 5.1 pour améliorer l’expérience de la console :

### <a name="vt100-support"></a>Prise en charge de VT100

Ajout dans Windows 10 de la prise en charge des [séquences d’échappement VT100](/windows/console/console-virtual-terminal-sequences).
PowerShell ignore certaines séquences d’échappement de mise en forme VT100 lors du calcul des largeurs de tableaux.

Ajout dans PowerShell d’une nouvelle API que vous pouvez utiliser dans le code de mise en forme pour déterminer si VT100 est pris en charge. Par exemple :

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

Voici un [exemple](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) complet que vous pouvez utiliser pour mettre en surbrillance des correspondances à partir de `Select-String`. Enregistrez l’exemple dans un fichier nommé `MatchInfo.format.ps1xml` puis, pour l’utiliser, dans votre profil ou ailleurs, exécutez `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Notez que les séquences d’échappement VT100 ne sont prises en charge qu’à compter de la Mise à jour anniversaire Windows 10.
Elles ne sont pas prises en charge sur les systèmes antérieurs.

### <a name="vi-mode-support-in-psreadline"></a>Prise en charge du mode vi dans PSReadline

Ajout de la prise en charge du mode vi dans [PSReadline](https://github.com/PowerShell/PSReadLine). Pour utiliser le mode vi, exécutez `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Stdin redirigé avec entrée interactive

Dans les versions antérieures, vous deviez démarrer PowerShell avec `powershell -File -` quand stdin était redirigé et que vous souhaitiez entrer des commandes de manière interactive.

Avec WMF 5.1, cette option difficile à découvrir n’est plus nécessaire. Il est possible de lancer PowerShell sans aucune option.

Notez que PSReadline ne prend pas en charge le flux STDIN redirigé et que l’expérience de modification de ligne de commande intégrée avec flux STDIN redirigé est très limitée (par exemple, les touches de direction ne fonctionnent pas). Une version ultérieure de PSReadline doit résoudre ce problème.
