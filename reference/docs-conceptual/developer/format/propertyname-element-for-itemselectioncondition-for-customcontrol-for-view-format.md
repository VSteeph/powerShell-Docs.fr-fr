---
title: PropertyName, élément de ItemSelectionCondition pour CustomControl pour View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362438"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName, élément pour ItemSelectionCondition pour CustomControl pour View (Format)

Spécifie la propriété .NET qui déclenche la condition. Lorsque cette propriété est présente ou lorsqu’elle prend la valeur `true`, la condition est remplie et le contrôle est utilisé. Cet élément est utilisé lors de la définition d’un affichage de contrôle personnalisé.

Élément de configuration (format) élément ViewDefinitions (format) élément de vue (format) élément CustomControl (format) élément CustomEntries pour CustomControl pour View (format) élément CustomEntry pour CustomEntries pour la vue (format) CustomItem, élément de CustomEntry pour l’élément ExpressionBinding View (format) de CustomItem pour CustomControl pour la vue (format) élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour l’élément View (format) PropertyName pour ItemSelectionCondition pour CustomControl pour View (format

## <a name="syntax"></a>Syntaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Éléments et attributs

Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l’élément `PropertyName`.

### <a name="attributes"></a>Attributs

Aucune.

### <a name="child-elements"></a>Éléments enfants

Aucune.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Définit la condition qui doit exister pour que ce contrôle soit utilisé.|

## <a name="text-value"></a>Valeur de texte

Spécifiez le nom de la propriété .NET qui déclenche la condition.

## <a name="remarks"></a>Remarks

Si cet élément est utilisé, vous ne pouvez pas spécifier l’élément [scriptblock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) lors de la définition de la condition de sélection.

## <a name="see-also"></a>Voir aussi

[Élément ScriptBlock pour ItemSelectionCondition pour CustomControl pour View (format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Élément ItemSelectionCondition pour la liaison d’expression pour CustomControl pour View (format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
