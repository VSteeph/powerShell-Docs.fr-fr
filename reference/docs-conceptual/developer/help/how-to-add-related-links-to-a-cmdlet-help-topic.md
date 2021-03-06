---
title: Comment ajouter des liens connexes à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560268"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande

Cette section décrit comment ajouter des références à d’autres contenus liés à une rubrique d’aide de l’applet de commande® Windows PowerShell. Étant donné que ces références s’affichent dans une fenêtre de commande, elles ne sont pas directement liées au contenu référencé.

Dans les rubriques d’aide sur les applets de commande incluses dans Windows PowerShell®, ces liens font référence à d’autres applets de commande, à un contenu conceptuel (« about_ »), ainsi qu’à d’autres documents et fichiers d’aide qui ne sont pas associés à des® Windows PowerShell.

Le code XML suivant montre comment ajouter un nœud RelatedLinks qui contient deux références à des rubriques connexes.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
