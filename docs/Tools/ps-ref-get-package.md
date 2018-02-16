---
title: "Referenční informace prostředí PowerShell Get balíček NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Referenční dokumentace pro příkaz prostředí PowerShell Get-balíčku v konzole Správce balíčků NuGet v sadě Visual Studio."
keywords: "NuGet konzoly Správce balíčků, příkazy prostředí NuGet Powershell, NuGet Powershell odkaz, Get-Package"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c38e0da2e98d2e5bf5b4fc165462e9abcfdd73c0
ms.sourcegitcommit: 262d026beeffd4f3b6fc47d780a2f701451663a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="get-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="a8a1a-104">Get-Package (konzola Správce balíčků v sadě Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a8a1a-104">Get-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="a8a1a-105">*Toto téma popisuje příkaz v rámci [Konzola správce balíčků NuGet](Package-Manager-Console.md) v sadě Visual Studio v systému Windows. Příkaz prostředí PowerShell Get-Package obecné najdete v článku [odkaz na prostředí PowerShell PackageManagement](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="a8a1a-105">*This topic describes the command within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows. For the generic PowerShell Get-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="a8a1a-106">Načte seznam balíčků nainstalovaných v místním úložišti, obsahuje seznam balíčků dostupné z balíčku zdroje při použití s přepínačem - ListAvailable nebo vypíše dostupné aktualizace, které při použití s přepínačem - Update.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-106">Retrieves the list of packages installed in the local repository, lists packages available from a package source when used with the -ListAvailable switch, or lists available updates when used with the -Update switch.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8a1a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8a1a-107">Syntax</span></span>

```ps
Get-Package -Source <string> [-ListAvailable] [-Updates] [-ProjectName <string>]
    [-Filter <string>] [-First <int>] [-Skip <int>] [-AllVersions] [-IncludePrerelease]
    [-PageSize] [<CommonParameters>]
```

<span data-ttu-id="a8a1a-108">Bez parametrů `Get-Package` zobrazí seznam balíčků nainstalovaných ve výchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-108">With no parameters, `Get-Package` displays the list of packages installed in the default project.</span></span>

## <a name="parameters"></a><span data-ttu-id="a8a1a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8a1a-109">Parameters</span></span>

| <span data-ttu-id="a8a1a-110">Parametr</span><span class="sxs-lookup"><span data-stu-id="a8a1a-110">Parameter</span></span> | <span data-ttu-id="a8a1a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a8a1a-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a8a1a-112">Zdroj</span><span class="sxs-lookup"><span data-stu-id="a8a1a-112">Source</span></span> | <span data-ttu-id="a8a1a-113">Adresu URL nebo cestu složky pro balíček.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-113">The URL or folder path for the package .</span></span> <span data-ttu-id="a8a1a-114">Cesty k místní složce může být absolutní, nebo relativně vzhledem k aktuální složce.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-114">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="a8a1a-115">Pokud tento parametr vynechán, `Get-Package` hledá aktuálně vybraném zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-115">If omitted, `Get-Package` searches the currently selected package source.</span></span> <span data-ttu-id="a8a1a-116">Při použití s příznakem-ListAvailable, výchozí hodnota je nuget.org.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-116">When used with -ListAvailable, defaults to nuget.org.</span></span> |
| <span data-ttu-id="a8a1a-117">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="a8a1a-117">ListAvailable</span></span> | <span data-ttu-id="a8a1a-118">Zobrazí seznam balíčků dostupné z balíčku zdroje, jako výchozí bude použit nuget.org. Výchozí hodnota je 50 balíčky ukazuje, pokud jsou zadány - PageSize nebo - první.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-118">Lists packages available from a package source, defaulting to nuget.org. Shows a default of 50 packages unless -PageSize and/or -First are specified.</span></span> |
| <span data-ttu-id="a8a1a-119">Aktualizace</span><span class="sxs-lookup"><span data-stu-id="a8a1a-119">Updates</span></span> | <span data-ttu-id="a8a1a-120">Zobrazí seznam balíčků, které mají k dispozici aktualizace ze zdroje balíčků.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-120">Lists packages that have an update available from the package source.</span></span> |
| <span data-ttu-id="a8a1a-121">ProjectName</span><span class="sxs-lookup"><span data-stu-id="a8a1a-121">ProjectName</span></span> | <span data-ttu-id="a8a1a-122">Projekt, ze kterého mají být získány nainstalované balíčky.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-122">The project from which to get installed packages.</span></span> <span data-ttu-id="a8a1a-123">Pokud tento parametr vynechán, vrátí nainstalované projekty pro celé řešení.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-123">If omitted, returns installed projects for the entire solution.</span></span> |
| <span data-ttu-id="a8a1a-124">Filtr</span><span class="sxs-lookup"><span data-stu-id="a8a1a-124">Filter</span></span> | <span data-ttu-id="a8a1a-125">Řetězec filtru sloužící k upřesnění seznamu balíčků použitím do ID balíčku, popisu a značkách.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-125">A filter string used to narrow down the list of packages by applying it to the package ID, description, and tags.</span></span> |
| <span data-ttu-id="a8a1a-126">první</span><span class="sxs-lookup"><span data-stu-id="a8a1a-126">First</span></span> | <span data-ttu-id="a8a1a-127">Počet balíčků, které mají být vráceny od začátku seznamu.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-127">The number of packages to return from the beginning of the list.</span></span> <span data-ttu-id="a8a1a-128">Pokud není zadáno, bude jako výchozí nastavena na 50.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-128">If not specified, defaults to 50.</span></span> |
| <span data-ttu-id="a8a1a-129">Skip</span><span class="sxs-lookup"><span data-stu-id="a8a1a-129">Skip</span></span> | <span data-ttu-id="a8a1a-130">Vynechá první &lt;int&gt; balíčky ze seznamu zobrazených.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-130">Omits the first &lt;int&gt; packages from the displayed list.</span></span>  |
| <span data-ttu-id="a8a1a-131">AllVersions</span><span class="sxs-lookup"><span data-stu-id="a8a1a-131">AllVersions</span></span> | <span data-ttu-id="a8a1a-132">Zobrazí všechny dostupné verze jednotlivých balíčků místo pouze nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-132">Displays all available versions of each package instead of only the latest version.</span></span> |
| <span data-ttu-id="a8a1a-133">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="a8a1a-133">IncludePrerelease</span></span> | <span data-ttu-id="a8a1a-134">Obsahuje předběžné verze balíčků ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-134">Includes prerelease packages in the results.</span></span> |
| <span data-ttu-id="a8a1a-135">PageSize</span><span class="sxs-lookup"><span data-stu-id="a8a1a-135">PageSize</span></span> | <span data-ttu-id="a8a1a-136">*(3.0 +)*  Při použití s příznakem-ListAvailable (povinné), počet balíčků, seznam, než se předá výzvy a pokračujte.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-136">*(3.0+)* When used with -ListAvailable (required), the number of packages to list before giving a prompt to continue.</span></span> |

<span data-ttu-id="a8a1a-137">Žádná z těchto parametrů přijmout kanálu vstup nebo zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-137">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="a8a1a-138">Společné parametry</span><span class="sxs-lookup"><span data-stu-id="a8a1a-138">Common Parameters</span></span>

<span data-ttu-id="a8a1a-139">`Get-Package`podporuje následující [společné parametry prostředí PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): ladění, Chyba akce, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, podrobná, WarningAction a WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8a1a-139">`Get-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="a8a1a-140">Příklady</span><span class="sxs-lookup"><span data-stu-id="a8a1a-140">Examples</span></span>

```ps
# Lists the packages installed in the current solution
Get-Package

# Lists the packages installed in a project
Get-Package -ProjectName MyProject

# Lists packages available in the current package source
Get-Package -ListAvailable

# Lists 30 packages at a time from the current source, and prompts to continue if more are available
Get-Package -ListAvailable -PageSize 30

# Lists packages with the Ninject keyword in the current source, up to 50
Get-Package -ListAvailable -Filter Ninject

# List all versions of packages matching the filter "jquery"
Get-Package -ListAvailable -Filter jquery -AllVersions

# Lists packages installed in the solution that have available updates
Get-Package -Updates

# Lists packages installed in a specific project that have available updates
Get-Package -Updates -ProjectName MyProject
```