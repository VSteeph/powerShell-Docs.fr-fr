---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation de DSC sur Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401437"
---
# <a name="using-dsc-on-nano-server"></a>Utilisation de DSC sur Nano Server

> S'applique à : Windows PowerShell 5.0

**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016. Le package peut être installé lorsque vous créez un disque dur virtuel pour Nano Server en spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**. Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle, la commande ressemble à ceci :

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir [Prise en main de Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>Fonctionnalités DSC disponibles sur Nano Server

Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur les références complètes pour l’instant. En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.

Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server :

Modes par envoi et par extraction

- Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes :
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguraiton](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Compilation de configurations (voir [Configurations DSC](../configurations/configurations.md))

  **Problème #1629** Chiffrement de mot de passe (voir [sécurisation du fichier MOF](../pull-server/secureMOF.md)) pendant la configuration de compilation ne fonctionne pas.

- Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md))

- Exécution d’une ressource sous un contexte utilisateur (voir [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](../configurations/runAsUser.md))

- Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](../resources/authoringResourceClass.md))

- Débogage des ressources DSC (voir [Débogage des ressources DSC](../troubleshooting/debugResource.md))

  **Problème #1629** Ne fonctionne pas si une ressource utilise PsDscRunAsCredential (voir [en cours d’exécution de DSC avec les informations d’identification utilisateur](../configurations/runAsUser.md))

- [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md)

- [Contrôle de version de ressources](../configurations/sxsResource.md)

- Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](../pull-server/pullClientConfigNames.md))

- [Configurations partielles (envoi et extraction)](../pull-server/partialConfigs.md)

- [Rapports au serveur collecteur](../pull-server/reportServer.md)

- Chiffrement de document MOF

- Journalisation des événements

- Création de rapports DSC Azure Automation

- Ressources entièrement fonctionnelles

- **Archive**
- **Environment**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))
- **WaitForAny** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))
- **WaitForSome** (voir [Spécification de dépendances entre nœuds](../configurations/crossNodeDependencies.md))

- Ressources partiellement fonctionnelles
- **Groupe**
- **GroupSet**

  **Problème #1629** Ressources ci-dessus échouent si l’instance spécifique est appelée deux fois (en cours d’exécution la même configuration deux fois)

- **Service**
- **ServiceSet**

  **Problème #1629** Fonctionne uniquement pour démarrage/arrêt de service (état). Échoue si vous essayez de modifier d’autres attributs de service, comme StartupType, les informations d’identification, la description, etc. L’erreur levée est semblable à :

  *Impossible de trouver le type [management.managementobject] : vérifiez que l’assembly contenant ce type est chargé.*

- Ressources non fonctionnelles
- **User**

## <a name="dsc-features-not-available-on-nano-server"></a>Fonctionnalités DSC non disponibles sur Nano Server

Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :

- Déchiffrement de documents MOF avec mots de passe cryptés
- Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment
- Tout ce qui n’est pas dans la liste des fonctionnalités marche

## <a name="using-custom-dsc-resources-on-nano-server"></a>Utilisation de ressources DSC personnalisées sur Nano Server

En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server.
Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.

## <a name="see-also"></a>Voir aussi

- [Prise en main de Nano Server](/windows-server/get-started/getting-started-with-nano-server)