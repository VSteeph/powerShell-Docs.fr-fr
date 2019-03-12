---
title: Élément WideEntry pour WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856525"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="e1ec0-102">WideEntry, élément pour WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="e1ec0-103">Fournit une définition de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="e1ec0-104">Élément (Format) ViewDefinitions, élément (Format) vue élément (Format) WideControl, élément (Format) WideEntries, élément (Format) WideEntry élément de configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1ec0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1ec0-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1ec0-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="e1ec0-106">Attributes and Elements</span></span>

<span data-ttu-id="e1ec0-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `WideEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="e1ec0-108">Vous devez spécifier un seul `WideItem` élément enfant.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1ec0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e1ec0-109">Attributes</span></span>

<span data-ttu-id="e1ec0-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1ec0-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e1ec0-111">Child Elements</span></span>

|<span data-ttu-id="e1ec0-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e1ec0-112">Element</span></span>|<span data-ttu-id="e1ec0-113">Description</span><span class="sxs-lookup"><span data-stu-id="e1ec0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1ec0-114">Élément EntrySelectedBy pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="e1ec0-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e1ec0-116">Définit les types .NET qui utilisent cette définition de l’entrée large ou la condition qui doit exister pour cette définition à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e1ec0-117">Élément WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e1ec0-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-118">Required element.</span></span><br /><br /> <span data-ttu-id="e1ec0-119">Définit la propriété ou un script dont la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1ec0-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e1ec0-120">Parent Elements</span></span>

|<span data-ttu-id="e1ec0-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e1ec0-121">Element</span></span>|<span data-ttu-id="e1ec0-122">Description</span><span class="sxs-lookup"><span data-stu-id="e1ec0-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1ec0-123">Élément WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="e1ec0-124">Fournit les définitions de l’affichage plus large.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1ec0-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="e1ec0-125">Remarks</span></span>

<span data-ttu-id="e1ec0-126">Un affichage plus large est un format de liste qui affiche une valeur de propriété unique ou une valeur de script pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="e1ec0-127">Contrairement à d’autres types de vues, vous pouvez spécifier qu’un seul élément pour chaque définition de la vue.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="e1ec0-128">Pour plus d’informations sur les autres composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e1ec0-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1ec0-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1ec0-129">Example</span></span>

<span data-ttu-id="e1ec0-130">L’exemple suivant montre un `WideEntry` élément qui définit un seul `WideItem` élément.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e1ec0-131">Le `WideItem` élément définit la propriété dont la valeur est affichée dans la vue.</span><span class="sxs-lookup"><span data-stu-id="e1ec0-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="e1ec0-132">Pour obtenir un exemple complet d’un affichage plus large, consultez [affichage plus large (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e1ec0-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ec0-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1ec0-133">See Also</span></span>

[<span data-ttu-id="e1ec0-134">Création d’un affichage plus large</span><span class="sxs-lookup"><span data-stu-id="e1ec0-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e1ec0-135">Élément SelectionCondition pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e1ec0-136">Élément SelectionSetName pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e1ec0-137">Élément TypeName pour WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e1ec0-138">Élément WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="e1ec0-139">Élément WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e1ec0-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e1ec0-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1ec0-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)