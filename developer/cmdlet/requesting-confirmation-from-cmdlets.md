---
title: Demander la Confirmation des applets de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853395"
---
# <a name="requesting-confirmation-from-cmdlets"></a><span data-ttu-id="7a562-102">Demandes de confirmation des applets de commande</span><span class="sxs-lookup"><span data-stu-id="7a562-102">Requesting Confirmation from Cmdlets</span></span>

<span data-ttu-id="7a562-103">Applets de commande demande une confirmation lorsqu’ils sont sur le point d’apporter une modification au système qui se trouve en dehors de l’environnement Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a562-103">Cmdlets should request confirmation when they are about to make a change to the system that is outside of the Windows PowerShell environment.</span></span> <span data-ttu-id="7a562-104">Par exemple, si une applet de commande est sur le point d’ajouter un compte d’utilisateur ou d’arrêter un processus, l’applet de commande doit nécessitent une confirmation de l’utilisateur avant de poursuivre.</span><span class="sxs-lookup"><span data-stu-id="7a562-104">For example, if a cmdlet is about to add a user account or stop a process, the cmdlet should require confirmation from the user before it proceeds.</span></span> <span data-ttu-id="7a562-105">En revanche, si une applet de commande est sur le point de modifier une variable Windows PowerShell, l’applet de commande ne devez pas nécessitent une confirmation.</span><span class="sxs-lookup"><span data-stu-id="7a562-105">In contrast, if a cmdlet is about to change a Windows PowerShell variable, the cmdlet does not need to require confirmation.</span></span>

<span data-ttu-id="7a562-106">Pour effectuer une demande de confirmation, l’applet de commande doit indiquer qu’il prend en charge les demandes de confirmation, et il doit appeler la [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes (facultatifs) pour afficher un message de demande de confirmation.</span><span class="sxs-lookup"><span data-stu-id="7a562-106">In order to make a confirmation request, the cmdlet must indicate that it supports confirmation requests, and it must call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) methods to display a confirmation request message.</span></span>

## <a name="supporting-confirmation-requests"></a><span data-ttu-id="7a562-107">Prise en charge des demandes de Confirmation</span><span class="sxs-lookup"><span data-stu-id="7a562-107">Supporting Confirmation Requests</span></span>

<span data-ttu-id="7a562-108">Pour prendre en charge les demandes de confirmation, l’applet de commande doit définir le `SupportsShouldProcess` paramètre de l’attribut de l’applet de commande à `true`.</span><span class="sxs-lookup"><span data-stu-id="7a562-108">To support confirmation requests, the cmdlet must set the `SupportsShouldProcess` parameter of the Cmdlet attribute to `true`.</span></span> <span data-ttu-id="7a562-109">Cela permet la `Confirm` et `WhatIf` paramètres d’applet de commande qui sont fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a562-109">This enables the `Confirm` and `WhatIf` cmdlet parameters that are provided by Windows PowerShell.</span></span> <span data-ttu-id="7a562-110">Le `Confirm` paramètre permet à l’utilisateur de contrôler si la demande de confirmation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7a562-110">The `Confirm` parameter allows the user to control whether the confirmation request is displayed.</span></span> <span data-ttu-id="7a562-111">Le `WhatIf` paramètre permet à l’utilisateur déterminer si l’applet de commande doit afficher un message ou exécuter son action.</span><span class="sxs-lookup"><span data-stu-id="7a562-111">The `WhatIf` parameter allows the user to determine whether the cmdlet should display a message or perform its action.</span></span> <span data-ttu-id="7a562-112">N’ajoutez pas manuellement la `Confirm` et `WhatIf` paramètres pour une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7a562-112">Do not manually add the `Confirm` and `WhatIf` parameters to a cmdlet.</span></span>

<span data-ttu-id="7a562-113">L’exemple suivant montre une déclaration d’attribut applet de commande qui prend en charge les demandes de confirmation.</span><span class="sxs-lookup"><span data-stu-id="7a562-113">The following example shows a Cmdlet attribute declaration that supports confirmation requests.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a><span data-ttu-id="7a562-114">Appel des méthodes de demande de Confirmation</span><span class="sxs-lookup"><span data-stu-id="7a562-114">Calling the Confirmation request methods</span></span>

