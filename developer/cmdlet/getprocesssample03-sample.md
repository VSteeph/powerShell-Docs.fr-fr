---
title: Exemple de GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856475"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="3fa0b-102">Exemple GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="3fa0b-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="3fa0b-103">Cet exemple montre comment implémenter une applet de commande qui Récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="3fa0b-104">Il fournit un `Name` paramètre qui peut accepter un objet provenant du pipeline ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="3fa0b-105">Cette applet de commande est une version simplifiée de la `Get-Process` applet de commande fournie par Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3fa0b-106">Guide pratique pour générer l’exemple à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="3fa0b-107">Avec le Windows SDK PowerShell 2.0 installé, accédez au dossier GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="3fa0b-108">L’emplacement par défaut est C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="3fa0b-109">Double-cliquez sur l’icône pour le fichier solution (.sln).</span><span class="sxs-lookup"><span data-stu-id="3fa0b-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3fa0b-110">L’exemple de projet s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="3fa0b-111">Dans le **Build** menu, sélectionnez **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="3fa0b-112">La bibliothèque de l’exemple est générée dans les dossiers \bin ou \bin\debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3fa0b-113">Comment exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="3fa0b-113">How to run the sample</span></span>

1. <span data-ttu-id="3fa0b-114">Créez le dossier de module suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa0b-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="3fa0b-115">Copiez l’exemple d’assembly dans le dossier de module.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="3fa0b-116">Démarrez Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3fa0b-117">Exécutez la commande suivante pour charger l’assembly dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="3fa0b-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="3fa0b-118">Exécutez la commande suivante pour exécuter l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="3fa0b-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="3fa0b-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fa0b-119">Requirements</span></span>

<span data-ttu-id="3fa0b-120">Cet exemple requiert Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3fa0b-121">Montre</span><span class="sxs-lookup"><span data-stu-id="3fa0b-121">Demonstrates</span></span>

<span data-ttu-id="3fa0b-122">Cet exemple montre ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3fa0b-123">Déclaration de la classe d’applet de commande à l’aide de l’attribut de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="3fa0b-124">Déclaration d’un paramètre de l’applet de commande à l’aide de l’attribut de paramètre.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="3fa0b-125">Spécifiant la position du paramètre.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="3fa0b-126">En spécifiant que le paramètre prend en entrée du pipeline.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="3fa0b-127">L’entrée peut provenir d’un objet ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="3fa0b-128">Déclaration d’un attribut de validation pour le paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="3fa0b-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="3fa0b-129">Example</span></span>

<span data-ttu-id="3fa0b-130">Cet exemple illustre une implémentation de l’applet de commande Get-Process qui inclut un `Name` paramètre qui accepte les entrées du pipeline.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="3fa0b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fa0b-131">See Also</span></span>

[<span data-ttu-id="3fa0b-132">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fa0b-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)