---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configuration du Gestionnaire de Configuration local dans les versions précédentes de Windows PowerShell
ms.openlocfilehash: 31ba2ecdaa5a2ff7fcfddb1791c4d00343f4b5d5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401467"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configuration du Gestionnaire de Configuration local dans les versions précédentes de Windows PowerShell

>S'applique à : Windows PowerShell 4.0

**Pour plus d’informations sur Windows PowerShell 5.0 et ultérieur, consultez [Configuration du Gestionnaire de Configuration local](metaConfig.md).**

Le Gestionnaire de configuration local (ou « LCM ») est le moteur de la fonctionnalité DSC (Desired State Configuration) de Windows PowerShell.
Exécuté sur tous les nœuds cibles, il est chargé d’appeler les ressources de configuration contenues dans un script de configuration DSC.
Cette rubrique répertorie les propriétés du Gestionnaire de configuration local et explique comment modifier les paramètres du Gestionnaire de configuration local sur un nœud cible.

## <a name="local-configuration-manager-properties"></a>Propriétés du Gestionnaire de configuration local

Vous pouvez définir ou récupérer les différentes propriétés du Gestionnaire de configuration local décrites ci-dessous.

- **AllowModuleOverwrite** : indique si vous autorisez le remplacement des configurations existantes sur le nœud cible par de nouvelles configurations téléchargées du service de configuration. Les valeurs possibles sont True et False.
- **CertificateID** : Empreinte d’un certificat utilisée pour sécuriser les informations d’identification transmise dans une configuration. Pour plus d’informations, consultez [Sécuriser les informations d’identification dans DSC Windows PowerShell](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID** : indique le GUID utilisé pour obtenir un fichier de configuration spécifique d’un service d’extraction. Le GUID permet d’identifier de façon unique le fichier de configuration à obtenir.
- **ConfigurationMode** : spécifie de quelle façon le Gestionnaire de configuration local applique réellement la configuration aux nœuds cibles. Cette propriété peut avoir les valeurs suivantes :
  - **ApplyOnly** : Cette valeur indique à DSC d’appliquer la configuration et de ne faire aucune autre opération, sauf si vous transmettez une nouvelle configuration directement au nœud cible ou si vous vous connectez à un service d’extraction, et que DSC détecte une nouvelle configuration en interrogeant le service d’extraction. Si la configuration du nœud cible diffère de la configuration initiale, aucune action particulière n’est effectuée.
  - **ApplyAndMonitor** : cette valeur (valeur par défaut) indique à DSC d’appliquer chaque nouvelle configuration que vous avez transmise directement au nœud cible ou qui a été détectée sur un service d’extraction. Après l’application de la nouvelle configuration, si la configuration du nœud cible diffère du fichier de configuration, DSC signale l’écart dans les journaux. Pour plus d’informations sur la journalisation de DSC, consultez [Utilisation des journaux des événements pour diagnostiquer les erreurs de configuration de l’état souhaité](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect** : cette valeur indique à DSC d’appliquer chaque nouvelle configuration que vous avez transmise directement au nœud cible ou qui a été détectée sur un service d’extraction. Après l’application de la nouvelle configuration, si la configuration du nœud cible diffère du fichier de configuration, DSC signale l’écart dans les journaux, puis tente de modifier la configuration du nœud cible pour la rendre conforme au fichier de configuration.
- **ConfigurationModeFrequencyMins** : indique la fréquence (en minutes) à laquelle l’application en arrière-plan de DSC tente d’appliquer la configuration actuelle sur le nœud cible. La valeur par défaut est 15. Cette valeur peut être définie conjointement avec RefreshMode. Quand la propriété RefreshMode est définie sur « Pull », le nœud cible interroge le service de configuration à la fréquence définie par RefreshFrequencyMins et télécharge la configuration actuelle. Quelle que soit la valeur de RefreshMode, le moteur de cohérence applique la dernière configuration téléchargée sur le nœud cible, à la fréquence définie par ConfigurationModeFrequencyMins. La valeur de RefreshFrequencyMins doit être un nombre entier multiple de la valeur de ConfigurationModeFrequencyMins.
- **Credential** : indique les informations d’identification (comme avec Get-Credential) nécessaires pour accéder à des ressources distantes, par exemple, pour interroger le service de configuration.
- **DownloadManagerCustomData**: Représente un tableau qui contient des données personnalisées spécifiques au Gestionnaire de téléchargement.
- **DownloadManagerName**: Indique le nom de la configuration et le Gestionnaire de téléchargement du module.
- **RebootNodeIfNeeded** : certaines modifications de la configuration sur un nœud cible peuvent nécessiter un redémarrage de ce nœud pour être appliquées. Si cette propriété est définie sur **True**, le nœud est redémarré automatiquement dès la fin de l’application de la configuration, sans avertissement préalable. Si elle est définie sur **False** (valeur par défaut), la configuration est appliquée, mais le nœud doit être redémarré manuellement pour que les modifications prennent effet.
- **RefreshFrequencyMins** : propriété à définir si vous avez configuré un service d’extraction. Elle indique la fréquence (en minutes) à laquelle le Gestionnaire de configuration local interroge un service d’extraction pour télécharger la configuration actuelle. Cette valeur peut être définie conjointement avec ConfigurationModeFrequencyMins. Quand la propriété RefreshMode est définie sur « Pull », le nœud cible interroge le service d’extraction à la fréquence définie par RefreshFrequencyMins et télécharge la configuration actuelle. À la fréquence définie par ConfigurationModeFrequencyMins, le moteur de cohérence applique ensuite la dernière configuration téléchargée sur le nœud cible. Le système arrondit la valeur de RefreshFrequencyMins si elle n’est pas un nombre entier multiple de la valeur de ConfigurationModeFrequencyMins. La valeur par défaut est 30.
- **RefreshMode** : les valeurs possibles sont **Push** (valeur par défaut) et **Pull**. Dans une configuration en mode « push », vous devez créer un fichier de configuration sur chaque nœud cible, avec n’importe quel ordinateur client. En mode « pull », vous devez configurer un service d’extraction que le Gestionnaire de configuration local peut interroger pour obtenir les fichiers de configuration.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exemple de mise à jour des paramètres du Gestionnaire de configuration local

Pour mettre à jour les paramètres du Gestionnaire de configuration local d’un nœud cible, ajoutez un bloc **LocalConfigurationManager** au bloc du nœud dans un script de configuration, comme indiqué dans l’exemple suivant.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

L’exécution du script dans l’exemple ci-dessus crée un fichier MOF qui spécifie et contient les paramètres souhaités.
Pour appliquer les paramètres, utilisez l’applet de commande **Set-DscLocalConfigurationManager**, comme dans l’exemple qui suit.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Remarque** : Pour le paramètre **Path**, vous devez spécifier le même chemin que celui que vous avez spécifié pour le paramètre **OutputPath** dans l’appel de la configuration de l’exemple précédent.

Pour afficher les paramètres actuels du Gestionnaire de configuration local, utilisez l’applet de commande **Get-DscLocalConfigurationManager**.
Si vous appelez cette applet de commande sans spécifier de paramètre, elle affiche par défaut les paramètres du Gestionnaire de configuration local pour le nœud sur lequel vous l’exécutez.
Pour spécifier un autre nœud, utilisez le paramètre **CimSession** avec cette applet de commande.