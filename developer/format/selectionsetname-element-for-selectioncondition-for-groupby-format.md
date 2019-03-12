---
title: Élément SelectionSetName pour SelectionCondition pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856755"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="b74cc-102">SelectionSetName, élément pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b74cc-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b74cc-103">Spécifie l’ensemble des types .NET qui déclenchent la condition.</span><span class="sxs-lookup"><span data-stu-id="b74cc-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b74cc-104">Quand les types dans cet ensemble sont présents, la condition est remplie, et l’objet est affiché à l’aide de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="b74cc-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="b74cc-105">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="b74cc-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b74cc-106">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de EntrySelectedBy GroupBy (Format) pour CustomEntry d’élément de SelectionCondition GroupBy (Format) pour EntrySelectedBy d’élément de SelectionSetName GroupBy (Format) pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b74cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b74cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b74cc-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b74cc-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="b74cc-108">Attributes and Elements</span></span>

<span data-ttu-id="b74cc-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `SelectionSetName` élément.</span><span class="sxs-lookup"><span data-stu-id="b74cc-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b74cc-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="b74cc-110">Attributes</span></span>

<span data-ttu-id="b74cc-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b74cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b74cc-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b74cc-112">Child Elements</span></span>

<span data-ttu-id="b74cc-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="b74cc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b74cc-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b74cc-114">Parent Elements</span></span>

|<span data-ttu-id="b74cc-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b74cc-115">Element</span></span>|<span data-ttu-id="b74cc-116">Description</span><span class="sxs-lookup"><span data-stu-id="b74cc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b74cc-117">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b74cc-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="b74cc-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b74cc-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b74cc-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="b74cc-119">Text Value</span></span>

<span data-ttu-id="b74cc-120">Spécifiez le nom de l’ensemble de la sélection.</span><span class="sxs-lookup"><span data-stu-id="b74cc-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b74cc-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="b74cc-121">Remarks</span></span>

<span data-ttu-id="b74cc-122">Les jeux de sélection sont courantes groupes d’objets .NET qui peuvent être utilisées par n’importe quelle vue qui définit le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b74cc-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b74cc-123">Pour plus d’informations sur la création et en faisant référence à des jeux de sélection, consultez [définition sélection définit](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b74cc-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b74cc-124">Lorsque cet élément est spécifié, vous ne pouvez pas spécifier le [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) élément.</span><span class="sxs-lookup"><span data-stu-id="b74cc-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="b74cc-125">Pour plus d’informations sur la définition des conditions de sélection, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b74cc-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b74cc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b74cc-126">See Also</span></span>

[<span data-ttu-id="b74cc-127">Élément TypeName pour SelectionCondition pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b74cc-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="b74cc-128">Élément SelectionCondition pour EntrySelectedBy pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b74cc-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="b74cc-129">Définition des Conditions pour lorsque les données sont affichées</span><span class="sxs-lookup"><span data-stu-id="b74cc-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b74cc-130">Définition de jeux de sélection</span><span class="sxs-lookup"><span data-stu-id="b74cc-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b74cc-131">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b74cc-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)