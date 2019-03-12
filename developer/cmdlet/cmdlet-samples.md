---
title: Exemples d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: d919d4ad8554e762230c1448d81b50e27c38ba99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863365"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="c0086-102">Exemples d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="c0086-102">Cmdlet Samples</span></span>

<span data-ttu-id="c0086-103">Cette section décrit l’exemple de code qui est fourni dans le Kit de développement logiciel de Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c0086-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="c0086-104">Vous pouvez copier le code dans les rubriques de cette section, ou ouvrir les fichiers de code source installés avec le Kit de développement.</span><span class="sxs-lookup"><span data-stu-id="c0086-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="c0086-105">Le [Kit de développement logiciel (SDK) Windows PowerShell 2.0](https://www.microsoft.com/en-us/download/details.aspx?id=2560) fournit les fichiers Lisez-moi, les fichiers sources et les fichiers de projet Visual Studio pour chaque échantillon.</span><span class="sxs-lookup"><span data-stu-id="c0086-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="c0086-106">Avec le Kit de développement SDK, vous pouvez trouver les exemples sous la `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` dossier.</span><span class="sxs-lookup"><span data-stu-id="c0086-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0086-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c0086-107">In This Section</span></span>

<span data-ttu-id="c0086-108">[L’exemple GetProcessSample01](./getprocesssample01-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c0086-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="c0086-109">[L’exemple GetProcessSample02](./getprocesssample02-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c0086-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c0086-110">Il fournit un paramètre de nom qui peut être utilisé pour spécifier les processus à récupérer.</span><span class="sxs-lookup"><span data-stu-id="c0086-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="c0086-111">[Exemple de GetProcessSample03](./getprocesssample03-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c0086-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c0086-112">Il fournit un paramètre de nom qui peut accepter un objet provenant du pipeline ou une valeur d’une propriété d’un objet dont le nom propriété est le même que le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c0086-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="c0086-113">[Exemple de GetProcessSample04](./getprocesssample04-sample.md) cet exemple montre comment écrire une applet de commande qui Récupère les processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c0086-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c0086-114">Il génère une erreur sans fin d’exécution si une erreur se produit lors de la récupération d’un processus.</span><span class="sxs-lookup"><span data-stu-id="c0086-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="c0086-115">[Exemple de GetProcessSample05](./getprocesssample05-sample.md) cet exemple montre une version complète de l’applet de commande Get-Process.</span><span class="sxs-lookup"><span data-stu-id="c0086-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="c0086-116">[Exemple de StopProcessSample01](./stopprocesssample01-sample.md) cet exemple montre comment écrire une applet de commande qui demande des commentaires à l’utilisateur avant d’essayer d’arrêter un processus et comment implémenter un `PassThru` paramètre qui indique que l’utilisateur souhaite que l’applet de commande pour retourner un objet.</span><span class="sxs-lookup"><span data-stu-id="c0086-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="c0086-117">[Exemple de StopProcessSample02](./stopprocesssample02-sample.md) cet exemple montre comment écrire une applet de commande écrit debug, verbose et les messages d’avertissement lors de l’arrêt de processus sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c0086-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="c0086-118">[Exemple de StopProcessSample03](./stopprocesssample03-sample.md) cet exemple montre comment écrire une applet de commande dont les paramètres ont des alias et qui prennent en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="c0086-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="c0086-119">[Exemple de StopProcessSample04](./stopprocesssample04-sample.md) cet exemple montre comment écrire une applet de commande qui déclare les jeux de paramètres, spécifie le paramètre par défaut définie et peut accepter un objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c0086-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="c0086-120">[Exemple de Events01](./events01-sample.md) cet exemple montre comment créer une applet de commande qui permet à l’utilisateur à s’inscrire pour les événements déclenchés par [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="c0086-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="c0086-121">Avec cette applet de commande les utilisateurs peuvent, par exemple, inscrire une action à exécuter quand un fichier est créé dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="c0086-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="c0086-122">Cet exemple dérive le [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe de base.</span><span class="sxs-lookup"><span data-stu-id="c0086-122">This sample derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0086-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0086-123">See Also</span></span>

[<span data-ttu-id="c0086-124">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0086-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)