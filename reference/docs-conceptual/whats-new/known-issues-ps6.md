---
ms.date: 02/03/2020
keywords: powershell,core
title: Problèmes connus de PowerShell 6.0
ms.openlocfilehash: e9550e3db53865cfc2713d1d80665cced6f0d47a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76996101"
---
# <a name="known-issues-for-powershell-60"></a>Problèmes connus de PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problèmes connus de PowerShell sur les plateformes autres que Windows

Les versions alpha de PowerShell sous Linux et macOS sont globalement fonctionnelles, mais présentent d’importantes limitations et quelques problèmes d’utilisation. Les versions bêta de PowerShell sous Linux et macOS sont plus fonctionnelles et stables que les versions alpha, mais elles sont susceptibles de comporter des bogues et des fonctionnalités manquantes. Dans certains cas, ces problèmes sont tout simplement des bogues qui n’ont pas encore été corrigés. Dans d’autres (par exemple, les alias par défaut de ls, cp, etc.), nous attendons les commentaires de la communauté au sujet des choix que nous avons faits.

Remarque : en raison des similitudes que présentent de nombreux sous-systèmes sous-jacents, PowerShell sur Linux et PowerShell sur macOS tendent à partagent le même niveau de maturité pour les fonctionnalités comme pour les bogues. Sauf mention contraire, les problèmes mentionnés dans cette section s’appliquent aux deux systèmes d’exploitation.

### <a name="case-sensitivity-in-powershell"></a>Respect de la casse dans PowerShell

Historiquement, PowerShell ne respecte jamais la casse, à quelques exceptions près. Sur les systèmes d’exploitation de type UNIX, le système de fichiers respecte majoritairement la casse ; PowerShell est conforme à ce standard, ce qui transparaît de différentes manières, évidentes ou non.

#### <a name="directly"></a>Directement

- Lorsque vous spécifiez un fichier dans PowerShell, vous devez utiliser la bonne casse.

#### <a name="indirectly"></a>Indirectement

- Si un script tente de charger un module dont le nom n'a pas la bonne casse, l’opération échoue. Ce comportement peut poser problème pour les scripts existants si le nom par lequel le module est référencé ne correspond pas au nom réel du fichier.
- La saisie semi-automatique par tabulation ne fonctionne pas si la casse du nom de fichier est incorrecte. Le fragment à compléter doit respecter la casse. (Le complètement respecte la casse pour le nom et les membres de type.)

### <a name="ps1-file-extensions"></a>Extensions de fichier .PS1

Les scripts PowerShell doivent se terminer par `.ps1` pour que l’interpréteur comprenne comment les charger et les exécuter dans le processus actuel. Le comportement habituel attendu de PowerShell implique l’exécution de scripts au cours du processus actif. Il est possible d’ajouter le nombre magique `#!` à un script n’ayant pas d’extension `.ps1`, mais celui-ci s’exécute alors dans une nouvelle instance de PowerShell, ce qui empêche le script de fonctionner correctement en cas d’échange d’objets. (Remarque : Ce comportement peut être souhaitable pour exécuter un script PowerShell à partir de `bash` ou d’un autre shell.)

### <a name="missing-command-aliases"></a>Alias de commandes manquants

Sous Linux/macOS, les « alias de commodité » des commandes de base `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount` et `ps` ont été supprimés. Sous Windows, PowerShell fournit un ensemble d’alias qui correspondent au nom des commandes Linux pour le confort de l’utilisateur. Ces alias ont été supprimés à partir des distributions PowerShell sous Linux/macOS par défaut, ce qui permet d’exécuter l’exécutable natif sans spécifier de chemin d’accès.

Cette mesure comporte des avantages et des inconvénients. La suppression des alias expose l’expérience des commandes natives à l’utilisateur de PowerShell, mais réduit les fonctionnalités du shell, car les commandes natives retournent des chaînes et non des objets.

