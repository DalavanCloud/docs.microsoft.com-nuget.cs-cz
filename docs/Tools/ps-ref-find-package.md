---
title: "Najděte balíček NuGet referenční informace prostředí PowerShell | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 6/1/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Referenční dokumentace pro příkaz prostředí PowerShell najít balíčku v konzole Správce balíčků NuGet v sadě Visual Studio."
keywords: "NuGet konzoly Správce balíčků, příkazy prostředí NuGet Powershell, NuGet Powershell odkaz, najít balíček"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 47b8420cc49d0a76709cf3268af69fcff310d165
ms.sourcegitcommit: 262d026beeffd4f3b6fc47d780a2f701451663a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="find-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="6a378-104">Najít Package (konzola Správce balíčků v sadě Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6a378-104">Find-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="6a378-105">*Verze 3.0 +; Toto téma popisuje příkaz v rámci [Konzola správce balíčků NuGet](Package-Manager-Console.md) v sadě Visual Studio v systému Windows. Příkaz Obecné najít balíčků prostředí PowerShell najdete v článku [odkaz na prostředí PowerShell PackageManagement](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="6a378-105">*Version 3.0+; this topic describes the command within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows. For the generic PowerShell Find-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="6a378-106">Získá ze zdroje balíčků sadu vzdálených balíčků se zadané ID nebo klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="6a378-106">Gets the set of remote packages with specified ID or keywords from the package source.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a378-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a378-107">Syntax</span></span>

```ps
Find-Package [-Id] <keywords> -Source <string> [-AllVersions] [-First [<int>]]
    [-Skip <int>] [-IncludePrerelease] [-ExactMatch] [-StartWith] [<CommonParameters>]
```

## <a name="parameters"></a><span data-ttu-id="6a378-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a378-108">Parameters</span></span>

| <span data-ttu-id="6a378-109">Parametr</span><span class="sxs-lookup"><span data-stu-id="6a378-109">Parameter</span></span> | <span data-ttu-id="6a378-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6a378-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="6a378-111">ID &lt;klíčová slova&gt;</span><span class="sxs-lookup"><span data-stu-id="6a378-111">Id &lt;keywords&gt;</span></span> | <span data-ttu-id="6a378-112">(Povinné) Klíčová slova pro hledání zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="6a378-112">(Required) Keywords to use when searching the package source.</span></span> <span data-ttu-id="6a378-113">Pomocí - ExactMatch vrátit pouze balíčky, jehož ID balíčku odpovídá klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="6a378-113">Use -ExactMatch to return only those packages whose package ID matches the keywords.</span></span> <span data-ttu-id="6a378-114">Je-li zadána žádná klíčová slova `Find-Package` vrátí seznam balíčků prvních 20 počítačů podle stahování nebo číslo určeného - nejdřív.</span><span class="sxs-lookup"><span data-stu-id="6a378-114">If no keywords are given, `Find-Package` returns a list of the top 20 packages by downloads, or the number specified by -First.</span></span> <span data-ttu-id="6a378-115">Všimněte si, že - Id je volitelné a žádná operace.</span><span class="sxs-lookup"><span data-stu-id="6a378-115">Note that -Id is optional and a no-op.</span></span> |
| <span data-ttu-id="6a378-116">Zdroj</span><span class="sxs-lookup"><span data-stu-id="6a378-116">Source</span></span> | <span data-ttu-id="6a378-117">Cestu adresy URL nebo ke složce zdroji balíčků pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="6a378-117">The URL or folder path for the package source to search.</span></span> <span data-ttu-id="6a378-118">Cesty k místní složce může být absolutní, nebo relativně vzhledem k aktuální složce.</span><span class="sxs-lookup"><span data-stu-id="6a378-118">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="6a378-119">Pokud tento parametr vynechán, `Find-Package` hledá aktuálně vybraném zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="6a378-119">If omitted, `Find-Package` searches the currently selected package source.</span></span> |
| <span data-ttu-id="6a378-120">AllVersions</span><span class="sxs-lookup"><span data-stu-id="6a378-120">AllVersions</span></span> | <span data-ttu-id="6a378-121">Zobrazí všechny dostupné verze jednotlivých balíčků místo pouze nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="6a378-121">Displays all available versions of each package instead of only the latest version.</span></span> |
| <span data-ttu-id="6a378-122">první</span><span class="sxs-lookup"><span data-stu-id="6a378-122">First</span></span> | <span data-ttu-id="6a378-123">Počet balíčků, které mají být vráceny od začátku seznamu; Výchozí hodnota je 20.</span><span class="sxs-lookup"><span data-stu-id="6a378-123">The number of packages to return from the beginning of the list; the default is 20.</span></span> |
| <span data-ttu-id="6a378-124">Skip</span><span class="sxs-lookup"><span data-stu-id="6a378-124">Skip</span></span> | <span data-ttu-id="6a378-125">Vynechá první &lt;int&gt; balíčky ze seznamu zobrazených.</span><span class="sxs-lookup"><span data-stu-id="6a378-125">Omits the first &lt;int&gt; packages from the displayed list.</span></span>  |
| <span data-ttu-id="6a378-126">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="6a378-126">IncludePrerelease</span></span> | <span data-ttu-id="6a378-127">Obsahuje předběžné verze balíčků ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="6a378-127">Includes prerelease packages in the results.</span></span> |
| <span data-ttu-id="6a378-128">ExactMatch</span><span class="sxs-lookup"><span data-stu-id="6a378-128">ExactMatch</span></span> | <span data-ttu-id="6a378-129">Zadaný používat &lt;klíčová slova&gt; jako ID malá a velká písmena balíčku.</span><span class="sxs-lookup"><span data-stu-id="6a378-129">Specified to use &lt;keywords&gt; as a case-sensitive package ID.</span></span> |
| <span data-ttu-id="6a378-130">StartWith</span><span class="sxs-lookup"><span data-stu-id="6a378-130">StartWith</span></span> | <span data-ttu-id="6a378-131">Vrátí balíčky balíčku, jehož ID začíná &lt;klíčová slova&gt;.</span><span class="sxs-lookup"><span data-stu-id="6a378-131">Returns packages whose package ID begins with &lt;keywords&gt;.</span></span> |

<span data-ttu-id="6a378-132">Žádná z těchto parametrů přijmout kanálu vstup nebo zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="6a378-132">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="6a378-133">Společné parametry</span><span class="sxs-lookup"><span data-stu-id="6a378-133">Common Parameters</span></span>

<span data-ttu-id="6a378-134">`Find-Package`podporuje následující [společné parametry prostředí PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): ladění, Chyba akce, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, podrobná, WarningAction a WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a378-134">`Find-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="6a378-135">Příklady</span><span class="sxs-lookup"><span data-stu-id="6a378-135">Examples</span></span>

```ps
# Find packages containing keywords
Find-Package elmah
Find-Package logging

# List packages whose ID begins with Elmah
Find-Package Elmah -StartWith

# By default, Get-Package returns a list of 20 packages; use -First to show more
Find-Package logging -First 100

# List all versions of the package with the ID of "jquery"
Find-Package jquery -AllVersions -ExactMatch
```