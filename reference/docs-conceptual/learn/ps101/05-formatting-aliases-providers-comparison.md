---
title: Mise en forme, alias, fournisseurs, comparaison
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: eb23b048a50f10ea83d156c0499772b1be439336
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438000"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="b6308-102">Chapitre 5 - Mise en forme, alias, fournisseurs, comparaison</span><span class="sxs-lookup"><span data-stu-id="b6308-102">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="b6308-103">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b6308-103">Requirements</span></span>

<span data-ttu-id="b6308-104">Certains des exemples présentés dans ce chapitre nécessitent le module SQL Server PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-104">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="b6308-105">Le module est installé dans le cadre de [SQL Server Management Studio (SSMS)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="b6308-105">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="b6308-106">Il est également utilisé dans les chapitres suivants.</span><span class="sxs-lookup"><span data-stu-id="b6308-106">It's also used in subsequent chapters.</span></span> <span data-ttu-id="b6308-107">Téléchargez-le et installez-le sur votre ordinateur dans un environnement lab Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b6308-107">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="b6308-108">Mettre en forme à droite</span><span class="sxs-lookup"><span data-stu-id="b6308-108">Format Right</span></span>

<span data-ttu-id="b6308-109">Dans le chapitre 4, vous avez appris à filtrer aussi loin que possible à gauche.</span><span class="sxs-lookup"><span data-stu-id="b6308-109">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="b6308-110">La règle de mise en forme manuelle de la sortie d’une commande est similaire à cette règle, sauf qu’elle doit se produire aussi loin que possible à droite.</span><span class="sxs-lookup"><span data-stu-id="b6308-110">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="b6308-111">Les commandes de mise en forme les plus courantes sont `Format-Table` et `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="b6308-111">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="b6308-112">`Format-Wide` et `Format-Custom` peuvent également être utilisées, mais sont moins courantes.</span><span class="sxs-lookup"><span data-stu-id="b6308-112">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="b6308-113">Comme mentionné dans le chapitre 3, une commande qui retourne plus de quatre propriétés a comme valeur par défaut une liste, sauf si une mise en forme personnalisée est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b6308-113">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="b6308-114">Utilisez l’applet de commande `Format-Table` pour remplacer manuellement la mise en forme et afficher la sortie dans une table plutôt que dans une liste.</span><span class="sxs-lookup"><span data-stu-id="b6308-114">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="b6308-115">La sortie par défaut de `Get-Service` est trois propriétés dans une table.</span><span class="sxs-lookup"><span data-stu-id="b6308-115">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="b6308-116">Utilisez l’applet de commande `Format-List` pour remplacer la mise en forme par défaut et retourner les résultats dans une liste.</span><span class="sxs-lookup"><span data-stu-id="b6308-116">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="b6308-117">Notez que la simple redirection de `Get-Service` vers `Format-List` lui a fait retourner des propriétés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b6308-117">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="b6308-118">Cela ne se produit pas avec chaque commande en raison de la façon dont la mise en forme de cette commande particulière est configurée en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b6308-118">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="b6308-119">La première chose à connaître avec les applets de commande de mise en forme est qu’elles produisent des objets de mise en forme différents des objets normaux dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-119">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="b6308-120">Cela signifie que les commandes de mise en forme ne peuvent pas être redirigées vers la plupart des autres commandes.</span><span class="sxs-lookup"><span data-stu-id="b6308-120">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="b6308-121">Elles peuvent être redirigées vers certaines des commandes `Out-*`, mais c’est à peu près tout.</span><span class="sxs-lookup"><span data-stu-id="b6308-121">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="b6308-122">C’est pourquoi vous voulez effectuer une mise en forme à la toute fin de la ligne (mettre en forme à droite).</span><span class="sxs-lookup"><span data-stu-id="b6308-122">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="b6308-123">Alias</span><span class="sxs-lookup"><span data-stu-id="b6308-123">Aliases</span></span>

<span data-ttu-id="b6308-124">Dans PowerShell, un alias est un nom plus court pour une commande.</span><span class="sxs-lookup"><span data-stu-id="b6308-124">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="b6308-125">PowerShell comprend un ensemble d’alias intégrés. Vous pouvez également définir vos propres alias.</span><span class="sxs-lookup"><span data-stu-id="b6308-125">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="b6308-126">L’applet de commande `Get-Alias` est utilisée pour rechercher des alias.</span><span class="sxs-lookup"><span data-stu-id="b6308-126">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="b6308-127">Si vous connaissez déjà l’alias d’une commande, le paramètre **Name** est utilisé pour déterminer la commande à laquelle l’alias est associé.</span><span class="sxs-lookup"><span data-stu-id="b6308-127">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="b6308-128">Vous pouvez spécifier plusieurs alias pour la valeur du paramètre **Name**.</span><span class="sxs-lookup"><span data-stu-id="b6308-128">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="b6308-129">Vous verrez souvent que le paramètre **Name** est omis car il s’agit d’un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="b6308-129">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="b6308-130">Si vous voulez rechercher des alias pour une commande, vous devez utiliser le paramètre **Definition**.</span><span class="sxs-lookup"><span data-stu-id="b6308-130">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="b6308-131">Il n’est pas possible d’utiliser le paramètre **Definition** de façon positionnelle. Il doit donc être spécifié.</span><span class="sxs-lookup"><span data-stu-id="b6308-131">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="b6308-132">Les alias peuvent vous faire gagner quelques séquences de touches et ils fonctionnent correctement quand vous tapez des commandes dans la console.</span><span class="sxs-lookup"><span data-stu-id="b6308-132">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="b6308-133">Ils ne doivent pas être utilisés dans des scripts ou du code que vous enregistrez ou que vous partagez avec d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b6308-133">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="b6308-134">Comme mentionné plus haut dans ce document, l’utilisation de noms d’applets de commande et de paramètres complets est auto-documentée et est plus facile à comprendre.</span><span class="sxs-lookup"><span data-stu-id="b6308-134">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="b6308-135">Soyez prudent lors de la création de vos propres alias car ils n’existent que dans votre session PowerShell actuelle sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6308-135">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="b6308-136">Fournisseurs</span><span class="sxs-lookup"><span data-stu-id="b6308-136">Providers</span></span>

<span data-ttu-id="b6308-137">Dans PowerShell, un fournisseur est une interface qui permet d’accéder à un magasin de données comme avec un système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b6308-137">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="b6308-138">Il existe un certain nombre de fournisseurs intégrés dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-138">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="b6308-139">Comme vous pouvez le voir dans les résultats précédents, il existe des fournisseurs intégrés pour le registre, les alias, les variables d’environnement, le système de fichiers, les fonctions, les variables, les certificats et WSMan.</span><span class="sxs-lookup"><span data-stu-id="b6308-139">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="b6308-140">Les lecteurs réels utilisés par ces fournisseurs pour exposer leur magasin de données peuvent être déterminés à l’aide de l’applet de commande `Get-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="b6308-140">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="b6308-141">L’applet de commande `Get-PSDrive` affiche non seulement les lecteurs exposés par les fournisseurs, mais également les lecteurs logiques Windows, notamment les lecteurs mappés à des partages réseau.</span><span class="sxs-lookup"><span data-stu-id="b6308-141">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="b6308-142">Les modules tiers comme le module Active Directory PowerShell et le module SQL Server PowerShell ajoutent tous les deux leur propre fournisseur PowerShell et PSDrive.</span><span class="sxs-lookup"><span data-stu-id="b6308-142">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="b6308-143">Importez les modules Active Directory et SQL Server PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-143">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="b6308-144">Vérifiez si des fournisseurs PowerShell supplémentaires ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="b6308-144">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="b6308-145">Notez que dans le jeu de résultats précédent, il existe désormais deux nouveaux fournisseurs PowerShell : un pour Active Directory et un autre pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6308-145">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="b6308-146">Un PSDrive a également été ajouté pour chacun de ces modules.</span><span class="sxs-lookup"><span data-stu-id="b6308-146">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="b6308-147">Les PSDrive sont accessibles exactement comme un système de fichiers traditionnel.</span><span class="sxs-lookup"><span data-stu-id="b6308-147">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="b6308-148">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="b6308-148">Comparison Operators</span></span>

