---
title: Control, élément pour les contrôles de Configuration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858885"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="5a338-102">Control, élément pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5a338-103">Définit un contrôle commun qui peut être utilisé par toutes les vues de la mise en forme du fichier et le nom qui est utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a338-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="5a338-104">Élément de contrôles (Format) d’élément de configuration de l’élément de contrôle de Configuration (Format) pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a338-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a338-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a338-106">Éléments et attributs</span><span class="sxs-lookup"><span data-stu-id="5a338-106">Attributes and Elements</span></span>

<span data-ttu-id="5a338-107">Les sections suivantes décrivent les attributs, éléments enfants et l’élément parent de la `Control` élément.</span><span class="sxs-lookup"><span data-stu-id="5a338-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="5a338-108">Vous devez spécifier un seul de chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="5a338-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a338-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5a338-109">Attributes</span></span>

<span data-ttu-id="5a338-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5a338-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a338-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a338-111">Child Elements</span></span>

|<span data-ttu-id="5a338-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5a338-112">Element</span></span>|<span data-ttu-id="5a338-113">Description</span><span class="sxs-lookup"><span data-stu-id="5a338-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a338-114">Élément CustomControl pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="5a338-115">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="5a338-115">Required element.</span></span><br /><br /> <span data-ttu-id="5a338-116">Définit le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a338-116">Defines the control.</span></span>|
|[<span data-ttu-id="5a338-117">Name, élément pour le contrôle de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="5a338-118">Élément requis.</span><span class="sxs-lookup"><span data-stu-id="5a338-118">Required element.</span></span><br /><br /> <span data-ttu-id="5a338-119">Spécifie le nom utilisé pour référencer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5a338-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a338-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a338-120">Parent Elements</span></span>

|<span data-ttu-id="5a338-121">Élément</span><span class="sxs-lookup"><span data-stu-id="5a338-121">Element</span></span>|<span data-ttu-id="5a338-122">Description</span><span class="sxs-lookup"><span data-stu-id="5a338-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a338-123">Élément de contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="5a338-124">Définit les contrôles communs qui peuvent être utilisées par toutes les vues du fichier de mise en forme ou par d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="5a338-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5a338-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a338-125">Remarks</span></span>

<span data-ttu-id="5a338-126">Le nom donné à ce contrôle peut être référencé dans les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5a338-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="5a338-127">Élément ExpressionBinding pour CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="5a338-128">Élément GroupBy pour View(Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="5a338-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a338-129">See Also</span></span>

[<span data-ttu-id="5a338-130">Élément de contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="5a338-131">Élément CustomControl pour le contrôle de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="5a338-132">Élément ExpressionBinding pour CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="5a338-133">Élément GroupBy pour View(Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5a338-134">Name, élément pour le contrôle pour les contrôles de Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5a338-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="5a338-135">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a338-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)