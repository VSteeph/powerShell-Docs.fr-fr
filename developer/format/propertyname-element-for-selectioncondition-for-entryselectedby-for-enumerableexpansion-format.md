---
title: Élément PropertyName pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859625"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b0da6-102">PropertyName, élément pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b0da6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b0da6-103">Spécifie la propriété .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="b0da6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b0da6-104">Lorsque cette propriété est présente ou lorsqu’il prend la valeur `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b0da6-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="b0da6-105">Configuration élément (Format) élément DefaultSettings (Format) EnumerableExpansions (Format) élément EnumerableExpansion (Format) EntrySelectedBy élément d’élément de SelectionCondition EnumerableExpansion (Format) pour EntrySelectedBy pour Élément de PropertyName EnumerableExpansion (Format) pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b0da6-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b0da6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0da6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0da6-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b0da6-107">Attributes and Elements</span></span>

<span data-ttu-id="b0da6-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `PropertyName` élément.</span><span class="sxs-lookup"><span data-stu-id="b0da6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0da6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b0da6-109">Attributes</span></span>

<span data-ttu-id="b0da6-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b0da6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0da6-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b0da6-111">Child Elements</span></span>

<span data-ttu-id="b0da6-112">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b0da6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b0da6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b0da6-113">Parent Elements</span></span>

|<span data-ttu-id="b0da6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="b0da6-114">Element</span></span>|<span data-ttu-id="b0da6-115">Description</span><span class="sxs-lookup"><span data-stu-id="b0da6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0da6-116">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b0da6-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b0da6-117">Définit la condition qui doit exister pour développer la collection d’objets de cette définition.</span><span class="sxs-lookup"><span data-stu-id="b0da6-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b0da6-118">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="b0da6-118">Text Value</span></span>

<span data-ttu-id="b0da6-119">Spécifiez le nom de propriété .NET.</span><span class="sxs-lookup"><span data-stu-id="b0da6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0da6-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="b0da6-120">Remarks</span></span>

<span data-ttu-id="b0da6-121">La condition de sélection doit spécifier nom d’au moins une propriété ou un script pour évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="b0da6-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b0da6-122">Pour plus d’informations sur l’utilisation des conditions de sélection, consultez [définition des Conditions pour lorsque les données sont affichées](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b0da6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0da6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0da6-123">See Also</span></span>

[<span data-ttu-id="b0da6-124">Définition des Conditions pour les données lorsque s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b0da6-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b0da6-125">Élément ScriptBlock pour SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b0da6-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b0da6-126">Élément SelectionCondition pour EntrySelectedBy pour EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b0da6-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b0da6-127">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0da6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)