---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Mettre à jour des nœuds à partir d’un serveur Pull
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500674"
---
# <a name="update-nodes-from-a-pull-server"></a>Mettre à jour des nœuds à partir d’un serveur Pull

Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull. Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état. Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources. Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Utilisation de l’applet de commande Update-DSCConfiguration

À compter de PowerShell 5.0, l’applet de commande [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) force un nœud à mettre à jour sa configuration à partir du serveur Pull configuré dans le gestionnaire de configuration local.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Utilisation d’Invoke-CIMMethod

Dans PowerShell 4.0, vous pouvez forcer manuellement un client Pull à mettre à jour sa configuration à l’aide d’[Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). L’exemple suivant crée une session CIM avec les informations d’identification spécifiées, appelle la méthode CIM appropriée, puis supprime la session.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Voir aussi

[PerformRequiredConfigurationChecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