<span data-ttu-id="7a562-115">Dans le code de l’applet de commande, appelez le [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode avant que l’opération qui modifie le système est effectuée.</span><span class="sxs-lookup"><span data-stu-id="7a562-115">In the cmdlet code, call the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the operation that changes the system is performed.</span></span> <span data-ttu-id="7a562-116">L’applet de commande de conception afin qu’en cas l’appel retourne une valeur de `false`, l’opération n’est pas effectuée et l’applet de commande traite l’opération suivante.</span><span class="sxs-lookup"><span data-stu-id="7a562-116">Design the cmdlet so that if the call returns a value of `false`, the operation is not performed, and the cmdlet processes the next operation.</span></span>

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="7a562-117">Appel de la méthode ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="7a562-117">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="7a562-118">La plupart des applets de commande demande confirmation à l’aide uniquement le [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7a562-118">Most cmdlets request confirmation using only the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="7a562-119">Toutefois, certains cas peuvent nécessiter de confirmation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="7a562-119">However, some cases might require additional confirmation.</span></span> <span data-ttu-id="7a562-120">Dans ce cas, vous devez compléter les [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) par un appel à la [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7a562-120">For these cases, supplement the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call with a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method.</span></span> <span data-ttu-id="7a562-121">Cela permet à l’applet de commande ou d’un fournisseur de contrôler plus précisément l’étendue de la **Oui pour tout** réponse à l’invite de confirmation.</span><span class="sxs-lookup"><span data-stu-id="7a562-121">This allows the cmdlet or provider to more finely control the scope of the **Yes to all** response to the confirmation prompt.</span></span>

<span data-ttu-id="7a562-122">Si une applet de commande appelle le [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode), l’applet de commande doit également fournir un `Force` paramètre booléen.</span><span class="sxs-lookup"><span data-stu-id="7a562-122">If a cmdlet calls the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method, the cmdlet must also provide a `Force` switch parameter.</span></span> <span data-ttu-id="7a562-123">Si l’utilisateur spécifie `Force` lorsque l’utilisateur appelle l’applet de commande, l’applet de commande doit toujours appeler [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), mais il doit ignorer l’appel à [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="7a562-123">If the user specifies `Force` when the user invokes the cmdlet, the cmdlet should still call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), but it should bypass the call to [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

<span data-ttu-id="7a562-124">[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) lève une exception lorsqu’elle est appelée à partir d’un environnement non interactif où l’utilisateur ne peut pas être invité.</span><span class="sxs-lookup"><span data-stu-id="7a562-124">[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) will throw an exception when it is called from a non-interactive environment where the user cannot be prompted.</span></span> <span data-ttu-id="7a562-125">Ajout d’un `Force` paramètre garantit que la commande peut toujours être effectuée lorsqu’il est appelé dans un environnement non interactif.</span><span class="sxs-lookup"><span data-stu-id="7a562-125">Adding a `Force` parameter ensures that the command can still be performed when it is invoked in a non-interactive environment.</span></span>

<span data-ttu-id="7a562-126">L’exemple suivant montre comment appeler [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="7a562-126">The following example shows how to call [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

<span data-ttu-id="7a562-127">Le comportement d’un [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel peut varier en fonction de l’environnement dans lequel l’applet de commande est appelé.</span><span class="sxs-lookup"><span data-stu-id="7a562-127">The behavior of a [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call can vary depending on the environment in which the cmdlet is invoked.</span></span> <span data-ttu-id="7a562-128">En suivant les recommandations précédentes afin de garantir que l’applet de commande se comporte de manière cohérente avec les autres applets de commande, quel que soit l’environnement hôte.</span><span class="sxs-lookup"><span data-stu-id="7a562-128">Using the previous guidelines will help ensure that the cmdlet behaves consistently with other cmdlets, regardless of the host environment.</span></span>

<span data-ttu-id="7a562-129">Pour obtenir un exemple de l’appel le [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), consultez [comment demander des Confirmations](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="7a562-129">For an example of calling the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specify-the-impact-level"></a><span data-ttu-id="7a562-130">Spécifiez le niveau d’Impact</span><span class="sxs-lookup"><span data-stu-id="7a562-130">Specify the Impact Level</span></span>

<span data-ttu-id="7a562-131">Lorsque vous créez l’applet de commande, spécifiez le niveau d’impact (la gravité) de la modification.</span><span class="sxs-lookup"><span data-stu-id="7a562-131">When you create the cmdlet, specify the impact level (the severity) of the change.</span></span> <span data-ttu-id="7a562-132">Pour ce faire, définissez la valeur de la `ConfirmImpact` paramètre de l’attribut de l’applet de commande à élevé, moyen ou faible.</span><span class="sxs-lookup"><span data-stu-id="7a562-132">To do this, set the value of the `ConfirmImpact` parameter of the Cmdlet attribute to High, Medium, or Low.</span></span> <span data-ttu-id="7a562-133">Vous pouvez spécifier une valeur pour `ConfirmImpact` uniquement lorsque vous également spécifiez les `SupportsShouldProcess` paramètre pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7a562-133">You can specify a value for `ConfirmImpact` only when you also specify the `SupportsShouldProcess` parameter for the cmdlet.</span></span>

<span data-ttu-id="7a562-134">Pour la plupart des applets de commande, vous n’avez pas à spécifier explicitement `ConfirmImpact`.</span><span class="sxs-lookup"><span data-stu-id="7a562-134">For most cmdlets, you do not have to explicitly specify `ConfirmImpact`.</span></span>  <span data-ttu-id="7a562-135">Au lieu de cela, utilisez le paramètre par défaut du paramètre, qui est la moyenne.</span><span class="sxs-lookup"><span data-stu-id="7a562-135">Instead, use the default setting of the parameter, which is Medium.</span></span> <span data-ttu-id="7a562-136">Si vous définissez `ConfirmImpact` élevé, l’opération sera confirmée par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a562-136">If you set `ConfirmImpact` to High, the operation will be confirmed by default.</span></span> <span data-ttu-id="7a562-137">Réserver ce paramètre pour les actions hautement perturbatrices, telles que le reformatage d’un volume de disque dur.</span><span class="sxs-lookup"><span data-stu-id="7a562-137">Reserve this setting for highly disruptive actions, such as reformatting a hard-disk volume.</span></span>

## <a name="calling-non-confirmation-methods"></a><span data-ttu-id="7a562-138">Appel de méthodes Non-Confirmation</span><span class="sxs-lookup"><span data-stu-id="7a562-138">Calling Non-Confirmation Methods</span></span>

<span data-ttu-id="7a562-139">Si l’applet de commande ou le fournisseur doit envoyer un message, mais pas demande confirmation, elle peut appeler le des trois méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="7a562-139">If the cmdlet or provider must send a message but not request confirmation, it can call the following three methods.</span></span> <span data-ttu-id="7a562-140">Évitez d’utiliser le [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) méthode pour envoyer des messages de ces types, car [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) le mélange de sortie avec la sortie normale de votre applet de commande ou d’un fournisseur, ce qui complique écriture de script.</span><span class="sxs-lookup"><span data-stu-id="7a562-140">Avoid using the [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to send messages of these types because [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output is intermingled with the normal output of your cmdlet or provider, which makes script writing difficult.</span></span>

- <span data-ttu-id="7a562-141">Pour l’attention de l’utilisateur et poursuivre l’opération, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7a562-141">To caution the user and continue with the operation, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

- <span data-ttu-id="7a562-142">Pour fournir des informations supplémentaires que l’utilisateur peut récupérer à l’aide de la `Verbose` paramètre, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7a562-142">To provide additional information that the user can retrieve using the `Verbose` parameter, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

- <span data-ttu-id="7a562-143">Pour fournir les détails de niveau débogage à d’autres développeurs, ou pour la prise en charge du produit, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7a562-143">To provide debugging-level detail for other developers or for product support, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="7a562-144">L’utilisateur peut récupérer cette information à l’aide de le `Debug` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7a562-144">The user can retrieve this information using the `Debug` parameter.</span></span>

<span data-ttu-id="7a562-145">Applets de commande et des fournisseurs d’abord appellent les méthodes suivantes pour demande confirmation avant de tenter d’effectuer une opération qui modifie un système en dehors de Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7a562-145">Cmdlets and providers first call the following methods to request confirmation before they attempt to perform an operation that changes a system outside of Windows PowerShell:</span></span>

- [<span data-ttu-id="7a562-146">System.Management.Automation.Cmdlet.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="7a562-146">System.Management.Automation.Cmdlet.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [<span data-ttu-id="7a562-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="7a562-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

<span data-ttu-id="7a562-148">Ils le font en appelant le [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), qui invite l’utilisateur à confirmer l’opération basée sur la façon dont l’utilisateur a appelé la commande.</span><span class="sxs-lookup"><span data-stu-id="7a562-148">They do so by calling the [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which prompts the user to confirm the operation based on how the user invoked the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a562-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a562-149">See Also</span></span>

[<span data-ttu-id="7a562-150">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a562-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)