---
title: "Referenční informace prostředí PowerShell NuGet BindingRedirect | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Referenční dokumentace pro příkaz prostředí PowerShell přidat BindingRedirect v konzole Správce balíčků NuGet v sadě Visual Studio."
keywords: "NuGet konzoly Správce balíčků, příkazy prostředí NuGet Powershell, NuGet Powershell odkaz, přidat BindingRedirect"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: b755970402f29a72b9a10f1a94e4a799e9cb71cf
ms.sourcegitcommit: 262d026beeffd4f3b6fc47d780a2f701451663a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="add-bindingredirect-package-manager-console-in-visual-studio"></a><span data-ttu-id="38907-104">Přidat BindingRedirect (konzola Správce balíčků v sadě Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="38907-104">Add-BindingRedirect (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="38907-105">*K dispozici pouze v rámci [Konzola správce balíčků NuGet](Package-Manager-Console.md) v sadě Visual Studio v systému Windows.*</span><span class="sxs-lookup"><span data-stu-id="38907-105">*Available only within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows.*</span></span>

<span data-ttu-id="38907-106">Hledá ve všech sestaveních ve výstupní cestě pro projekt a potřeby přidá přesměrování vazby do konfiguračního souboru aplikace nebo webu.</span><span class="sxs-lookup"><span data-stu-id="38907-106">Examines all assemblies within the output path for a project and adds binding redirects to the application or web configuration file where necessary.</span></span> <span data-ttu-id="38907-107">Tento příkaz spustí automaticky při instalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="38907-107">This command is run automatically when installing a package.</span></span>

<span data-ttu-id="38907-108">Podrobnosti o vazby přesměrování a proč se používají, najdete v části [přesměrování verzí sestavení](/dotnet/framework/configure-apps/redirect-assembly-versions) v dokumentaci k rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="38907-108">For details on binding redirects and why they are used, see [Redirecting Assembly Versions](/dotnet/framework/configure-apps/redirect-assembly-versions) in the .NET documentation.</span></span>

## <a name="syntax"></a><span data-ttu-id="38907-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38907-109">Syntax</span></span>

```ps
Add-BindingRedirect [-ProjectName] <string> [<CommonParameters>]
```

## <a name="parameters"></a><span data-ttu-id="38907-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="38907-110">Parameters</span></span>

| <span data-ttu-id="38907-111">Parametr</span><span class="sxs-lookup"><span data-stu-id="38907-111">Parameter</span></span> | <span data-ttu-id="38907-112">Popis</span><span class="sxs-lookup"><span data-stu-id="38907-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="38907-113">ProjectName</span><span class="sxs-lookup"><span data-stu-id="38907-113">ProjectName</span></span> | <span data-ttu-id="38907-114">(Povinné) Projekt, pro které má být přidána přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="38907-114">(Required) The project to which to add binding redirects.</span></span> <span data-ttu-id="38907-115">Je volitelný přepínač - ProjectName sám sebe.</span><span class="sxs-lookup"><span data-stu-id="38907-115">The -ProjectName switch itself is optional.</span></span> |

<span data-ttu-id="38907-116">Žádná z těchto parametrů přijmout kanálu vstup nebo zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="38907-116">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="38907-117">Společné parametry</span><span class="sxs-lookup"><span data-stu-id="38907-117">Common Parameters</span></span>

<span data-ttu-id="38907-118">`Add-BindingRedirect`podporuje následující [společné parametry prostředí PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): ladění, Chyba akce, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, podrobná, WarningAction a WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38907-118">`Add-BindingRedirect` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="38907-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="38907-119">Examples</span></span>

```ps
Add-BindingRedirect MyProject

Add-BindingRedirect -ProjectName MyProject
```