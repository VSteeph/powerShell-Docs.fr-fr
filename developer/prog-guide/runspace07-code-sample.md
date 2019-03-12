---
title: Exemple de Code RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429633"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="c6637-102">Exemple de code RunSpace07</span><span class="sxs-lookup"><span data-stu-id="c6637-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="c6637-103">Voici le code source pour l’exemple Runspace07 décrit dans [création d’une Application qu’ajoute des commandes de la Console à un Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="c6637-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="c6637-104">Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute les deux commandes au pipeline, puis exécute le pipeline.</span><span class="sxs-lookup"><span data-stu-id="c6637-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="c6637-105">Les commandes ajoutées au pipeline sont le `Get-Process` et `Measure-Object` applets de commande.</span><span class="sxs-lookup"><span data-stu-id="c6637-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="c6637-106">Vous pouvez télécharger le C# le fichier source (runspace07.cs) en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="c6637-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c6637-107">Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c6637-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c6637-108">Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="c6637-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c6637-109">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c6637-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="c6637-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6637-110">See Also</span></span>

[<span data-ttu-id="c6637-111">Guide du programmeur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6637-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c6637-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c6637-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)