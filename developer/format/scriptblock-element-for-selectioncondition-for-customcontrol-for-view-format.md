---
title: Élément ScriptBlock pour SelectionCondition pour CustomControl de vue (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857415"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="79119-102">ScriptBlock, élément pour SelectionCondition pour CustomControl pour View (Format)</span><span class="sxs-lookup"><span data-stu-id="79119-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="79119-103">Spécifie le script qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="79119-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="79119-104">Lorsque ce script est évalué à `true`, la condition est remplie et que la définition est utilisée.</span><span class="sxs-lookup"><span data-stu-id="79119-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="79119-105">Cet élément est utilisé lors de la définition d’une vue de contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="79119-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="79119-106">Configuration élément (Format) élément ViewDefinitions (Format) vue (Format) CustomControl élément pour élément d’affichage (Format) de CustomEntries pour CustomControl pour élément d’affichage (Format) de CustomEntry pour CustomEntries pour CustomControl pour la vue ( Format), élément CustomItem pour CustomEntry pour CustomControl pour l’élément d’affichage (Format) de SelectionCondition pour EntrySelectedBy pour CustomControl pour élément ScriptBlock de vue (Format) pour SelectionCondition pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="79119-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79119-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79119-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79119-108">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="79119-108">Attributes and Elements</span></span>

<span data-ttu-id="79119-109">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `ScriptBlock` élément.</span><span class="sxs-lookup"><span data-stu-id="79119-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79119-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="79119-110">Attributes</span></span>

<span data-ttu-id="79119-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="79119-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79119-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="79119-112">Child Elements</span></span>

<span data-ttu-id="79119-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="79119-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79119-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="79119-114">Parent Elements</span></span>

|<span data-ttu-id="79119-115">Élément</span><span class="sxs-lookup"><span data-stu-id="79119-115">Element</span></span>|<span data-ttu-id="79119-116">Description</span><span class="sxs-lookup"><span data-stu-id="79119-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79119-117">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="79119-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="79119-118">Définit une condition qui doit exister pour la définition du contrôle à utiliser.</span><span class="sxs-lookup"><span data-stu-id="79119-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79119-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="79119-119">Text Value</span></span>

<span data-ttu-id="79119-120">Spécifiez le script qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="79119-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="79119-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="79119-121">Remarks</span></span>

<span data-ttu-id="79119-122">La condition de sélection doit spécifier un moins un script ou le nom à évaluer, mais vous ne pouvez pas spécifier à la fois.</span><span class="sxs-lookup"><span data-stu-id="79119-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="79119-123">Pour plus d’informations sur la façon dont les conditions de sélection peuvent être utilisées, consultez [définition des Conditions d’affichage de données](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="79119-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79119-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79119-124">See Also</span></span>

[<span data-ttu-id="79119-125">Élément SelectionCondition pour EntrySelectedBy pour CustomControl de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="79119-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="79119-126">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="79119-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)