---
title: L’étiquette d’élément pour TableColumnHeader pour la table (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856085"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="154ee-102">Label, élément pour TableColumnHeader pour TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="154ee-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="154ee-103">Définit l’étiquette qui s’affiche en haut d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="154ee-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="154ee-104">Cet élément est utilisé lors de la définition d’une vue de table.</span><span class="sxs-lookup"><span data-stu-id="154ee-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="154ee-105">Élément (Format) élément ViewDefinitions (Format) vue élément (Format) élément de table (Format) TableHeaders élément de configuration pour élément TableColumnHeader de table (Format) pour TableHeaders pour l’élément Label de table (Format) pour TableColumnHeader pour TablControl (Format)</span><span class="sxs-lookup"><span data-stu-id="154ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TablControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="154ee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="154ee-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="154ee-107">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="154ee-107">Attributes and Elements</span></span>

<span data-ttu-id="154ee-108">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Label` élément.</span><span class="sxs-lookup"><span data-stu-id="154ee-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="154ee-109">Étiquette qu’un seul est autorisée pour chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="154ee-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="154ee-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="154ee-110">Attributes</span></span>

<span data-ttu-id="154ee-111">Aucune.</span><span class="sxs-lookup"><span data-stu-id="154ee-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="154ee-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="154ee-112">Child Elements</span></span>

<span data-ttu-id="154ee-113">Aucune.</span><span class="sxs-lookup"><span data-stu-id="154ee-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="154ee-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="154ee-114">Parent Elements</span></span>

|<span data-ttu-id="154ee-115">Élément</span><span class="sxs-lookup"><span data-stu-id="154ee-115">Element</span></span>|<span data-ttu-id="154ee-116">Description</span><span class="sxs-lookup"><span data-stu-id="154ee-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="154ee-117">Élément TableColumnHeader pour TableHeaders pour la table (Format)</span><span class="sxs-lookup"><span data-stu-id="154ee-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="154ee-118">Définit une étiquette, la largeur et l’alignement des données pour une colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="154ee-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="154ee-119">Valeur de texte</span><span class="sxs-lookup"><span data-stu-id="154ee-119">Text Value</span></span>

<span data-ttu-id="154ee-120">Spécifiez le texte qui s’affiche en haut de la colonne de la table.</span><span class="sxs-lookup"><span data-stu-id="154ee-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="154ee-121">Il n’existe aucun des caractères non autorisés pour l’étiquette de colonne.</span><span class="sxs-lookup"><span data-stu-id="154ee-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="154ee-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="154ee-122">Remarks</span></span>

<span data-ttu-id="154ee-123">Si aucune étiquette n’est spécifiée, le nom de la propriété dont la valeur est affichée dans les lignes est utilisé.</span><span class="sxs-lookup"><span data-stu-id="154ee-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="154ee-124">Pour plus d’informations sur les composants d’une vue de table, consultez [création d’une vue de Table](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="154ee-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="154ee-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="154ee-125">Example</span></span>

<span data-ttu-id="154ee-126">Cet exemple montre un `TableColumnHeader` élément dont l’étiquette est « Colonne 1 ».</span><span class="sxs-lookup"><span data-stu-id="154ee-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="154ee-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="154ee-127">See Also</span></span>

[<span data-ttu-id="154ee-128">Création d’une vue de Table</span><span class="sxs-lookup"><span data-stu-id="154ee-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="154ee-129">Élément TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="154ee-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="154ee-130">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="154ee-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)