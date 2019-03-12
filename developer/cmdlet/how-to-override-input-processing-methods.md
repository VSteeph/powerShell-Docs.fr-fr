---
title: Comment substituer les méthodes de traitement d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855915"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="5ca5f-102">Guide pratique pour remplacer des méthodes de traitement des entrées</span><span class="sxs-lookup"><span data-stu-id="5ca5f-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="5ca5f-103">Ces exemples montrent comment remplacer les méthodes au sein d’une applet de commande de traitement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="5ca5f-104">Ces méthodes sont utilisées pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ca5f-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="5ca5f-105">Le [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode est utilisée pour effectuer des opérations de démarrage à usage unique qui sont valides pour tous les objets traités par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-105">The [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="5ca5f-106">Le runtime Windows PowerShell appelle cette méthode une seule fois.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="5ca5f-107">Le [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode est utilisée pour traiter les objets passés à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-107">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="5ca5f-108">Le runtime Windows PowerShell appelle cette méthode pour chaque objet passé à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="5ca5f-109">Le [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode est utilisée pour effectuer des opérations de traitement de billet à usage unique.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-109">The [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="5ca5f-110">Le runtime Windows PowerShell appelle cette méthode une seule fois.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="5ca5f-111">Pour substituer la méthode BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="5ca5f-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="5ca5f-112">Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-112">Declare a protected override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="5ca5f-113">La classe suivante imprime un exemple de message.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-113">The following class prints a sample message.</span></span> <span data-ttu-id="5ca5f-114">Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="5ca5f-115">Pour substituer la méthode ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="5ca5f-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="5ca5f-116">Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-116">Declare a protected override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="5ca5f-117">La classe suivante imprime un exemple de message.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-117">The following class prints a sample message.</span></span> <span data-ttu-id="5ca5f-118">Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="5ca5f-119">Pour substituer la méthode EndProcessing</span><span class="sxs-lookup"><span data-stu-id="5ca5f-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="5ca5f-120">Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-120">Declare a protected override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="5ca5f-121">La classe suivante imprime un exemple.</span><span class="sxs-lookup"><span data-stu-id="5ca5f-121">The following class prints a sample.</span></span> <span data-ttu-id="5ca5f-122">Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.Endprocessing\* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5ca5f-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="5ca5f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca5f-123">See Also</span></span>

[<span data-ttu-id="5ca5f-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="5ca5f-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="5ca5f-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="5ca5f-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="5ca5f-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="5ca5f-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="5ca5f-127">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ca5f-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)