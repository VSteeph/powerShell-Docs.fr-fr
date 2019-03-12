---
title: Élément de configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856325"
---
# <a name="configuration-element-format"></a><span data-ttu-id="691c4-102">Configuration, élément (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-102">Configuration Element (Format)</span></span>

<span data-ttu-id="691c4-103">Représente l’élément de niveau supérieur d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="691c4-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="691c4-104">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="691c4-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="691c4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="691c4-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="691c4-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="691c4-106">Attributes and Elements</span></span>

<span data-ttu-id="691c4-107">Les sections suivantes décrivent les attributs et éléments enfants de l’élément parent le `Configuration` élément.</span><span class="sxs-lookup"><span data-stu-id="691c4-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="691c4-108">Cet élément doit être l’élément racine pour chaque fichier de mise en forme, et cet élément doit contenir au moins un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="691c4-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="691c4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="691c4-109">Attributes</span></span>

<span data-ttu-id="691c4-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="691c4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="691c4-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="691c4-111">Child Elements</span></span>

|<span data-ttu-id="691c4-112">Élément</span><span class="sxs-lookup"><span data-stu-id="691c4-112">Element</span></span>|<span data-ttu-id="691c4-113">Description</span><span class="sxs-lookup"><span data-stu-id="691c4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="691c4-114">Élément de Controls pour la Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="691c4-115">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="691c4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="691c4-116">Définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="691c4-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="691c4-117">Élément DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="691c4-118">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="691c4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="691c4-119">Définit des paramètres communs qui s’appliquent à toutes les vues du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="691c4-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="691c4-120">Format d’élément de SelectionSets</span><span class="sxs-lookup"><span data-stu-id="691c4-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="691c4-121">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="691c4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="691c4-122">Définit les jeux d’objets .NET qui peuvent être utilisées par toutes les vues du fichier de mise en forme courants.</span><span class="sxs-lookup"><span data-stu-id="691c4-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="691c4-123">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="691c4-124">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="691c4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="691c4-125">Définit les vues utilisées pour afficher les objets.</span><span class="sxs-lookup"><span data-stu-id="691c4-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="691c4-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="691c4-126">Parent Elements</span></span>

<span data-ttu-id="691c4-127">Aucune.</span><span class="sxs-lookup"><span data-stu-id="691c4-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="691c4-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="691c4-128">Remarks</span></span>

<span data-ttu-id="691c4-129">Fichiers de mise en forme définissent comment les objets sont affichés.</span><span class="sxs-lookup"><span data-stu-id="691c4-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="691c4-130">Dans la plupart des cas, cet élément racine contient un [ViewDefinitions](./viewdefinitions-element-format.md) élément qui définit la table, une liste et un affichage large du fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="691c4-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="691c4-131">Outre les définitions de vue, le fichier de mise en forme pouvez définir des jeux de sélection, les paramètres et les contrôles ces vues peuvent utiliser courants.</span><span class="sxs-lookup"><span data-stu-id="691c4-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="691c4-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="691c4-132">See Also</span></span>

[<span data-ttu-id="691c4-133">Élément de Controls pour la Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="691c4-134">Élément DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="691c4-135">Élément SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="691c4-136">Élément ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="691c4-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="691c4-137">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="691c4-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)