---
title: Exemples de fournisseurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 7fabd251b2a9ae7704493681d1502fdc0f0a73cb
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560965"
---
# <a name="provider-samples"></a>Exemples de fournisseurs

Cette section comprend des exemples de fournisseurs qui accèdent à une base de données Microsoft Access. Ces exemples incluent des classes de fournisseur qui dérivent de toutes les classes de fournisseur de base.

## <a name="in-this-section"></a>Dans cette section

Cette section comprend les rubriques suivantes :

[Exemple AccessDBProviderSample01](./accessdbprovidersample01.md) Cet exemple montre comment déclarer la classe de fournisseur qui dérive directement de la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Il est indiqué ici uniquement par souci de citer tous les exemples.

[AccessDBProviderSample02](./accessdbprovidersample02.md) Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) et [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour prendre en charge les appels aux `New-PSDrive` applets de commande et `Remove-PSDrive` . La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

[AccessDBProviderSample03](./accessdbprovidersample03.md) Cet exemple montre comment remplacer les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) et [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) pour prendre en charge les appels aux `Get-Item` applets de commande et `Set-Item` . La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

[AccessDBProviderSample04](./accessdbprovidersample04.md) Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Copy-Item` applets de commande,, `Get-ChildItem` `New-Item` et `Remove-Item` . Ces méthodes doivent être implémentées quand le magasin de données contient des éléments de type conteneur. Un conteneur est un groupe d’éléments enfants qui descendent d’un même élément parent. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

[AccessDBProviderSample05](./accessdbprovidersample05.md) Cet exemple montre comment remplacer les méthodes de conteneur pour prendre en charge les appels aux `Move-Item` applets de commande et `Join-Path` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de déplacer des éléments dans un conteneur et si le magasin de données contient des conteneurs imbriqués. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

[AccessDBProviderSample06](./accessdbprovidersample06.md) Cet exemple montre comment remplacer les méthodes de contenu pour prendre en charge les appels aux `Clear-Content` applets de commande, `Get-Content` et `Set-Content` . Ces méthodes doivent être implémentées quand l’utilisateur a besoin de gérer le contenu des éléments situés dans le magasin de données. La classe de fournisseur de cet exemple dérive de la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et implémente l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)