<span data-ttu-id="b6308-149">PowerShell contient un certain nombre d’opérateurs de comparaison utilisés pour comparer des valeurs ou rechercher des valeurs qui correspondent à certains modèles.</span><span class="sxs-lookup"><span data-stu-id="b6308-149">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="b6308-150">Le tableau 5-1 contient une liste d’opérateurs de comparaison disponibles dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-150">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="b6308-151">Opérateur</span><span class="sxs-lookup"><span data-stu-id="b6308-151">Operator</span></span>    |                          <span data-ttu-id="b6308-152">Définition</span><span class="sxs-lookup"><span data-stu-id="b6308-152">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="b6308-153">Égal à</span><span class="sxs-lookup"><span data-stu-id="b6308-153">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="b6308-154">Différent de</span><span class="sxs-lookup"><span data-stu-id="b6308-154">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="b6308-155">Supérieur à</span><span class="sxs-lookup"><span data-stu-id="b6308-155">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="b6308-156">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="b6308-156">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="b6308-157">Inférieur à</span><span class="sxs-lookup"><span data-stu-id="b6308-157">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="b6308-158">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="b6308-158">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="b6308-159">Correspondance à l’aide du caractère générique `*`</span><span class="sxs-lookup"><span data-stu-id="b6308-159">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="b6308-160">Absence de correspondance à l’aide du caractère générique `*`</span><span class="sxs-lookup"><span data-stu-id="b6308-160">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="b6308-161">Correspond à l’expression régulière spécifiée</span><span class="sxs-lookup"><span data-stu-id="b6308-161">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="b6308-162">Ne correspond pas à l’expression régulière spécifiée</span><span class="sxs-lookup"><span data-stu-id="b6308-162">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="b6308-163">Détermine si la collection contient une valeur spécifiée</span><span class="sxs-lookup"><span data-stu-id="b6308-163">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="b6308-164">Détermine si une collection ne contient pas de valeur spécifique</span><span class="sxs-lookup"><span data-stu-id="b6308-164">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="b6308-165">Détermine si une valeur spécifiée se trouve dans une collection</span><span class="sxs-lookup"><span data-stu-id="b6308-165">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="b6308-166">Détermine si une valeur spécifiée ne se trouve pas dans une collection</span><span class="sxs-lookup"><span data-stu-id="b6308-166">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="b6308-167">Remplace la valeur spécifiée</span><span class="sxs-lookup"><span data-stu-id="b6308-167">Replaces the specified value</span></span>                                 |

