---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet PowerShellTabCollection
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808565"
---
# <a name="the-powershelltabcollection-object"></a>Objet PowerShellTabCollection

L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**. Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. L’objet `$psISE.PowerShellTabs` en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add"></a>Add\(\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Ajoute un nouvel onglet PowerShell à la collection. Elle retourne l’onglet qui vient d’être ajouté.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Supprime l’onglet spécifié par le paramètre **psTab**.

**psTab** Onglet PowerShell à supprimer.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.

**psTab** Onglet PowerShell à sélectionner.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Voir aussi

- [Objet PowerShellTab](The-PowerShellTab-Object.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
