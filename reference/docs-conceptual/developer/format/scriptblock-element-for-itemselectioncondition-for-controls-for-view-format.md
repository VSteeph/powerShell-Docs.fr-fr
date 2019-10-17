---
title: Élément ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364918"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>ScriptBlock, élément pour ItemSelectionCondition pour Controls pour View (Format)

Spécifie le script qui déclenche la condition. Lorsque ce script est évalué à `true`, la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition de contrôles qui peuvent être utilisés par une vue.

Élément de configuration (format) élément ViewDefinitions (format) View, élément (format) contrôle l’élément (format) Control, élément pour les contrôles pour View (format) CustomControl, élément de Control pour les contrôles pour l’élément View (format) CustomEntries pour CustomControl pour View (format) CustomEntry, élément pour CustomEntries pour les contrôles pour l’élément CustomItem (format) View pour CustomEntry pour les contrôles pour l’élément View (format) ExpressionBinding pour CustomItem pour les contrôles pour View (format) Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour l’élément de vue (format) ScriptBlock pour ItemSelectionCondition pour les contrôles pour View (format)

## <a name="syntax"></a>Syntaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `ScriptBlock`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur texte

Spécifiez le script qui est évalué.

## <a name="remarks"></a>Remarks

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément PropertyName pour ItemSelectionCondition pour les contrôles pour View (format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Élément ItemSelectionCondition de ExpressionBinding pour les contrôles pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)