<span data-ttu-id="b6308-168">Tous les opérateurs listés dans le tableau 5-1 ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="b6308-168">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="b6308-169">Placez un `c` devant l’opérateur listé dans le tableau 5-1 pour qu’il respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="b6308-169">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="b6308-170">Par exemple, `-ceq` est la version qui respecte la casse de l’opérateur de comparaison `-eq`.</span><span class="sxs-lookup"><span data-stu-id="b6308-170">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="b6308-171">La casse appropriée « PowerShell » est égale à « PowerShell » en minuscules lors de l’utilisation de l’opérateur de comparaison Égal à.</span><span class="sxs-lookup"><span data-stu-id="b6308-171">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="b6308-172">Elle n’est pas égale à l’utilisation de la version qui respecte la casse de l’opérateur de comparaison Égal à.</span><span class="sxs-lookup"><span data-stu-id="b6308-172">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="b6308-173">L’opérateur de comparaison Différent de inverse la condition.</span><span class="sxs-lookup"><span data-stu-id="b6308-173">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="b6308-174">Les opérateurs Supérieur à, Supérieur ou égal à, Inférieur à et Inférieur ou égal à fonctionnent tous avec des chaînes ou des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="b6308-174">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="b6308-175">L’utilisation de l’opérateur Supérieur ou égal à au lieu de Supérieur à avec l’exemple précédent retourne la valeur **booléenne** true puisque cinq est égal à cinq.</span><span class="sxs-lookup"><span data-stu-id="b6308-175">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="b6308-176">En fonction des résultats des deux exemples précédents, vous pouvez probablement deviner comment les deux opérateurs Inférieur et Inférieur ou égal à fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="b6308-176">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="b6308-177">Les opérateurs `-Like` et `-Match` peuvent prêter à confusion, même pour les utilisateurs expérimentés de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6308-177">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="b6308-178">`-Like` est utilisé avec les caractères génériques `*` et `?` pour effectuer des correspondances « Like ».</span><span class="sxs-lookup"><span data-stu-id="b6308-178">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="b6308-179">`-Match` utilise une expression régulière pour effectuer la correspondance.</span><span class="sxs-lookup"><span data-stu-id="b6308-179">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="b6308-180">Utilisez l’opérateur de plage pour stocker les nombres 1 à 10 dans une variable.</span><span class="sxs-lookup"><span data-stu-id="b6308-180">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="b6308-181">Déterminez si la variable `$Numbers` inclut 15.</span><span class="sxs-lookup"><span data-stu-id="b6308-181">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="b6308-182">Déterminez si elle inclut le nombre 10.</span><span class="sxs-lookup"><span data-stu-id="b6308-182">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="b6308-183">`-NotContains` inverse la logique pour voir si la variable `$Numbers` ne contient pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="b6308-183">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="b6308-184">L’exemple précédent retourne la valeur **booléenne** true car il est vrai que la variable `$Numbers` ne contient pas 15.</span><span class="sxs-lookup"><span data-stu-id="b6308-184">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="b6308-185">Elle contient toutefois le nombre 10, donc le résultat est false quand elle est testée.</span><span class="sxs-lookup"><span data-stu-id="b6308-185">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="b6308-186">L’opérateur de comparaison « In » a été introduit pour la première fois dans PowerShell version 3.0.</span><span class="sxs-lookup"><span data-stu-id="b6308-186">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="b6308-187">Il est utilisé pour déterminer si une valeur est présente dans (« in ») un tableau.</span><span class="sxs-lookup"><span data-stu-id="b6308-187">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="b6308-188">La variable `$Numbers` est un tableau car elle contient plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="b6308-188">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="b6308-189">En d’autres termes, `-in` effectue le même test que l’opérateur de comparaison Contains excepté de le sens contraire.</span><span class="sxs-lookup"><span data-stu-id="b6308-189">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="b6308-190">Comme 15 ne se trouve pas dans le tableau `$Numbers`, la valeur false est retournée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b6308-190">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="b6308-191">Tout comme l’opérateur `-contains`, `not` inverse la logique de l’opérateur `-in`.</span><span class="sxs-lookup"><span data-stu-id="b6308-191">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="b6308-192">L’exemple précédent retourne la valeur false car le tableau `$Numbers` inclut 10 alors que la condition a été testée pour déterminer s’il ne contenait pas 10.</span><span class="sxs-lookup"><span data-stu-id="b6308-192">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="b6308-193">Comme 15 n’est pas dans (« not in ») le tableau `$Numbers`, il retourne la valeur **booléenne** true.</span><span class="sxs-lookup"><span data-stu-id="b6308-193">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="b6308-194">L’opérateur `-replace` fait exactement ce que vous pensez.</span><span class="sxs-lookup"><span data-stu-id="b6308-194">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="b6308-195">Il est utilisé pour remplacer un élément.</span><span class="sxs-lookup"><span data-stu-id="b6308-195">It's used to replace something.</span></span> <span data-ttu-id="b6308-196">La spécification d’une seule valeur remplace cette valeur par rien.</span><span class="sxs-lookup"><span data-stu-id="b6308-196">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="b6308-197">Dans l’exemple suivant, je remplace « Shell » par rien.</span><span class="sxs-lookup"><span data-stu-id="b6308-197">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="b6308-198">Si vous voulez remplacer une valeur par une autre valeur, spécifiez la nouvelle valeur après le modèle que vous voulez remplacer.</span><span class="sxs-lookup"><span data-stu-id="b6308-198">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="b6308-199">SQL Saturday à Baton Rouge est un événement dont j’essaie de parler chaque année.</span><span class="sxs-lookup"><span data-stu-id="b6308-199">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="b6308-200">Dans l’exemple suivant, je remplace le mot « Saturday » par l’abréviation « Sat ».</span><span class="sxs-lookup"><span data-stu-id="b6308-200">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="b6308-201">Il existe également des méthodes comme **Replace()** qui peuvent être utilisées pour remplacer des éléments de la même façon que l’opérateur Replace.</span><span class="sxs-lookup"><span data-stu-id="b6308-201">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="b6308-202">Toutefois, l’opérateur `-Replace` n’est pas sensible à la casse par défaut, alors que la méthode **Replace()** l’est.</span><span class="sxs-lookup"><span data-stu-id="b6308-202">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="b6308-203">Notez que le mot « Saturday » n’a pas été remplacé dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="b6308-203">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="b6308-204">En effet, il était spécifié dans une casse différente de l’original.</span><span class="sxs-lookup"><span data-stu-id="b6308-204">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="b6308-205">Quand le mot « Saturday » est spécifié dans la même casse que l’original, la méthode **Replace()** le remplace comme prévu.</span><span class="sxs-lookup"><span data-stu-id="b6308-205">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="b6308-206">Soyez prudent quand vous utilisez des méthodes pour transformer des données, car vous pouvez rencontrer des problèmes imprévus, comme l’échec du Test de Turquie (_Turkey Test_).</span><span class="sxs-lookup"><span data-stu-id="b6308-206">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="b6308-207">Pour obtenir un exemple, consultez l’article de blog intitulé [Using Pester to Test PowerShell Code with Other Cultures][] (Utilisation de Pester pour tester du code PowerShell avec d’autres cultures).</span><span class="sxs-lookup"><span data-stu-id="b6308-207">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="b6308-208">Je vous recommande d’utiliser autant que possible un opérateur plutôt qu’une méthode afin d’éviter ces types de problèmes.</span><span class="sxs-lookup"><span data-stu-id="b6308-208">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="b6308-209">Alors que les opérateurs de comparaison peuvent être utilisés comme indiqué dans les exemples précédents, je les utilise normalement avec l’applet de commande `Where-Object` pour effectuer un certain type de filtrage.</span><span class="sxs-lookup"><span data-stu-id="b6308-209">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="b6308-210">Résumé</span><span class="sxs-lookup"><span data-stu-id="b6308-210">Summary</span></span>

