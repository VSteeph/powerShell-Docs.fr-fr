---
title: Exemple deC#code GetProc01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 71ba68521ed8d26d0c85169d2b0d547cc6d2d5e3
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978421"
---
# <a name="getproc01-c-sample-code"></a>Exemple de code GetProc01 (C#)

Le code suivant illustre l’implémentation de l’applet de commande GetProc01 Sample. Notez que l’applet de commande est simplifiée en laissant le travail réel de récupération du processus à la méthode [System. Diagnostics. Process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) .

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (getproc01.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** .

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
