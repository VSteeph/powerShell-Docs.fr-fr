---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Tri d’objets"
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="234dd-103">Tri d’objets</span><span class="sxs-lookup"><span data-stu-id="234dd-103">Sorting Objects</span></span>
<span data-ttu-id="234dd-104">Vous pouvez organiser des données affichées pour faciliter leur analyse en utilisant l’applet de commande **Sort-Object**.</span><span class="sxs-lookup"><span data-stu-id="234dd-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="234dd-105">L’applet de commande **Sort-Object** prend le nom d’une ou plusieurs propriétés pour trier et retourner les données triées sur les valeurs de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="234dd-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="234dd-106">Prenez le problème de l’affichage de la liste d’instances Win32_SystemDriver.</span><span class="sxs-lookup"><span data-stu-id="234dd-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="234dd-107">Si vous souhaitez trier sur l’état (**State**), puis sur le nom (**Name**), vous pouvez taper ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="234dd-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="234dd-108">Bien que l’affichage soit long, les éléments sont regroupés par état :</span><span class="sxs-lookup"><span data-stu-id="234dd-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

<span data-ttu-id="234dd-109">Vous pouvez également trier les objets dans l’ordre inverse en spécifiant le paramètre **Descending**.</span><span class="sxs-lookup"><span data-stu-id="234dd-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="234dd-110">Cela a pour effet d’inverser l’ordre de tri, de sorte que les noms sont triés dans l’ordre alphabétique inverse et les nombres dans l’ordre décroissant de leur valeur.</span><span class="sxs-lookup"><span data-stu-id="234dd-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```
