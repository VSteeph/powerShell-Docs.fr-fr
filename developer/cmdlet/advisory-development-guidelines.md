---
title: Directives de développement Advisory | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 97a2d3587f8f69edc92150474e94a620ff9a2f71
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854545"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="16bb2-102">Instructions dont le suivi est conseillé pour le développement</span><span class="sxs-lookup"><span data-stu-id="16bb2-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="16bb2-103">Cette section décrit les instructions qui vous aideront à assurer une bonne expérience des utilisateurs et de développement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="16bb2-104">Parfois, ils peuvent s’appliquer, et parfois ils ne le peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="16bb2-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="16bb2-105">Règles de conception</span><span class="sxs-lookup"><span data-stu-id="16bb2-105">Design Guidelines</span></span>

- [<span data-ttu-id="16bb2-106">Prend en charge un paramètre InputObject (AD01)</span><span class="sxs-lookup"><span data-stu-id="16bb2-106">Support an InputObject Parameter (AD01)</span></span>](./advisory-development-guidelines.md#AD01)

- [<span data-ttu-id="16bb2-107">Prise en charge le paramètre Force (AD02)</span><span class="sxs-lookup"><span data-stu-id="16bb2-107">Support the Force Parameter (AD02)</span></span>](./advisory-development-guidelines.md#AD02)

- [<span data-ttu-id="16bb2-108">Gérer les informations d’identification via Windows PowerShell (AD03)</span><span class="sxs-lookup"><span data-stu-id="16bb2-108">Handle Credentials Through Windows PowerShell (AD03)</span></span>](./advisory-development-guidelines.md#AD03)

- [<span data-ttu-id="16bb2-109">Prend en charge les paramètres d’encodage (AD04)</span><span class="sxs-lookup"><span data-stu-id="16bb2-109">Support Encoding Parameters (AD04)</span></span>](./advisory-development-guidelines.md#AD04)

- [<span data-ttu-id="16bb2-110">Applets de commande de test doit retourner une valeur booléenne (AD05)</span><span class="sxs-lookup"><span data-stu-id="16bb2-110">Test Cmdlets Should Return a Boolean (AD05)</span></span>](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a><span data-ttu-id="16bb2-111">Instructions de code</span><span class="sxs-lookup"><span data-stu-id="16bb2-111">Code Guidelines</span></span>

- [<span data-ttu-id="16bb2-112">Suivez les Conventions de nom de la classe de l’applet de commande (AC01)</span><span class="sxs-lookup"><span data-stu-id="16bb2-112">Follow Cmdlet Class Naming Conventions (AC01)</span></span>](./advisory-development-guidelines.md#AC01)

- [<span data-ttu-id="16bb2-113">Si aucune entrée de Pipeline ne substituer la méthode BeginProcessing (AC02)</span><span class="sxs-lookup"><span data-stu-id="16bb2-113">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>](./advisory-development-guidelines.md#AC02)

- [<span data-ttu-id="16bb2-114">Pour gérer les demandes d’arrêt substituent la méthode StopProcessing (AC03)</span><span class="sxs-lookup"><span data-stu-id="16bb2-114">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>](./advisory-development-guidelines.md#AC03)

- [<span data-ttu-id="16bb2-115">Implémenter l’Interface IDisposable (AC04)</span><span class="sxs-lookup"><span data-stu-id="16bb2-115">Implement the IDisposable Interface (AC04)</span></span>](./advisory-development-guidelines.md#AC04)

- [<span data-ttu-id="16bb2-116">Utiliser des Types de paramètres de sérialisation conviviale (AC05)</span><span class="sxs-lookup"><span data-stu-id="16bb2-116">Use Serialization-friendly Parameter Types (AC05)</span></span>](./advisory-development-guidelines.md#AC05)

- [<span data-ttu-id="16bb2-117">Utilisez SecureString pour les données sensibles (AC06)</span><span class="sxs-lookup"><span data-stu-id="16bb2-117">Use SecureString for Sensitive Data (AC06)</span></span>](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a><span data-ttu-id="16bb2-118">Règles de conception</span><span class="sxs-lookup"><span data-stu-id="16bb2-118">Design Guidelines</span></span>

<span data-ttu-id="16bb2-119">Les instructions suivantes doivent être considérées lors de la conception des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-119">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="16bb2-120">Lorsque vous trouvez une indication de conception qui s’appliquent à votre situation, veillez à consulter les instructions de Code pour obtenir des instructions similaires.</span><span class="sxs-lookup"><span data-stu-id="16bb2-120">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="16bb2-121">Prend en charge un paramètre InputObject (AD01)</span><span class="sxs-lookup"><span data-stu-id="16bb2-121">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="16bb2-122">Étant donné que Windows PowerShell fonctionne directement avec les objets Microsoft .NET Framework, un objet .NET Framework est souvent disponible que correspond exactement le type de l’utilisateur doit effectuer une opération particulière.</span><span class="sxs-lookup"><span data-stu-id="16bb2-122">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="16bb2-123">`InputObject` est le nom standard pour un paramètre qui accepte un tel objet en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="16bb2-123">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="16bb2-124">Par exemple, l’exemple **Stop-Process** applet de commande dans le [StopProc didacticiel](./stopproc-tutorial.md) définit un `InputObject` paramètre de type de processus qui prend en charge de l’entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="16bb2-124">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="16bb2-125">L’utilisateur peut obtenir un ensemble d’objets de processus, les manipuler pour sélectionner les objets spécifiques à arrêter, puis les passer à la **Stop-Process** applet de commande directement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-125">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="16bb2-126">Prise en charge le paramètre Force (AD02)</span><span class="sxs-lookup"><span data-stu-id="16bb2-126">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="16bb2-127">Parfois, une applet de commande doit protéger l’utilisateur d’effectuer une opération demandée.</span><span class="sxs-lookup"><span data-stu-id="16bb2-127">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="16bb2-128">Ce type une applet de commande doit prendre en charge un `Force` paramètre pour autoriser l’utilisateur de substituer cette protection si l’utilisateur dispose des autorisations nécessaires pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="16bb2-128">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="16bb2-129">Par exemple, le [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) applet de commande ne supprime pas normalement un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="16bb2-129">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="16bb2-130">Toutefois, cette applet de commande prend en charge un `Force` paramètre pour un utilisateur peut forcer la suppression d’un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="16bb2-130">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="16bb2-131">Si l’utilisateur a déjà autorisé à modifier l’attribut en lecture seule, et l’utilisateur supprime le fichier, utilisez le `Force` paramètre simplifie l’opération.</span><span class="sxs-lookup"><span data-stu-id="16bb2-131">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="16bb2-132">Toutefois, si l’utilisateur n’est pas autorisé à supprimer le fichier, le `Force` paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="16bb2-132">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="16bb2-133">Gérer les informations d’identification via Windows PowerShell (AD03)</span><span class="sxs-lookup"><span data-stu-id="16bb2-133">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="16bb2-134">Une applet de commande doit définir un `Credential` paramètre pour représenter les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="16bb2-134">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="16bb2-135">Ce paramètre doit être de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) et doit être défini à l’aide d’une déclaration d’attribut d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="16bb2-135">This parameter must be of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="16bb2-136">Cette prise en charge invite automatiquement l’utilisateur pour le nom d’utilisateur, le mot de passe ou les deux lorsqu’une information d’identification complète n’est pas fournie directement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-136">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="16bb2-137">Pour plus d’informations sur l’attribut d’informations d’identification, consultez [déclaration d’attribut d’informations d’identification](./credential-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16bb2-137">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="16bb2-138">Prend en charge les paramètres d’encodage (AD04)</span><span class="sxs-lookup"><span data-stu-id="16bb2-138">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="16bb2-139">Si votre applet de commande lit ou écrit du texte vers ou à partir d’une forme binaire, telles que l’écriture ou de lecture à partir d’un fichier dans un système de fichiers, puis votre applet de commande doit avoir le paramètre Encoding qui spécifie la façon dont le texte est encodé sous la forme binaire.</span><span class="sxs-lookup"><span data-stu-id="16bb2-139">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="16bb2-140">Applets de commande de test doit retourner une valeur booléenne (AD05)</span><span class="sxs-lookup"><span data-stu-id="16bb2-140">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="16bb2-141">Applets de commande qui effectuent des tests par rapport à leurs ressources doit retourner un [System.Boolean](/dotnet/api/System.Boolean) tapez au pipeline afin qu’ils peuvent être utilisés dans des expressions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="16bb2-141">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="16bb2-142">Instructions de code</span><span class="sxs-lookup"><span data-stu-id="16bb2-142">Code Guidelines</span></span>

<span data-ttu-id="16bb2-143">Les instructions suivantes doivent être considérées lors de l’écriture de code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-143">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="16bb2-144">Lorsque vous trouvez une indication qui s’appliquent à votre situation, veillez à examiner les règles de conception pour obtenir des instructions similaires.</span><span class="sxs-lookup"><span data-stu-id="16bb2-144">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="16bb2-145">Suivez les Conventions de nom de la classe de l’applet de commande (AC01)</span><span class="sxs-lookup"><span data-stu-id="16bb2-145">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="16bb2-146">En suivant les conventions d’affectation de noms standard, vous rendez vos applets de commande plus détectable, et vous aider à l’utilisateur de comprendre exactement ce que font les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-146">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="16bb2-147">Cette pratique est particulièrement importante pour les autres développeurs à l’aide de Windows PowerShell, car les applets de commande sont des types publics.</span><span class="sxs-lookup"><span data-stu-id="16bb2-147">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="16bb2-148">Définir une applet de commande dans le Namespace Correct</span><span class="sxs-lookup"><span data-stu-id="16bb2-148">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="16bb2-149">Vous définissez normalement la classe pour une applet de commande dans un espace de noms .NET Framework qui ajoute ». Commandes » pour l’espace de noms qui représente le produit dans lequel s’exécute l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-149">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="16bb2-150">Par exemple, les applets de commande qui sont inclus avec Windows PowerShell sont définies dans le `Microsoft.PowerShell.Commands` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="16bb2-150">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="16bb2-151">Nommez la classe d’applet de commande doit correspondre au nom de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="16bb2-151">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="16bb2-152">Lorsque vous nommez la classe .NET Framework qui implémente une applet de commande, nommez la classe «*\<verbe >**\<Noun >**\<commande >*», où vous remplacez le  *\<Verbe >* et  *\<Noun >* des espaces réservés avec le verbe et substantif, utilisé pour le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-152">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="16bb2-153">Par exemple, le [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) applet de commande est implémentée par une classe appelée `GetProcessCommand`.</span><span class="sxs-lookup"><span data-stu-id="16bb2-153">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="16bb2-154">Si aucune entrée de Pipeline ne substituer la méthode BeginProcessing (AC02)</span><span class="sxs-lookup"><span data-stu-id="16bb2-154">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="16bb2-155">Si votre applet de commande n’accepte pas d’entrée provenant du pipeline, le traitement doit être implémenté dans le [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="16bb2-155">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="16bb2-156">Utilisation de cette méthode permet de conserver l’ordre entre les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16bb2-156">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="16bb2-157">La première applet de commande dans le pipeline retourne toujours ses objets avant les autres applets de commande dans le pipeline chance de démarrer leur traitement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-157">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="16bb2-158">Pour gérer les demandes d’arrêt substituent la méthode StopProcessing (AC03)</span><span class="sxs-lookup"><span data-stu-id="16bb2-158">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="16bb2-159">Remplacer le [System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) méthode afin que votre applet de commande peut gérer le signal d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="16bb2-159">Override the [System.Management.Automation.Cmdlet.Stopprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="16bb2-160">Certaines applets de commande prennent beaucoup de temps pour terminer leur opération, et ils permettent de beaucoup de temps passer entre les appels à l’exécution de Windows PowerShell, telles que lorsque l’applet de commande bloque le thread dans les appels RPC longue.</span><span class="sxs-lookup"><span data-stu-id="16bb2-160">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="16bb2-161">Cela inclut les applets de commande qui effectuent des appels à la [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (méthode), à la [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (méthode) et à d’autres commentaires mécanismes qui peuvent prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="16bb2-161">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="16bb2-162">Dans ce cas l’utilisateur devra peut-être envoyer un signal d’arrêt à ces applets de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-162">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="16bb2-163">Implémenter l’Interface IDisposable (AC04)</span><span class="sxs-lookup"><span data-stu-id="16bb2-163">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="16bb2-164">Si votre applet de commande possède des objets qui ne sont pas supprimés de (écrit dans le pipeline) par le [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), votre applet de commande peut nécessiter la suppression d’objets supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="16bb2-164">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="16bb2-165">Par exemple, si votre applet de commande ouvre un handle de fichier dans son [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode) et conserve le handle ouvrir pour une utilisation par le [System.Management.Automation.Cmdlet.Processrecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode), ce handle doit être fermé à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-165">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="16bb2-166">Le runtime Windows PowerShell n’appelle pas toujours le [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="16bb2-166">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="16bb2-167">Par exemple, le [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode ne peut pas être appelée si l’applet de commande est annulée à mi-chemin via son fonctionnement, ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="16bb2-167">For example, the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="16bb2-168">Par conséquent, la classe .NET Framework pour une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.Idisposable](/dotnet/api/System.IDisposable) modèle d’interface, y compris le finaliseur, afin que le runtime Windows PowerShell peut appeler à la fois le [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) et [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement.</span><span class="sxs-lookup"><span data-stu-id="16bb2-168">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.Idisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="16bb2-169">Utiliser des Types de paramètres de sérialisation conviviale (AC05)</span><span class="sxs-lookup"><span data-stu-id="16bb2-169">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="16bb2-170">Pour prendre en charge votre applet de commande en cours d’exécution sur des ordinateurs distants, utilisez les types qui peuvent être facilement sérialisées sur l’ordinateur client et puis réalimentées sur l’ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="16bb2-170">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="16bb2-171">Les types de suivi sont adapté à la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="16bb2-171">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="16bb2-172">Types primitifs :</span><span class="sxs-lookup"><span data-stu-id="16bb2-172">Primitive types:</span></span>

- <span data-ttu-id="16bb2-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 et UInt64.</span><span class="sxs-lookup"><span data-stu-id="16bb2-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="16bb2-174">Valeur booléenne, Guid, Byte [], intervalle de temps, DateTime, Uri et Version.</span><span class="sxs-lookup"><span data-stu-id="16bb2-174">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="16bb2-175">Char, String, XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="16bb2-175">Char, String, XmlDocument.</span></span>

<span data-ttu-id="16bb2-176">Types rehydratable intégrés :</span><span class="sxs-lookup"><span data-stu-id="16bb2-176">Built-in rehydratable types:</span></span>

- <span data-ttu-id="16bb2-177">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="16bb2-177">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="16bb2-178">SwitchParmeter</span><span class="sxs-lookup"><span data-stu-id="16bb2-178">SwitchParmeter</span></span>

- <span data-ttu-id="16bb2-179">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="16bb2-179">PSListModifier</span></span>

- <span data-ttu-id="16bb2-180">PSCredential</span><span class="sxs-lookup"><span data-stu-id="16bb2-180">PSCredential</span></span>

- <span data-ttu-id="16bb2-181">IPAddress, MailAddress</span><span class="sxs-lookup"><span data-stu-id="16bb2-181">IPAddress, MailAddress</span></span>

- <span data-ttu-id="16bb2-182">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="16bb2-182">CultureInfo</span></span>

- <span data-ttu-id="16bb2-183">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="16bb2-183">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="16bb2-184">DirectorySecurity, FileSecurity, RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="16bb2-184">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="16bb2-185">Autres types :</span><span class="sxs-lookup"><span data-stu-id="16bb2-185">Other types:</span></span>

- <span data-ttu-id="16bb2-186">SecureString</span><span class="sxs-lookup"><span data-stu-id="16bb2-186">SecureString</span></span>

- <span data-ttu-id="16bb2-187">Conteneurs (listes et les dictionnaires de type ci-dessus)</span><span class="sxs-lookup"><span data-stu-id="16bb2-187">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="16bb2-188">Utilisez SecureString pour les données sensibles (AC06)</span><span class="sxs-lookup"><span data-stu-id="16bb2-188">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="16bb2-189">Lors de la gestion des données sensibles de toujours utiliser le [System.Security.Securestring](/dotnet/api/System.Security.SecureString) type de données.</span><span class="sxs-lookup"><span data-stu-id="16bb2-189">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="16bb2-190">Cela peut inclure les entrées de pipeline pour les paramètres, ainsi que le renvoi de données sensibles dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="16bb2-190">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="16bb2-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16bb2-191">See Also</span></span>

[<span data-ttu-id="16bb2-192">Directives de développement requis</span><span class="sxs-lookup"><span data-stu-id="16bb2-192">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="16bb2-193">Directives de développement vous êtes vivement invité</span><span class="sxs-lookup"><span data-stu-id="16bb2-193">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="16bb2-194">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16bb2-194">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)