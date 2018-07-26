---
ms.date: 06/12/2018
keywords: wmf,powershell,configuration
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943605"
---
# <a name="windows-management-framework"></a><span data-ttu-id="425d7-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="425d7-103">Windows Management Framework</span></span>

<span data-ttu-id="425d7-104">Windows Management Framework (WMF) fournit une interface de gestion cohérente pour Windows.</span><span class="sxs-lookup"><span data-stu-id="425d7-104">Windows Management Framework (WMF) provides a consistent management interface for Windows.</span></span> <span data-ttu-id="425d7-105">WMF offre un moyen fluide de gérer différentes versions du client Windows et de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="425d7-105">WMF provides a seamless way to manage various versions of Windows client and Windows Server.</span></span> <span data-ttu-id="425d7-106">Les packages du programme d’installation de WMF contiennent les mises à jour des fonctionnalités de gestion qui sont disponibles pour les anciennes versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="425d7-106">WMF installer packages contain updates to management functionality and are available for older versions of Windows.</span></span>

<span data-ttu-id="425d7-107">L’installation de WMF ajoute ou met à jour les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="425d7-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="425d7-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="425d7-108">Windows PowerShell</span></span>
- <span data-ttu-id="425d7-109">Configuration de l’état souhaité de Windows PowerShell (DSC)</span><span class="sxs-lookup"><span data-stu-id="425d7-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="425d7-110">Windows PowerShell Integrated Script Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="425d7-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="425d7-111">Windows Remote Management (WinRM)</span><span class="sxs-lookup"><span data-stu-id="425d7-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="425d7-112">Infrastructure de gestion Windows (WMI, Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="425d7-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="425d7-113">Windows PowerShell Web Services (Extension ISS Management OData)</span><span class="sxs-lookup"><span data-stu-id="425d7-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="425d7-114">Journalisation de l’inventaire logiciel</span><span class="sxs-lookup"><span data-stu-id="425d7-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="425d7-115">Fournisseur CIM de Gestionnaire de serveur</span><span class="sxs-lookup"><span data-stu-id="425d7-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="425d7-116">Notes de publication de WMF</span><span class="sxs-lookup"><span data-stu-id="425d7-116">WMF Release Notes</span></span>

