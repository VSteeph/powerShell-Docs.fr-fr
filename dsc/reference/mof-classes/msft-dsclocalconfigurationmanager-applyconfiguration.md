---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677623"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager

Utilise l’agent de configuration pour appliquer la configuration en attente.

S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.

## <a name="syntax"></a>Syntaxe

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Paramètres

*force* \[in\] Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques

Il s’agit d’une méthode statique.

## <a name="requirements"></a>Spécifications

**MOF :** DscCore.mof

**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Voir aussi

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)