---
title: Création d’un flux de travail avec Windows PowerShell activités | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853465"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="2f1d0-102">Création d’un workflow avec des activités Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f1d0-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="2f1d0-103">Vous pouvez créer un flux de travail Windows PowerShell en sélectionnant des activités à partir de la boîte à outils Visual Studio et en les faisant glisser vers la fenêtre du Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="2f1d0-104">Pour plus d’informations sur l’ajout d’activités de Windows PowerShell à la boîte à outils Visual Studio, consultez [Ajout d’activités Windows PowerShell pour Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d0-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="2f1d0-105">Les procédures suivantes décrivent comment créer un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifié par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joint, puis vérifie à nouveau l’état.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="2f1d0-106">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="2f1d0-106">Setting up the Project</span></span>

1. <span data-ttu-id="2f1d0-107">Suivez la procédure de [Ajout d’activités Windows PowerShell pour Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) pour créer un projet de flux de travail et ajouter les activités à partir de la [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) et [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) des assemblys de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="2f1d0-108">Ajouter System.Management.Automation Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities et Microsoft.PowerShell.Commands.Management concernant le projet en tant que les assemblys de référence.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="2f1d0-109">Ajout d’activités au flux de travail</span><span class="sxs-lookup"><span data-stu-id="2f1d0-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="2f1d0-110">Ajouter un **séquence** activité au flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="2f1d0-111">Créer un argument nommé `ComputerName` avec un type d’argument de `String[]`.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="2f1d0-112">Cet argument représente les noms des ordinateurs à vérifier et à joindre.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="2f1d0-113">Créer un argument nommé `DomainCred` de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="2f1d0-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="2f1d0-114">Cet argument représente les informations d’identification de domaine d’un compte de domaine qui est autorisé à joindre un ordinateur au domaine.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="2f1d0-115">Créer un argument nommé `MachineCred` de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="2f1d0-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="2f1d0-116">Cet argument représente les informations d’identification d’un administrateur sur les ordinateurs à vérifier et à joindre.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="2f1d0-117">Ajouter un **ParallelForEach** activité à l’intérieur du **séquence** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="2f1d0-118">Entrez `comp` et `ComputerName` dans les zones de texte afin que la boucle effectue une itération dans les éléments de la `ComputerName` tableau.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="2f1d0-119">Ajouter un **séquence** activité au corps de la **ParallelForEach** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="2f1d0-120">Définir le **DisplayName** propriété de la séquence à `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="2f1d0-121">Ajouter un **GetWmiObject** activité à la **JoinDomain** séquence.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="2f1d0-122">Modifier les propriétés de la **GetWmiObject** activité comme suit.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="2f1d0-123">Propriété</span><span class="sxs-lookup"><span data-stu-id="2f1d0-123">Property</span></span>|<span data-ttu-id="2f1d0-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="2f1d0-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="2f1d0-125">**Class**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-125">**Class**</span></span>|<span data-ttu-id="2f1d0-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="2f1d0-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="2f1d0-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-127">**PSComputerName**</span></span>|<span data-ttu-id="2f1d0-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="2f1d0-128">{comp}</span></span>|
   |<span data-ttu-id="2f1d0-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-129">**PSCredential**</span></span>|<span data-ttu-id="2f1d0-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="2f1d0-130">MachineCred</span></span>|

9. <span data-ttu-id="2f1d0-131">Ajouter un **AddComputer** activité à la **JoinDomain** séquence après le **GetWmiObject** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="2f1d0-132">Modifier les propriétés de la **AddComputer** activité comme suit.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="2f1d0-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="2f1d0-133">Property</span></span>|<span data-ttu-id="2f1d0-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="2f1d0-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="2f1d0-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-135">**ComputerName**</span></span>|<span data-ttu-id="2f1d0-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="2f1d0-136">{comp}</span></span>|
    |<span data-ttu-id="2f1d0-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-137">**DomainCredential**</span></span>|<span data-ttu-id="2f1d0-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="2f1d0-138">DomainCred</span></span>|

11. <span data-ttu-id="2f1d0-139">Ajouter un **RestartComputer** activité à la **JoinDomain** séquence après le **AddComputer** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="2f1d0-140">Modifier les propriétés de la **RestartComputer** activité comme suit.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="2f1d0-141">Propriété</span><span class="sxs-lookup"><span data-stu-id="2f1d0-141">Property</span></span>|<span data-ttu-id="2f1d0-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="2f1d0-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="2f1d0-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-143">**ComputerName**</span></span>|<span data-ttu-id="2f1d0-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="2f1d0-144">{comp}</span></span>|
    |<span data-ttu-id="2f1d0-145">**Informations d’identification**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-145">**Credential**</span></span>|<span data-ttu-id="2f1d0-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="2f1d0-146">MachineCred</span></span>|
    |<span data-ttu-id="2f1d0-147">**Pour**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-147">**For**</span></span>|<span data-ttu-id="2f1d0-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f1d0-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="2f1d0-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="2f1d0-149">**Force**</span></span>|<span data-ttu-id="2f1d0-150">True</span><span class="sxs-lookup"><span data-stu-id="2f1d0-150">True</span></span>|
    |<span data-ttu-id="2f1d0-151">Wait</span><span class="sxs-lookup"><span data-stu-id="2f1d0-151">Wait</span></span>|<span data-ttu-id="2f1d0-152">True</span><span class="sxs-lookup"><span data-stu-id="2f1d0-152">True</span></span>|
    |<span data-ttu-id="2f1d0-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="2f1d0-153">PSComputerName</span></span>|<span data-ttu-id="2f1d0-154">{""}</span><span class="sxs-lookup"><span data-stu-id="2f1d0-154">{""}</span></span>|

13. <span data-ttu-id="2f1d0-155">Ajouter un **GetWmiObject** activité à la **JoinDomain** séquence après le **RestartComputer** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="2f1d0-156">Modifier ses propriétés pour être le même que le précédent **GetWmiObject** activité.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="2f1d0-157">Lorsque vous avez terminé les procédures, la fenêtre de conception de flux de travail doit ressembler à ceci.</span><span class="sxs-lookup"><span data-stu-id="2f1d0-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="2f1d0-158">![XAML JoinDomain dans le Concepteur de flux de travail](../media/joindomainworkflow.png)
    ![XAML JoinDomain dans le Concepteur de flux de travail](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="2f1d0-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>