<span data-ttu-id="425d7-117">Pour en savoir plus sur les diverses améliorations apportées à PowerShell et d’autres composants d’une version donnée de WMF, consultez les liens ci-dessous pour consulter les notes de publication :</span><span class="sxs-lookup"><span data-stu-id="425d7-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="425d7-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="425d7-118">WMF 5.1</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="425d7-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="425d7-119">WMF 5.0</span></span>](5.0/releasenotes.md)
- [<span data-ttu-id="425d7-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="425d7-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="425d7-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="425d7-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="425d7-122">Disponibilité de WMF sur les systèmes d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="425d7-122">WMF Availability Across Windows Operating Systems</span></span>

|<span data-ttu-id="425d7-123">Version du système d'exploitation</span><span class="sxs-lookup"><span data-stu-id="425d7-123">Operating System Version</span></span>  |<span data-ttu-id="425d7-124">[WMF 5.1][]</span><span class="sxs-lookup"><span data-stu-id="425d7-124">[WMF 5.1][]</span></span> |<span data-ttu-id="425d7-125">[WMF 5.0][]</span><span class="sxs-lookup"><span data-stu-id="425d7-125">[WMF 5.0][]</span></span> |<span data-ttu-id="425d7-126">[WMF 4.0][]</span><span class="sxs-lookup"><span data-stu-id="425d7-126">[WMF 4.0][]</span></span> |<span data-ttu-id="425d7-127">[WMF 3.0][]</span><span class="sxs-lookup"><span data-stu-id="425d7-127">[WMF 3.0][]</span></span>  |<span data-ttu-id="425d7-128">[WMF 2.0][]</span><span class="sxs-lookup"><span data-stu-id="425d7-128">[WMF 2.0][]</span></span> |
|--------------------------|------------|------------|------------|-------------|------------|
|<span data-ttu-id="425d7-129">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="425d7-129">Windows Server 2016</span></span>       |<span data-ttu-id="425d7-130">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-130">Ships in-box</span></span>|            |            |             |            |
|<span data-ttu-id="425d7-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="425d7-131">Windows 10</span></span>                |<span data-ttu-id="425d7-132">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-132">Ships in-box</span></span>|<span data-ttu-id="425d7-133">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-133">Ships in-box</span></span>|            |             |            |
|<span data-ttu-id="425d7-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="425d7-134">Windows Server 2012 R2</span></span>    |<span data-ttu-id="425d7-135">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-135">Yes</span></span>         |<span data-ttu-id="425d7-136">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-136">Yes</span></span>         |<span data-ttu-id="425d7-137">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-137">Ships in-box</span></span>|             |            |
|<span data-ttu-id="425d7-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="425d7-138">Windows 8.1</span></span>               |<span data-ttu-id="425d7-139">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-139">Yes</span></span>         |<span data-ttu-id="425d7-140">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-140">Yes</span></span>         |<span data-ttu-id="425d7-141">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-141">Ships in-box</span></span>|             |            |
|<span data-ttu-id="425d7-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="425d7-142">Windows Server 2012</span></span>       |<span data-ttu-id="425d7-143">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-143">Yes</span></span>         |<span data-ttu-id="425d7-144">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-144">Yes</span></span>         |<span data-ttu-id="425d7-145">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-145">Yes</span></span>         |<span data-ttu-id="425d7-146">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-146">Ships in-box</span></span> |            |
|<span data-ttu-id="425d7-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="425d7-147">Windows 8</span></span>                 |            |            |            |<span data-ttu-id="425d7-148">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-148">Ships in-box</span></span> |            |
|<span data-ttu-id="425d7-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="425d7-149">Windows Server 2008 R2 SP1</span></span>|<span data-ttu-id="425d7-150">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-150">Yes</span></span>         |<span data-ttu-id="425d7-151">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-151">Yes</span></span>         |<span data-ttu-id="425d7-152">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-152">Yes</span></span>         |<span data-ttu-id="425d7-153">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-153">Yes</span></span>          |<span data-ttu-id="425d7-154">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-154">Ships in-box</span></span>|
|<span data-ttu-id="425d7-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="425d7-155">Windows 7 SP1</span></span>             |<span data-ttu-id="425d7-156">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-156">Yes</span></span>         |<span data-ttu-id="425d7-157">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-157">Yes</span></span>         |<span data-ttu-id="425d7-158">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-158">Yes</span></span>         |<span data-ttu-id="425d7-159">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-159">Yes</span></span>          |<span data-ttu-id="425d7-160">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="425d7-160">Ships in-box</span></span>|
|<span data-ttu-id="425d7-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="425d7-161">Windows Server 2008 SP2</span></span>   |            |            |            |<span data-ttu-id="425d7-162">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-162">Yes</span></span>          |<span data-ttu-id="425d7-163">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-163">Yes</span></span>         |
|<span data-ttu-id="425d7-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="425d7-164">Windows Vista</span></span>             |            |            |            |             |<span data-ttu-id="425d7-165">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-165">Yes</span></span>         |
|<span data-ttu-id="425d7-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="425d7-166">Windows Server 2003</span></span>       |            |            |            |             |<span data-ttu-id="425d7-167">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-167">Yes</span></span>         |
|<span data-ttu-id="425d7-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="425d7-168">Windows XP</span></span>                |            |            |            |<span data-ttu-id="425d7-169">Oui</span><span class="sxs-lookup"><span data-stu-id="425d7-169">Yes</span></span>          |            |

<span data-ttu-id="425d7-170">**Fourni par défaut** : les fonctionnalités de la version spécifiée de WMF ont été fournies dans la version indiquée du client Windows ou de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="425d7-170">**Ships in-box**: The features of the specified version of WMF were shipped in the indicated version of Windows client or Windows Server.</span></span>

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download