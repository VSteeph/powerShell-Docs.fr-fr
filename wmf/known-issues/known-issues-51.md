---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Problèmes connus dans WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855714"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="88883-103">Problèmes connus dans WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="88883-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="88883-104">Démarrage de raccourci PowerShell en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="88883-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="88883-105">Lors de l’installation de WMF, si vous essayez de démarrer PowerShell en tant qu’administrateur à partir du raccourci, vous pouvez obtenir un message « Erreur non spécifiée ».</span><span class="sxs-lookup"><span data-stu-id="88883-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="88883-106">Rouvrez le raccourci comme non-administrateur. Le raccourci fonctionne désormais même comme administrateur.</span><span class="sxs-lookup"><span data-stu-id="88883-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="88883-107">Pester</span><span class="sxs-lookup"><span data-stu-id="88883-107">Pester</span></span>

<span data-ttu-id="88883-108">Dans cette version, vous devez savoir qu’il existe deux problèmes quand vous utilisez Pester sur Nano Server :</span><span class="sxs-lookup"><span data-stu-id="88883-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="88883-109">L’exécution des tests directement sur Pester peut entraîner des échecs en raison des différences entre la version CLR complète et la version CLR de base.</span><span class="sxs-lookup"><span data-stu-id="88883-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="88883-110">En particulier, la méthode **Validate** n’est pas disponible sur le type **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="88883-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="88883-111">Six tests qui tentent de valider le schéma des journaux de sortie NUnit échouent systématiquement.</span><span class="sxs-lookup"><span data-stu-id="88883-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="88883-112">Un test de couverture du code échoue, car la ressource DSC **WindowsFeature** n’existe pas dans Nano Server.</span><span class="sxs-lookup"><span data-stu-id="88883-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="88883-113">Toutefois, ces échecs sont généralement sans conséquence et peuvent être ignorés.</span><span class="sxs-lookup"><span data-stu-id="88883-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="88883-114">Validation de l’opération</span><span class="sxs-lookup"><span data-stu-id="88883-114">Operation Validation</span></span>

- <span data-ttu-id="88883-115">`Update-Help` échoue pour le module Microsoft.PowerShell.Operation.Validation en raison d’un URI d’aide qui ne fonctionne pas</span><span class="sxs-lookup"><span data-stu-id="88883-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="88883-116">DSC après la désinstallation de WMF</span><span class="sxs-lookup"><span data-stu-id="88883-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="88883-117">La désinstallation de WMF ne supprime pas les documents MOF DSC du dossier de configuration.</span><span class="sxs-lookup"><span data-stu-id="88883-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="88883-118">DSC ne fonctionne pas correctement si les documents MOF contiennent des propriétés récentes qui ne sont pas disponibles sur les anciens systèmes.</span><span class="sxs-lookup"><span data-stu-id="88883-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="88883-119">Dans ce cas, exécutez le script suivant à partir de la console PowerShell avec élévation de privilèges pour nettoyer les états DSC.</span><span class="sxs-lookup"><span data-stu-id="88883-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="88883-120">Comptes virtuels JEA</span><span class="sxs-lookup"><span data-stu-id="88883-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="88883-121">Si des configurations de session et des points de terminaison JEA sont configurés pour utiliser des comptes virtuels dans WMF 5.0, il n’en est pas de même après la mise à niveau vers WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="88883-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="88883-122">Les commandes exécutées dans des sessions JEA s’exécutent alors sous l’identité de l’utilisateur connecté et non sous un compte d’administrateur temporaire, ce qui peut empêcher l’utilisateur d’exécuter des commandes nécessitant des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="88883-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="88883-123">Pour restaurer les comptes virtuels, vous devez désinscrire et réinscrire toute configuration de session utilisant des comptes virtuels.</span><span class="sxs-lookup"><span data-stu-id="88883-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```