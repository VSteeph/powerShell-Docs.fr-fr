---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource DSC WaitForSome
ms.openlocfilehash: 37c73ed4a42975194938f78de04096a988cf9846
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561084"
---
# <a name="dsc-waitforsome-resource"></a>Ressource DSC WaitForSome

> S’applique à : Windows PowerShell 5.x

La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](../../../configurations/configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.

La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.

> [!NOTE]
> La ressource **WaitForSome** utilise Windows Remote Management pour vérifier l’état d’autres nœuds. Pour plus d’informations sur la configuration requise des ports et de la sécurité pour WinRM, consultez [Éléments à prendre en compte en matière de sécurité de la communication à distance PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Syntaxe

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|NodeCount |Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse. |
|NodeName |Les nœuds cible de la ressource de la dépendance. |
|Nom_ressource |Le nom de la ressource de la dépendance. Si cette ressource appartient à une configuration différente, mettez le nom sous la forme `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. |
|RetryIntervalSec |Le nombre de secondes avant la nouvelle tentative. Le minimum est 1. |
|RetryCount |Le nombre maximum de nouvelles tentatives. |
|ThrottleLimit |Le nombre de machines à connecter simultanément. La valeur par défaut est `New-CimSession` par défaut. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](../../../configurations/crossNodeDependencies.md)
