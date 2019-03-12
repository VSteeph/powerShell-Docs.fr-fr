---
title: Élément des frames pour CustomItem pour GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854845"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="27f42-102">Frame, élément pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="27f42-103">Définit l’affichage des données, telles que les données le décalage vers la gauche ou droite.</span><span class="sxs-lookup"><span data-stu-id="27f42-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="27f42-104">Cet élément est utilisé lors de la définition d’affichage d’un nouveau groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="27f42-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="27f42-105">Configuration élément (Format) ViewDefinitions (Format) vue (Format) d’élément GroupBy élément pour les éléments de CustomControl affichage (Format) d’élément de CustomEntries GroupBy (Format) pour CustomControl d’élément de CustomEntry GroupBy (Format) pour CustomControl d’élément de CustomItem GroupBy (Format) pour CustomEntry d’élément de Frame GroupBy (Format) pour CustomItem pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27f42-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27f42-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27f42-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="27f42-107">Attributes and Elements</span></span>

<span data-ttu-id="27f42-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="27f42-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27f42-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="27f42-109">Attributes</span></span>

<span data-ttu-id="27f42-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="27f42-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27f42-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27f42-111">Child Elements</span></span>

|<span data-ttu-id="27f42-112">Élément</span><span class="sxs-lookup"><span data-stu-id="27f42-112">Element</span></span>|<span data-ttu-id="27f42-113">Description</span><span class="sxs-lookup"><span data-stu-id="27f42-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="27f42-114">Élément requis</span><span class="sxs-lookup"><span data-stu-id="27f42-114">Required Element</span></span>|
|[<span data-ttu-id="27f42-115">Élément FirstLineHanging pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="27f42-116">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27f42-116">Optional element.</span></span><br /><br /> <span data-ttu-id="27f42-117">Spécifie le nombre de caractères la première ligne de données est décalée vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="27f42-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="27f42-118">Élément FirstLineIndent pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="27f42-119">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27f42-119">Optional element.</span></span><br /><br /> <span data-ttu-id="27f42-120">Spécifie le nombre de caractères la première ligne de données est décalée vers la droite.</span><span class="sxs-lookup"><span data-stu-id="27f42-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="27f42-121">Élément Macintosh pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="27f42-122">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27f42-122">Optional element.</span></span><br /><br /> <span data-ttu-id="27f42-123">Spécifie le nombre de caractères les données s’éloigne de la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="27f42-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="27f42-124">[Élément RightIndent pour Frame pour GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent élément</span><span class="sxs-lookup"><span data-stu-id="27f42-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="27f42-125">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="27f42-125">Optional element.</span></span><br /><br /> <span data-ttu-id="27f42-126">Spécifie le nombre de caractères les données s’éloigne de la marge de droite.</span><span class="sxs-lookup"><span data-stu-id="27f42-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="27f42-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27f42-127">Parent Elements</span></span>

|<span data-ttu-id="27f42-128">Élément</span><span class="sxs-lookup"><span data-stu-id="27f42-128">Element</span></span>|<span data-ttu-id="27f42-129">Description</span><span class="sxs-lookup"><span data-stu-id="27f42-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27f42-130">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="27f42-131">Définit les données affichées par le contrôle et comment il est affiché.</span><span class="sxs-lookup"><span data-stu-id="27f42-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="27f42-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="27f42-132">Remarks</span></span>

<span data-ttu-id="27f42-133">Vous ne pouvez pas spécifier le [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) et [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) éléments dans le même `Frame` élément.</span><span class="sxs-lookup"><span data-stu-id="27f42-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="27f42-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f42-134">See Also</span></span>

[<span data-ttu-id="27f42-135">Élément FirstLineHanging pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="27f42-136">Élément FirstLineIndent pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="27f42-137">Élément Macintosh pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="27f42-138">Élément RightIndent pour Frame pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="27f42-139">Élément CustomItem pour CustomEntry pour GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="27f42-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="27f42-140">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27f42-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)