> [!NOTE]
> L’équipe PowerShell aimerait avoir votre avis sur ce point. Quelle est la meilleure solution ?
> Devons-nous laisser les choses telles quelles ou rétablir les alias de commodité ? Voir [Problème #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Prise en charge manquante du caractère générique

Actuellement, PowerShell ne procède à l’expansion de caractères génériques que pour les applets de commande intégrées sous Windows et pour les binaires ou les commandes externes ainsi que les applets de commande sous Linux. De ce fait, une commande du type `ls
*.txt` échoue, car l’astérisque n’est pas développée pour correspondre aux noms de fichiers. Vous pouvez contourner ce problème en écrivant `ls (gci *.txt | % name)` ou, plus simplement, `gci *.txt`, avec l’équivalent intégré de `ls` de PowerShell.

Accédez à [#954](https://github.com/PowerShell/PowerShell/issues/954) pour nous donner votre avis sur la façon d’améliorer l’expérience d’utilisation des caractères génériques sous Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>Comparaison entre .NET Framework et .NET Core Framework

PowerShell sous Linux/macOS utilise .NET Core, qui est un sous-ensemble de la version complète de .NET Framework sous Microsoft Windows. C’est un point important, car PowerShell offre un accès direct aux méthodes, types de frameworks, etc. sous-jacents. Par conséquent, les scripts qui s’exécutent sous Windows risquent de ne pas fonctionner sur les plateformes autres que Windows en raison des différences d’infrastructure. Pour plus d’informations sur .NET Core Framework, consultez [dotnetfoundation.org](https://dotnetfoundation.org/).

Avec l’arrivée de [.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/), .NET Core 2.0 réintègre la plupart des types et méthodes traditionnels présents dans la version complète de .NET Framework. PowerShell Core peut donc charger de nombreux modules Windows PowerShell traditionnels sans modification. Vous pouvez suivre [ici](https://github.com/PowerShell/PowerShell/projects/4) nos travaux liés à .NET Standard 2.0.

### <a name="redirection-issues"></a>Problèmes de redirection

La redirection d’entrée n’est pas prise en charge dans PowerShell, quelle que soit la plateforme.
[Problème #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Utilisez `Get-Content` pour écrire le contenu d’un fichier dans le pipeline.

La sortie redirigée contient la marque d’ordre d’octet (BOM) Unicode lorsque l’encodage UTF-8 par défaut est utilisé. Cet indicateur pose problème avec les utilitaires qui ne l’attendent pas ou en cas d’ajout à un fichier. Utilisez `-Encoding Ascii` pour écrire du texte ASCII, qui n’a pas de marque d’ordre d’octet (BOM).

> [!Note]
> Accédez à [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) pour nous donner votre avis sur la façon d’améliorer l’expérience d’encodage de PowerShell Core sur toutes les plateformes. Nous travaillons actuellement à prendre en charge UTF-8 sans marque d’ordre d’octet et éventuellement à modifier les encodages par défaut pour diverses applets de commande sur différentes plateformes.

### <a name="job-control"></a>Contrôle des tâches

Le contrôle des tâches n’est pas pris en charge du tout dans PowerShell sous Linux/macOS.
Les commandes `fg` et `bg` ne sont pas disponibles.

Pour l’instant, vous pouvez utiliser les [travaux PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs) qui fonctionnent sur toutes les plateformes.

### <a name="remoting-support"></a>Prise en charge de la communication à distance

Actuellement, PowerShell Core prend en charge la communication à distance PowerShell (PSRP) via WSMan avec l’authentification de base sous macOS et Linux, et avec l’authentification NTLM sous Linux. (L’authentification Kerberos n'est pas prise en charge.)

Le travail sur la communication à distance via WSMan est effectué dans le référentiel [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider).

PowerShell Core prend également en charge la communication à distance PowerShell (PSRP) via SSH sur toutes les plateformes (Windows, macOS et Linux). Si la prise en charge n’est pas encore possible en production, vous pouvez consulter [cette page](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md) pour en savoir plus sur sa configuration.

### <a name="just-enough-administration-jea-support"></a>Prise en charge de Just Enough Administration (JEA)

La possibilité de créer des points de terminaison de communication à distance à administration contrainte (JEA) n’est pas disponible à l’heure actuelle dans PowerShell sous Linux/macOS. Cette fonctionnalité n’entre pas dans le champ de la version 6.0 ; nous l’étudierons après la version 6.0, car elle implique un gros travail de conception.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` et PowerShell

PowerShell exécute la plupart des commandes en mémoire (par exemple, Python ou Ruby). De ce fait, il n’est pas possible d’utiliser sudo directement avec les modules intégrés de PowerShell. (Vous pouvez, bien entendu, exécuter `pwsh` à partir de sudo.) S’il vous faut exécuter une applet de commande PowerShell dans PowerShell avec sudo, par exemple, `sudo Set-Date 8/18/2016`, faites `sudo pwsh Set-Date 8/18/2016`. De même, vous ne pouvez pas exécuter directement un module intégré de PowerShell. Vous devrez passer par `exec pwsh item_to_exec`.

Ce problème fait l’objet d’un suivi dans le ticket [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Applets de commande manquantes

De nombreuses commandes (applets de commande) normalement disponibles dans PowerShell ne sont pas disponibles sous Linux/macOS. Dans la plupart des cas, elles ne sont pas pertinentes sur ces plateformes (par exemple, les fonctionnalités propres à Windows, comme le Registre). D’autres commandes, comme le contrôle de service (Get/Start/Stop-Service) sont présentes, mais non fonctionnelles. Les versions à venir sont susceptibles de corriger ces problèmes, en réparant les cmdlets non fonctionnelles et en en ajoutant de nouvelles au fur et à mesure.

### <a name="command-availability"></a>Disponibilité des commandes

Le tableau suivant répertorie les commandes dont on sait qu’elles ne fonctionnent pas dans PowerShell sous Linux/macOS.

|Commandes|État de fonctionnement|Notes|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Non disponible.|Ces commandes ne sont pas reconnues. Ce problème devrait être corrigé dans une version ultérieure.|
|`Get-Acl`, `Get-AuthenticodeSignature`, `Get-CmsMessage`, `New-FileCatalog`, `Protect-CmsMessage`, `Set-Acl`, `Set-AuthenticodeSignature`, `Test-FileCatalog`, `Unprotect-CmsMessage`|Non disponible.|Ces commandes ne sont pas reconnues. Ce problème devrait être corrigé dans une version ultérieure.|
|`Wait-Process`|Disponible, mais ne fonctionne pas correctement. |Par exemple, `Start-Process gvim -PassThru | Wait-Process` ne fonctionne pas ; il ne parvient pas à attendre le processus.|
|`Connect-PSSession`, `Disable-PSRemoting`, `Disable-PSSessionConfiguration`, `Disconnect-PSSession`, `Enable-PSRemoting`, `Enable-PSSessionConfiguration`, `Get-PSSessionCapability`, `Get-PSSessionConfiguration`, `New-PSSessionConfigurationFile`, `Receive-PSSession`, `Register-PSSessionConfiguration`, `Set-PSSessionConfiguration`, `Test-PSSessionConfigurationFile`, `Unregister-PSSessionConfiguration`|Non disponible.|Ces commandes ne sont pas reconnues. Ce problème devrait être corrigé dans une version ultérieure.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Remove-Event`, `Unregister-Event`|Disponible, mais aucune source d’événement n’est disponible.|Les commandes de gestion des événements de PowerShell sont présentes, mais la plupart des sources d’événements utilisées avec les commandes (par exemple, System.Timers.Timer) ne sont pas disponibles sous Linux, ce qui rend les commandes inutiles dans la version alpha.|
|`Set-ExecutionPolicy`|Disponible, mais ne fonctionne pas.|Retourne un message indiquant que la prise en charge n’est pas assurée sur cette plateforme. La stratégie d’exécution est une « ceinture de sécurité » orientée utilisateur qui permet d’empêcher l’utilisateur de commettre des erreurs coûteuses. Il ne s’agit pas d’une limite de sécurité.|
|`New-PSSessionOption`, `New-PSTransportOption`|Disponible, mais `New-PSSession` ne fonctionne pas.|Il n’a pas été vérifié que `New-PSSessionOption` et `New-PSTransportOption` fonctionnaient, maintenant que `New-PSSession` fonctionne.|
