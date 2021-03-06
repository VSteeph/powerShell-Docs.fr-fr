---
title: Guide pratique pour ajouter des exemples à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 82bee7b7bb0ef49203636f2a293075f3db924ce4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557088"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Éléments à connaître sur les exemples de l’aide sur les applets de commande

- Répertorie tous les noms de paramètres dans la commande, même si les noms de paramètres sont facultatifs. Cela permet à l’utilisateur d’interpréter facilement la commande.

- Évitez les alias et les noms de paramètres partiels, même s’ils fonctionnent dans Windows PowerShell®.

- Dans l’exemple de description, expliquez le raisonnement pour la construction de la commande. Expliquez pourquoi vous avez choisi des paramètres et des valeurs particuliers et comment utiliser des variables.

- Si la commande utilise des expressions, expliquez-les en détail.

- Si la commande utilise des propriétés et des méthodes d’objets, en particulier les propriétés qui n’apparaissent pas dans l’affichage par défaut, utilisez l’exemple comme une opportunité pour indiquer à l’utilisateur l’objet.

## <a name="help-views-that-display-examples"></a>Vues d’aide qui affichent des exemples

Les exemples apparaissent uniquement dans les vues détaillées et complètes de l’aide sur les applets de commande.

## <a name="adding-an-examples-node"></a>Ajout d’un nœud exemples

Le code XML suivant montre comment ajouter un nœud exemples qui contient un seul nœud exemple. Ajoutez des exemples de nœuds supplémentaires pour chaque exemple que vous souhaitez inclure dans la rubrique.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Ajout d’un titre d’exemple

Le code XML suivant montre comment ajouter un titre pour l’exemple. Le titre est utilisé pour définir l’exemple, à l’exception des autres exemples. Windows PowerShell® utilise un en-tête standard qui comprend un numéro d’exemple séquentiel.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Ajout de caractères précédents

Le code XML suivant montre comment ajouter des caractères, tels que l’invite de commandes Windows PowerShell, qui sont affichés immédiatement avant l’exemple de commande (sans espaces intermédiaires). Windows PowerShell® utilise l’invite de commandes Windows PowerShell : C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Ajout de la commande

Le code XML suivant montre comment ajouter la commande réelle de l’exemple. Lorsque vous ajoutez la commande, tapez le nom complet (n’utilisez pas d’alias) des applets de commande et des paramètres. En outre, utilisez des caractères minuscules dans la mesure du possible.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Ajout d’une description

Le code XML suivant montre comment ajouter une description pour l’exemple. Windows PowerShell® utilise un ensemble unique de \< balises MAML : para> pour la description, même si plusieurs \< balises MAML : para> peuvent être utilisées.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Ajout d’un exemple de sortie

Le code XML suivant montre comment ajouter la sortie de la commande. Les informations sur les résultats de la commande sont facultatives, mais dans certains cas, il est utile d’illustrer l’effet de l’utilisation de paramètres spécifiques. Windows PowerShell® utilise deux ensembles de \< balises MAML : para> vides pour séparer la sortie de commande de la commande.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
