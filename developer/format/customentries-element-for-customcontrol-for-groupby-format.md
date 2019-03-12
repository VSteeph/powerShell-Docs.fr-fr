---
title: Élément CustomEntries pour CustomControl pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853675"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="2be7f-102">CustomEntries, élément pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="2be7f-103">Fournit les définitions pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2be7f-103">Provides the definitions for the control.</span></span> <span data-ttu-id="2be7f-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="2be7f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2be7f-105">Configuration élément (Format) ViewDefinitions, élément (Format) élément (Format) GroupBy élément d’affichage pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2be7f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2be7f-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2be7f-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="2be7f-107">Attributes and Elements</span></span>

<span data-ttu-id="2be7f-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents de la `CustomEntries` élément.</span><span class="sxs-lookup"><span data-stu-id="2be7f-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="2be7f-109">Il n’existe aucune limite maximale pour le nombre d’éléments enfants qui peuvent être spécifiées.</span><span class="sxs-lookup"><span data-stu-id="2be7f-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="2be7f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2be7f-110">Attributes</span></span>

<span data-ttu-id="2be7f-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="2be7f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2be7f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2be7f-112">Child Elements</span></span>

|<span data-ttu-id="2be7f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="2be7f-113">Element</span></span>|<span data-ttu-id="2be7f-114">Description</span><span class="sxs-lookup"><span data-stu-id="2be7f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2be7f-115">Élément CustomEntry pour CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="2be7f-116">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="2be7f-116">Required element.</span></span><br /><br /> <span data-ttu-id="2be7f-117">Fournit une définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="2be7f-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2be7f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2be7f-118">Parent Elements</span></span>

|<span data-ttu-id="2be7f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="2be7f-119">Element</span></span>|<span data-ttu-id="2be7f-120">Description</span><span class="sxs-lookup"><span data-stu-id="2be7f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2be7f-121">Élément CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="2be7f-122">Définit le contrôle personnalisé qui affiche le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="2be7f-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2be7f-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2be7f-123">Remarks</span></span>

<span data-ttu-id="2be7f-124">Dans la plupart des cas, un contrôle n'a qu’une seule définition, ce qui est spécifiée dans un seul `CustomEntry` élément.</span><span class="sxs-lookup"><span data-stu-id="2be7f-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="2be7f-125">Toutefois, il est possible de fournir plusieurs définitions si vous souhaitez utiliser le même contrôle pour afficher les différents groupes.</span><span class="sxs-lookup"><span data-stu-id="2be7f-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="2be7f-126">Dans ce cas, vous pouvez définir un `CustomEntry` élément pour un groupe.</span><span class="sxs-lookup"><span data-stu-id="2be7f-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="2be7f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2be7f-127">See Also</span></span>

[<span data-ttu-id="2be7f-128">Élément CustomEntry pour CustomEntries pour les contrôles de vue (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="2be7f-129">Élément CustomControl pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2be7f-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="2be7f-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2be7f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)