---
title: Tâches en arrière-plan | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857165"
---
# <a name="background-jobs"></a><span data-ttu-id="7c8bb-102">Travaux en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c8bb-102">Background Jobs</span></span>

<span data-ttu-id="7c8bb-103">Applets de commande peut exécuter leur action en interne ou un PowerShell Windows*tâche en arrière-plan*.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="7c8bb-104">Quand une applet de commande s’exécute en tant que tâche en arrière-plan, le travail est effectué de façon asynchrone dans son propre thread séparé à partir du thread de pipeline à l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="7c8bb-105">Du point de vue de l’utilisateur, quand une applet de commande s’exécute en tant que tâche en arrière-plan, l’invite de commande retourne immédiatement même si le travail prend un certain temps, et l’utilisateur peut continuer sans interruption pendant l’exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="7c8bb-106">Tâches en arrière-plan, les travaux d’enfant et le référentiel de tâches</span><span class="sxs-lookup"><span data-stu-id="7c8bb-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="7c8bb-107">L’objet de travail qui est retourné par les applets de commande qui prennent en charge les tâches en arrière-plan définit la tâche.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="7c8bb-108">(Le [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) applet de commande renvoie également un objet de traitement.) Le nom de la tâche, un identificateur qui est utilisé pour spécifier le travail, les informations d’état et les tâches enfant sont inclus dans cette définition.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="7c8bb-109">La tâche n’effectue aucun du travail.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-109">The job does not perform any of the work.</span></span> <span data-ttu-id="7c8bb-110">Chaque tâche en arrière-plan a au moins une tâche enfant, car la tâche enfant effectue le travail réel.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="7c8bb-111">Lorsque vous exécutez une applet de commande afin que le travail est effectué en tant que tâche en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfant à un référentiel commun, appelé le *référentiel de tâches*.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>
<span data-ttu-id="7c8bb-112">L’objet de travail qui est retourné par les applets de commande qui prennent en charge les tâches en arrière-plan définit la tâche.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-112">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="7c8bb-113">(Le [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) applet de commande renvoie également un objet de traitement.) Le nom de la tâche, un identificateur qui est utilisé pour spécifier le travail, les informations d’état et les tâches enfant sont inclus dans cette définition.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-113">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="7c8bb-114">La tâche n’effectue aucun du travail.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-114">The job does not perform any of the work.</span></span> <span data-ttu-id="7c8bb-115">Chaque tâche en arrière-plan a au moins une tâche enfant, car la tâche enfant effectue le travail réel.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-115">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="7c8bb-116">Lorsque vous exécutez une applet de commande afin que le travail est effectué en tant que tâche en arrière-plan, l’applet de commande doit ajouter le travail et les tâches enfant à un référentiel commun, appelé le *référentiel de tâches*.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-116">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="7c8bb-117">Pour plus d’informations sur la gestion des tâches en arrière-plan sur la ligne de commande, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c8bb-117">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="7c8bb-118">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="7c8bb-118">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="7c8bb-119">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="7c8bb-119">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="7c8bb-120">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="7c8bb-120">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="7c8bb-121">Écriture d’une applet de commande qui s’exécute en tant que tâche en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c8bb-121">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="7c8bb-122">Pour écrire une applet de commande qui peut être exécuté en tant que tâche en arrière-plan, vous devez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c8bb-122">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="7c8bb-123">Définir un `asJob` paramètre de commutateur afin que l’utilisateur peut décider s’il faut exécuter l’applet de commande en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-123">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="7c8bb-124">Créer un objet qui dérive de la [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-124">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="7c8bb-125">Cet objet peut être un objet de tâche personnalisé ou un objet de travail fournis par Windows PowerShell, par exemple un [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objet.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-125">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="7c8bb-126">Dans une méthode de traitement enregistrement, ajoutez un `if` instruction qui détecte si l’applet de commande doit s’exécuter en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-126">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="7c8bb-127">Pour les objets de tâche personnalisé, implémentez la classe de tâche.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-127">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="7c8bb-128">Retourner les objets appropriés, selon que l’applet de commande est exécutée comme une tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-128">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="7c8bb-129">Pour obtenir un exemple de code, consultez [comment les tâches de prise en charge](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="7c8bb-129">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="7c8bb-130">API liées au travail en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="7c8bb-130">Background Job-Related APIs</span></span>

<span data-ttu-id="7c8bb-131">Les API suivantes sont fournies par PowerShell de Windows pour gérer les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-131">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="7c8bb-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) dérive des objets de tâche personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="7c8bb-133">Il s’agit d’une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-133">This is an abstract class.</span></span>

<span data-ttu-id="7c8bb-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gère et fournit des informations sur les tâches d’arrière-plan active actuelle.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="7c8bb-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) définit l’état de la tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="7c8bb-136">Les États incluent démarré et arrêté en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-136">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="7c8bb-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fournit des informations sur l’état d’une tâche en arrière-plan et, si l’état de la dernière modification a été provoqué par une erreur, la raison pour laquelle le travail est passé à son état actuel.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="7c8bb-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fournit les arguments pour un événement qui est déclenché lorsqu’une tâche en arrière-plan change d’état.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="7c8bb-139">Applets de commande PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="7c8bb-139">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="7c8bb-140">Les applets de commande suivantes sont fournies par PowerShell de Windows pour gérer les tâches en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-140">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="7c8bb-141">Get-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-141">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="7c8bb-142">Obtient les tâches en arrière-plan Windows PowerShell qui s'exécutent dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-142">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="7c8bb-143">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-143">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="7c8bb-144">Obtient les résultats des tâches Windows PowerShell en arrière-plan dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-144">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="7c8bb-145">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-145">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="7c8bb-146">Supprime une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-146">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7c8bb-147">Start-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-147">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="7c8bb-148">Démarre une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-148">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7c8bb-149">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-149">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="7c8bb-150">Arrête une tâche en arrière-plan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-150">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7c8bb-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="7c8bb-151">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="7c8bb-152">Supprime l'invite de commandes jusqu'à ce qu'une ou toutes les tâches en arrière-plan Windows PowerShell en cours d'exécution dans la session soient terminées.</span><span class="sxs-lookup"><span data-stu-id="7c8bb-152">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c8bb-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c8bb-153">See Also</span></span>

[<span data-ttu-id="7c8bb-154">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c8bb-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)