<span data-ttu-id="b6308-211">Dans ce chapitre, vous avez appris un certain nombre de rubriques différentes permettant d’inclure la mise en forme à droite, des alias, des fournisseurs et des opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="b6308-211">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="b6308-212">Révision</span><span class="sxs-lookup"><span data-stu-id="b6308-212">Review</span></span>

1. <span data-ttu-id="b6308-213">Pourquoi est-il nécessaire d’effectuer une mise en forme aussi loin que possible à droite ?</span><span class="sxs-lookup"><span data-stu-id="b6308-213">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="b6308-214">Comment déterminer l’applet de commande réelle qui correspond à l’alias `%` ?</span><span class="sxs-lookup"><span data-stu-id="b6308-214">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="b6308-215">Pourquoi ne devez-vous pas utiliser des alias dans des scripts que vous enregistrez ou dans du code que vous partagez avec d’autres utilisateurs ?</span><span class="sxs-lookup"><span data-stu-id="b6308-215">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="b6308-216">Dressez une liste des répertoires présents sur les lecteurs qui sont associés à l’un des fournisseurs de registre.</span><span class="sxs-lookup"><span data-stu-id="b6308-216">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="b6308-217">Quel est l’un des principaux avantages de l’utilisation de l’opérateur Replace au lieu de la méthode replace ?</span><span class="sxs-lookup"><span data-stu-id="b6308-217">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="b6308-218">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="b6308-218">Recommended Reading</span></span>

- <span data-ttu-id="b6308-219">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="b6308-219">[Format-Table][]</span></span>
- <span data-ttu-id="b6308-220">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="b6308-220">[Format-List][]</span></span>
- <span data-ttu-id="b6308-221">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="b6308-221">[Format-Wide][]</span></span>
- <span data-ttu-id="b6308-222">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="b6308-222">[about_Aliases][]</span></span>
- <span data-ttu-id="b6308-223">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="b6308-223">[about_Providers][]</span></span>
- <span data-ttu-id="b6308-224">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b6308-224">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="b6308-225">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="b6308-225">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/ (Utilisation de Pester pour tester du code PowerShell avec d’autres cultures)