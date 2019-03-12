---
title: Runspace02 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854615"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="69f06-102">Exemple de code Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="69f06-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="69f06-103">Voici le C# code source pour l’exemple Runspace02.</span><span class="sxs-lookup"><span data-stu-id="69f06-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="69f06-104">Cet exemple utilise le [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe pour exécuter le `Get-Process` applet de commande synchrone.</span><span class="sxs-lookup"><span data-stu-id="69f06-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="69f06-105">Windows Forms et la liaison de données sont ensuite utilisés pour afficher les résultats dans un contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="69f06-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="69f06-106">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="69f06-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="69f06-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69f06-107">See Also</span></span>

[<span data-ttu-id="69f06-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="69f06-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)