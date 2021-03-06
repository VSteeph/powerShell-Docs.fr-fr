---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Empaqueter et charger des ressources vers un serveur Pull
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278497"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Empaqueter et charger des ressources vers un serveur Pull

Les sections ci-dessous supposent que vous avez déjà configuré un serveur Pull. Si vous n’avez pas configuré votre serveur Pull, vous pouvez utiliser les guides suivants :

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)

Chaque nœud cible peut être configuré pour télécharger les configurations et les ressources, et même pour signaler son état. Cet article montre comment charger des ressources afin qu’elles soient disponibles pour être téléchargées, et comment configurer les clients pour télécharger automatiquement des ressources. Lorsque le nœud reçoit une configuration attribuée, via un serveur **Pull** ou **Push** (v5), il télécharge automatiquement toutes les ressources requises par la configuration depuis l’emplacement spécifié dans le gestionnaire de configuration local (LCM).

## <a name="package-resource-modules"></a>Modules Resource Package

Chaque ressource disponible pour un client à télécharger doit être stockée dans un fichier « .zip ». L’exemple ci-dessous montre les étapes nécessaires en utilisant la ressource [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).

> [!NOTE]
> Si vous avez tous les clients à l’aide de PowerShell 4.0, vous devez aplanir la structure de dossiers de ressources et supprimez tous les dossiers version. Pour plus d’informations, consultez [Plusieurs versions de ressources](../configurations/import-dscresource.md#multiple-resource-versions).

Vous pouvez compresser le répertoire des ressources à l’aide de l’utilitaire, du script ou de la méthode de votre choix. Dans Windows, *cliquez avec le bouton droit* sur le répertoire « xPSDesiredStateConfiguration », puis sélectionnez « Envoyer vers », puis « Dossier compressé ».

![Cliquer avec le bouton droit](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>Nommer l’archive de ressources

L’archive de ressources doit être nommée avec le format suivant :

```
{ModuleName}_{Version}.zip
```

Dans l’exemple ci-dessus, le fichier « xPSDesiredStateConfiguration.zip » doit être renommé « xPSDesiredStateConfiguration_8.4.4.0.zip ».

### <a name="create-checksums"></a>Créer des sommes de contrôle

Une fois le module de ressources compressé et renommé, vous devez créer une **somme de contrôle**.  La **somme de contrôle** est utilisée par le gestionnaire de configuration local sur le client pour déterminer si la ressource a été modifiée et doit être téléchargée à nouveau. Vous pouvez créer une **somme de contrôle** avec l’applet de commande [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), comme indiqué dans l’exemple ci-dessous.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Aucune sortie ne s’affichera, mais vous devriez maintenant voir un fichier « xPSDesiredStateConfiguration_8.4.4.0.zip.checksum ». Vous pouvez également exécuter `New-DSCCheckSum` dans un répertoire de fichiers à l’aide du paramètre `-Path`. Si une somme de contrôle existe déjà, vous pouvez forcer sa recréation avec le paramètre `-Force`.

### <a name="where-to-store-resource-archives"></a>Emplacement de stockage des archives de ressources

#### <a name="on-a-dsc-http-pull-server"></a>Sur un serveur Pull HTTP DSC

Lorsque vous configurez votre serveur Pull HTTP, comme expliqué dans la section [Configurer un serveur Pull HTTP DSC](pullServer.md), vous spécifiez des répertoires pour les clés **ModulePath** et **ConfigurationPath**. La clé **ConfigurationPath** indique l’emplacement où tous les fichiers « .mof » devraient être stockés. La clé **ModulePath** indique l’emplacement où les modules de ressources DSC devraient être stockés.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Sur un partage SMB

Si vous avez spécifié une clé **ResourceRepositoryShare**, lors de la configuration de votre client Pull, stockez les archives et les sommes de contrôle dans le répertoire **SourcePath** du bloc **ResourceRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Si vous n’avez spécifié qu’une clé **ConfigurationRepositoryShare**, lors de la configuration de votre client Pull, stockez les archives et les sommes de contrôle dans le répertoire **SourcePath** du bloc **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Mise à jour des ressources

Vous pouvez forcer un nœud à mettre à jour ses ressources en modifiant le numéro de version dans le nom de l’archive, ou en créant une somme de contrôle. Le client Pull recherchera des versions plus récentes des ressources requises, ainsi que des mises à jour les sommes de contrôle, lorsque son gestionnaire de configuration local est actualisé.

## <a name="see-also"></a>Voir aussi

- [Configurer un serveur Pull SMB DSC](pullServerSmb.md)
- [Configurer un serveur Pull HTTP DSC](pullServer.md)
