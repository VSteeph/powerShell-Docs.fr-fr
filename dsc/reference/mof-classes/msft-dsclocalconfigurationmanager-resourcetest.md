---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678440"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager

Appelle directement la méthode **Test** d’une ressource DSC.

## <a name="syntax"></a>Syntaxe

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Paramètres

*ResourceType* \[in\] Nom de la ressource à appeler.

*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.

*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement. Utilisez l’applet de commande [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) pour découvrir les propriétés de ressources et leurs types.

*InDesiredState* \[out\] En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)