---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Utilisation de classes et méthodes statiques"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="a0d68-103">Utilisation de classes et méthodes statiques</span><span class="sxs-lookup"><span data-stu-id="a0d68-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="a0d68-104">Certaines classes de .NET Framework ne peuvent pas être créées à l’aide de l’applet de commande **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="a0d68-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="a0d68-105">Par exemple, si vous essayez de créer un objet **System.Environment** ou **System.Math** avec l’applet de commande **New-Object**, vous obtenez les messages d’erreur suivants :</span><span class="sxs-lookup"><span data-stu-id="a0d68-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment
PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="a0d68-106">Ces erreurs se produisent parce qu’il n’existe aucun moyen de créer un objet à partir de ces classes.</span><span class="sxs-lookup"><span data-stu-id="a0d68-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="a0d68-107">Ces classes sont des bibliothèques de référence de méthodes et propriétés qui ne changent pas d’état.</span><span class="sxs-lookup"><span data-stu-id="a0d68-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="a0d68-108">Vous n’avez pas besoin de les créer. Vous les utilisez simplement.</span><span class="sxs-lookup"><span data-stu-id="a0d68-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="a0d68-109">Les classes et méthodes telles que celles-ci sont appelées *classes statiques*, car elles ne sont pas créées, détruites ou modifiées.</span><span class="sxs-lookup"><span data-stu-id="a0d68-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="a0d68-110">Par souci de clarté, nous fournirons des exemples qui utilisent des classes statiques.</span><span class="sxs-lookup"><span data-stu-id="a0d68-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="a0d68-111">Obtention de données d’environnement avec System.Environment</span><span class="sxs-lookup"><span data-stu-id="a0d68-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="a0d68-112">En règle générale, la première étape de l’utilisation d’un objet dans Windows PowerShell consiste à utiliser l’applet de commande Get-Member pour découvrir les membres qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="a0d68-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="a0d68-113">Avec des classes statiques, le processus est un peu différent, car la classe réelle n’est pas un objet.</span><span class="sxs-lookup"><span data-stu-id="a0d68-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="a0d68-114">Référence à la classe statique System.Environment</span><span class="sxs-lookup"><span data-stu-id="a0d68-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="a0d68-115">Vous pouvez faire référence à une classe statique en entourant le nom de la classe de crochets.</span><span class="sxs-lookup"><span data-stu-id="a0d68-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="a0d68-116">Par exemple, vous pouvez faire référence à la classe **System.Environment** en tapant le nom entre crochets.</span><span class="sxs-lookup"><span data-stu-id="a0d68-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="a0d68-117">Cela a pour effet d’afficher des informations de type générique :</span><span class="sxs-lookup"><span data-stu-id="a0d68-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="a0d68-118">Comme mentionné précédemment, Windows PowerShell ajoute automatiquement « **System.** »</span><span class="sxs-lookup"><span data-stu-id="a0d68-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="a0d68-119">aux noms de type lorsque vous utilisez l’applet de commande **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="a0d68-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="a0d68-120">La même chose se produisant en cas d’utilisation d’un nom de type entre crochets, vous pouvez spécifier **\[System.Environment]** en tant que **\[Environment]**.</span><span class="sxs-lookup"><span data-stu-id="a0d68-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="a0d68-121">La classe **System.Environment** contient des informations générales sur l’environnement de travail pour le processus actuel, c’est-à-dire powershell.exe lorsque vous travaillez dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0d68-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="a0d68-122">Si vous essayez d’afficher les détails de cette classe en tapant **\[System.Environment] | Get-Member**, le type d’objet est signalé comme étant **System.RuntimeType**, pas **System.Environment** :</span><span class="sxs-lookup"><span data-stu-id="a0d68-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="a0d68-123">Pour afficher les membres statiques avec Get-Member, spécifiez le paramètre **Static** paramètre :</span><span class="sxs-lookup"><span data-stu-id="a0d68-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="a0d68-124">Nous pouvons désormais sélectionner des propriétés à afficher à partir de System.Environment.</span><span class="sxs-lookup"><span data-stu-id="a0d68-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="a0d68-125">Affichage de propriétés statiques de System.Environment</span><span class="sxs-lookup"><span data-stu-id="a0d68-125">Displaying Static Properties of System.Environment</span></span>
<span data-ttu-id="a0d68-126">Les propriétés de System.Environment sont également statiques, et doivent être spécifiées d’une autre façon que des propriétés normales.</span><span class="sxs-lookup"><span data-stu-id="a0d68-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="a0d68-127">Nous utilisons **::** pour indiquer à Windows PowerShell que nous souhaitons travailler avec une méthode ou propriété statique.</span><span class="sxs-lookup"><span data-stu-id="a0d68-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="a0d68-128">Pour afficher la commande utilisée pour lancer Windows PowerShell, nous vérifions la propriété **CommandLine** en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a0d68-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="a0d68-129">Pour vérifier la version du système d’exploitation, affichez la propriété OSVersion en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a0d68-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="a0d68-130">Nous pouvons vérifier si l’ordinateur est en cours d’arrêt en affichant la propriété **HasShutdownStarted** :</span><span class="sxs-lookup"><span data-stu-id="a0d68-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="a0d68-131">Opérations mathématiques avec System.Math</span><span class="sxs-lookup"><span data-stu-id="a0d68-131">Doing Math with System.Math</span></span>
<span data-ttu-id="a0d68-132">La classe statique System.Math est utile pour effectuer certaines opérations mathématiques.</span><span class="sxs-lookup"><span data-stu-id="a0d68-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="a0d68-133">Les membres importants de **System.Math** sont essentiellement des méthodes que nous pouvons afficher à l’aide de l’applet de commande **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="a0d68-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="a0d68-134">System.Math dispose de plusieurs méthodes portant le même nom, mais qui se distinguent par le type de leurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="a0d68-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="a0d68-135">Tapez la commande suivante pour répertorier les méthodes de la classe **System.Math**.</span><span class="sxs-lookup"><span data-stu-id="a0d68-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="a0d68-136">Cette opération affiche plusieurs méthodes mathématiques.</span><span class="sxs-lookup"><span data-stu-id="a0d68-136">This displays several mathematical methods.</span></span> <span data-ttu-id="a0d68-137">Voici une liste de commandes qui illustrent le fonctionnement de certaines méthodes courantes :</span><span class="sxs-lookup"><span data-stu-id="a0d68-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```
