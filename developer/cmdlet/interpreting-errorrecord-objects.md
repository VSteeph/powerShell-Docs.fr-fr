---
title: Interprétation des objets d’ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: d77e4daf25bfcd5e76c184f6dbdb619368627bfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857225"
---
# <a name="interpreting-errorrecord-objects"></a><span data-ttu-id="3acc2-102">Interprétation des objets ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="3acc2-102">Interpreting ErrorRecord Objects</span></span>

<span data-ttu-id="3acc2-103">Dans la plupart des cas, un [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet représente une erreur sans fin d’exécution générée par une commande ou un script.</span><span class="sxs-lookup"><span data-stu-id="3acc2-103">In most cases, an [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object represents a non-terminating error generated by a command or script.</span></span> <span data-ttu-id="3acc2-104">Arrêt des erreurs permettre également spécifier les informations supplémentaires dans ErrorRecord via le [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.</span><span class="sxs-lookup"><span data-stu-id="3acc2-104">Terminating errors can also specify the additional information in an ErrorRecord via the [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.</span></span>

<span data-ttu-id="3acc2-105">Si vous souhaitez écrire un gestionnaire d’erreurs dans votre script ou un ordinateur hôte pour gérer les erreurs spécifiques qui se produisent pendant l’exécution de commande ou un script, vous devez interpréter les [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet afin de déterminer si elle représente la classe d’erreur que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="3acc2-105">If you want to write an error handler in your script or a host to handle specific errors that occur during command or script execution, you must interpret the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object to determine whether it represents the class of error that you want to handle.</span></span>

<span data-ttu-id="3acc2-106">Quand une applet de commande rencontre une fin ou erreur sans fin d’exécution, il doit créer un enregistrement d’erreur qui décrit la condition d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-106">When a cmdlet encounters a terminating or non-terminating error, it should create an error record that describes the error condition.</span></span> <span data-ttu-id="3acc2-107">L’application hôte doit examiner ces enregistrements d’erreur et effectuer toute action atténuera l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-107">The host application must investigate these error records and perform whatever action will mitigate the error.</span></span> <span data-ttu-id="3acc2-108">L’application hôte doit également rechercher des enregistrements d’erreur pour les erreurs sans fin d’exécution qui n’a pas pu traiter un enregistrement mais qui ont été en mesure de continuer, et elle doit examiner les enregistrements d’erreur pour les erreurs avec fin d’exécution qui a provoqué le pipeline à arrêter.</span><span class="sxs-lookup"><span data-stu-id="3acc2-108">The host application must also investigate error records for nonterminating errors that failed to process a record but were able to continue, and it must investigate error records for terminating errors that caused the pipeline to stop.</span></span>

> [!NOTE]
> <span data-ttu-id="3acc2-109">Pour les erreurs avec fin d’exécution, l’applet de commande appelle le [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3acc2-109">For terminating errors, the cmdlet calls the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="3acc2-110">Pour les erreurs sans fin d’exécution, l’applet de commande appelle le [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3acc2-110">For non-terminating errors, the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span>

## <a name="error-record-design"></a><span data-ttu-id="3acc2-111">Conception enregistrements d’erreur</span><span class="sxs-lookup"><span data-stu-id="3acc2-111">Error Record Design</span></span>

<span data-ttu-id="3acc2-112">Enregistrements d’erreur sont conçus pour fournir des informations d’erreur supplémentaires qui ne sont pas disponibles dans les exceptions tout en garantissant que les informations combinés dans chaque enregistrement d’erreur sont uniques.</span><span class="sxs-lookup"><span data-stu-id="3acc2-112">Error records are designed to provide additional error information that is not available in exceptions while ensuring that the combined information in each error record is unique.</span></span> <span data-ttu-id="3acc2-113">Ce caractère unique permet à l’application hôte inspecter les différentes parties de l’enregistrement d’erreur afin qu’il peut identifier la condition d’erreur et l’action de l’hôte doit prendre.</span><span class="sxs-lookup"><span data-stu-id="3acc2-113">This uniqueness allows the host application to inspect the different parts of the error record so that it can identify the error condition and the action the host must take.</span></span>

## <a name="interpreting-error-records"></a><span data-ttu-id="3acc2-114">Interprétation des enregistrements d’erreur</span><span class="sxs-lookup"><span data-stu-id="3acc2-114">Interpreting Error Records</span></span>

<span data-ttu-id="3acc2-115">Vous pouvez examiner plusieurs parties de l’enregistrement d’erreur pour identifier l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-115">You can review several parts of the error record to identify the error.</span></span> <span data-ttu-id="3acc2-116">Ces parties sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3acc2-116">These parts include the following:</span></span>

- <span data-ttu-id="3acc2-117">La catégorie d’erreur</span><span class="sxs-lookup"><span data-stu-id="3acc2-117">The error category</span></span>

- <span data-ttu-id="3acc2-118">L’exception d’erreur</span><span class="sxs-lookup"><span data-stu-id="3acc2-118">The error exception</span></span>

- <span data-ttu-id="3acc2-119">L’identificateur d’erreur complet (FQID)</span><span class="sxs-lookup"><span data-stu-id="3acc2-119">The fully qualified error identifier (FQID)</span></span>

- <span data-ttu-id="3acc2-120">Autres informations</span><span class="sxs-lookup"><span data-stu-id="3acc2-120">Other information</span></span>

### <a name="the-error-category"></a><span data-ttu-id="3acc2-121">La catégorie d’erreur</span><span class="sxs-lookup"><span data-stu-id="3acc2-121">The Error Category</span></span>

<span data-ttu-id="3acc2-122">La catégorie d’erreur de l’enregistrement d’erreur est une des constantes prédéfinies fournies par le [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) énumération.</span><span class="sxs-lookup"><span data-stu-id="3acc2-122">The error category of the error record is one of the predefined constants provided by the [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="3acc2-123">Ces informations sont disponibles via le [System.Management.Automation.Errorrecord.Categoryinfo\*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriété de la [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet.</span><span class="sxs-lookup"><span data-stu-id="3acc2-123">This information  is available through the [System.Management.Automation.Errorrecord.Categoryinfo\*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) property of the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.</span></span>

<span data-ttu-id="3acc2-124">L’applet de commande permettre spécifier les catégories CloseError OpenError, InvalidType, ReadError et WriteError et autres catégories d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-124">The cmdlet can specify the CloseError, OpenError, InvalidType, ReadError, and WriteError categories, and other error categories.</span></span> <span data-ttu-id="3acc2-125">L’application hôte peut utiliser la catégorie d’erreur pour capturer des groupes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="3acc2-125">The host application can use the error category to capture groups of errors.</span></span>

### <a name="the-exception"></a><span data-ttu-id="3acc2-126">L’Exception</span><span class="sxs-lookup"><span data-stu-id="3acc2-126">The Exception</span></span>

<span data-ttu-id="3acc2-127">L’exception incluse dans l’enregistrement d’erreur est fournie par l’applet de commande et est accessible via la [System.Management.Automation.Errorrecord.Exception\*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriété de la [ System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet.</span><span class="sxs-lookup"><span data-stu-id="3acc2-127">The exception included in the error record is provided by the cmdlet and can be accessed through the [System.Management.Automation.Errorrecord.Exception\*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) property of the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.</span></span>

<span data-ttu-id="3acc2-128">Les applications hôte peuvent utiliser le `is` mot clé pour identifier l’exception d’une classe spécifique ou d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3acc2-128">Host applications can use the `is` keyword to identify that the exception is of a specific class or of a derived class.</span></span> <span data-ttu-id="3acc2-129">Il est préférable de branche sur le type d’exception, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3acc2-129">It is better to branch on the exception type, as shown in the following example.</span></span>

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

<span data-ttu-id="3acc2-130">De cette façon, vous interceptez les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="3acc2-130">This way, you catch the derived classes.</span></span> <span data-ttu-id="3acc2-131">Toutefois, il existe des problèmes si l’exception est désérialisée.</span><span class="sxs-lookup"><span data-stu-id="3acc2-131">However, there are problems if the exception is deserialized.</span></span>

### <a name="the-fqid"></a><span data-ttu-id="3acc2-132">Le FQID</span><span class="sxs-lookup"><span data-stu-id="3acc2-132">The FQID</span></span>

<span data-ttu-id="3acc2-133">Le FQID est les informations plus spécifiques, que vous pouvez utiliser pour identifier l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-133">The FQID is the most specific information you can use to identify the error.</span></span> <span data-ttu-id="3acc2-134">C’est une chaîne qui inclut un identificateur défini par l’applet de commande, le nom de la classe de l’applet de commande et la source qui a signalé l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-134">It is a string that includes a cmdlet-defined identifier, the name of the cmdlet class, and the source that reported the error.</span></span> <span data-ttu-id="3acc2-135">En règle générale, un enregistrement d’erreur est analogue à un enregistrement d’événement d’un journal des événements de Windows.</span><span class="sxs-lookup"><span data-stu-id="3acc2-135">In general, an error record is analogous to an event record of a Windows Event log.</span></span> <span data-ttu-id="3acc2-136">Le FQID est analogue au tuple suivant, qui identifie la classe de l’enregistrement d’événement : (*nom_journal*, *source*, *ID d’événement*).</span><span class="sxs-lookup"><span data-stu-id="3acc2-136">The FQID is analogous to the following tuple, which identifies the class of the event record: (*log name*, *source*, *event ID*).</span></span>

<span data-ttu-id="3acc2-137">Le FQID est conçu pour être inspecté sous forme de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="3acc2-137">The FQID is designed to be inspected as a single string.</span></span> <span data-ttu-id="3acc2-138">Toutefois, le cas existent dans lequel l’identificateur de l’erreur est conçu pour être analysée par l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="3acc2-138">However, cases exist in which the error identifier is designed to be parsed by the host application.</span></span> <span data-ttu-id="3acc2-139">L’exemple suivant est un identificateur d’erreur complet correct.</span><span class="sxs-lookup"><span data-stu-id="3acc2-139">The following example is a well-formed fully qualified error identifier.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

<span data-ttu-id="3acc2-140">Dans l’exemple précédent, le premier jeton est l’identificateur de l’erreur, qui est suivie par le nom de la classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3acc2-140">In the previous example, the first token is the error identifier, which is followed by the name of the cmdlet class.</span></span> <span data-ttu-id="3acc2-141">Identificateur de l’erreur peut être un jeton unique, ou il peut être un identificateur séparés par des points qui permet le branchement sur l’inspection de l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-141">The error identifier can be a single token, or it can be a dot-separated identifier that allows for branching on inspection of the identifier.</span></span> <span data-ttu-id="3acc2-142">N’utilisez pas d’espace blanc ou des signes de ponctuation dans l’identificateur de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-142">Do not use white space or punctuation in the error identifier.</span></span> <span data-ttu-id="3acc2-143">Il est particulièrement important de ne pas utiliser une virgule ; une virgule est utilisée par Windows PowerShell pour séparer l’identificateur et le nom de la classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3acc2-143">It is especially important not to use a comma; a comma is used by Windows PowerShell to separate the identifier and the cmdlet class name.</span></span>

### <a name="other-information"></a><span data-ttu-id="3acc2-144">Autres informations</span><span class="sxs-lookup"><span data-stu-id="3acc2-144">Other Information</span></span>

<span data-ttu-id="3acc2-145">Le [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objet peut également fournir des informations qui décrivent l’environnement dans lequel l’erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3acc2-145">The [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object might also provide information that describes the environment in which the error occurred.</span></span> <span data-ttu-id="3acc2-146">Ces informations incluent des éléments tels que les détails de l’erreur, informations d’appel et l’objet cible qui était traitée lorsque l’erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3acc2-146">This information includes items such as error details, invocation information, and the target object that was being processed when the error occurred.</span></span> <span data-ttu-id="3acc2-147">Bien que ces informations peuvent être utiles à l’application hôte, il n’est pas généralement utilisé pour identifier l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3acc2-147">Although this information might be useful to the host application, it is not typically used to identify the error.</span></span> <span data-ttu-id="3acc2-148">Ces informations sont disponibles via les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3acc2-148">This information is available through the following properties:</span></span>

[<span data-ttu-id="3acc2-149">System.Management.Automation.Errorrecord.Errordetails\*</span><span class="sxs-lookup"><span data-stu-id="3acc2-149">System.Management.Automation.Errorrecord.Errordetails\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[<span data-ttu-id="3acc2-150">System.Management.Automation.Errorrecord.Invocationinfo\*</span><span class="sxs-lookup"><span data-stu-id="3acc2-150">System.Management.Automation.Errorrecord.Invocationinfo\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[<span data-ttu-id="3acc2-151">System.Management.Automation.Errorrecord.Targetobject\*</span><span class="sxs-lookup"><span data-stu-id="3acc2-151">System.Management.Automation.Errorrecord.Targetobject\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a><span data-ttu-id="3acc2-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3acc2-152">See Also</span></span>

[<span data-ttu-id="3acc2-153">System.Management.Automation.Errorrecord</span><span class="sxs-lookup"><span data-stu-id="3acc2-153">System.Management.Automation.Errorrecord</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord)

[<span data-ttu-id="3acc2-154">System.Management.Automation.Errorcategory</span><span class="sxs-lookup"><span data-stu-id="3acc2-154">System.Management.Automation.Errorcategory</span></span>](/dotnet/api/System.Management.Automation.ErrorCategory)

[<span data-ttu-id="3acc2-155">System.Management.Automation.Errorcategoryinfo</span><span class="sxs-lookup"><span data-stu-id="3acc2-155">System.Management.Automation.Errorcategoryinfo</span></span>](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[<span data-ttu-id="3acc2-156">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="3acc2-156">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="3acc2-157">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="3acc2-157">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="3acc2-158">Ajout de rapport d’erreurs à votre applet de commande sans terminaison</span><span class="sxs-lookup"><span data-stu-id="3acc2-158">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="3acc2-159">Rapport d’erreurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3acc2-159">Windows PowerShell Error Reporting</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="3acc2-160">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3acc2-160">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)