---
title: Příkaz pack NuGet rozhraní příkazového řádku
description: Referenční dokumentace pro příkaz nuget.exe pack
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: a2468b099a822e69298ea78c80cfd1d5d5c09938
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="pack-command-nuget-cli"></a><span data-ttu-id="e4969-103">Příkaz Pack (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="e4969-103">pack command (NuGet CLI)</span></span>

<span data-ttu-id="e4969-104">**Platí pro:** balíček vytvoření &bullet; **podporované verze:** 2.7 +</span><span class="sxs-lookup"><span data-stu-id="e4969-104">**Applies to:** package creation &bullet; **Supported versions:** 2.7+</span></span>

<span data-ttu-id="e4969-105">Vytvoří balíček NuGet založený na zadaný `.nuspec` nebo soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="e4969-105">Creates a NuGet package based on the specified `.nuspec` or project file.</span></span> <span data-ttu-id="e4969-106">`dotnet pack` Příkazu (najdete v části [dotnet příkazy](dotnet-Commands.md)) a `msbuild /t:pack` (najdete v části [cíle MSBuild](../reference/msbuild-targets.md)) může být použita jako alternativ.</span><span class="sxs-lookup"><span data-stu-id="e4969-106">The `dotnet pack` command (see [dotnet Commands](dotnet-Commands.md)) and `msbuild /t:pack` (see [MSBuild targets](../reference/msbuild-targets.md)) may be used as alternates.</span></span>

> [!Important]
> <span data-ttu-id="e4969-107">V části Mono není podporováno vytváření balíčku ze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="e4969-107">Under Mono, creating a package from a project file is not supported.</span></span> <span data-ttu-id="e4969-108">Také budete muset upravit jiné než místní cesty v `.nuspec` souborů na formátu UNIX cesty, jako jsou třeba nuget.exe nepřevádí názvy cest Windows sám sebe.</span><span class="sxs-lookup"><span data-stu-id="e4969-108">You also need to adjust non-local paths in the `.nuspec` file to Unix-style paths, as nuget.exe doesn't convert Windows pathnames itself.</span></span>

## <a name="usage"></a><span data-ttu-id="e4969-109">Použití</span><span class="sxs-lookup"><span data-stu-id="e4969-109">Usage</span></span>

```cli
nuget pack <nuspecPath | projectPath> [options] [-Properties ...]
```

<span data-ttu-id="e4969-110">kde `<nuspecPath>` a `<projectPath>` zadejte `.nuspec` nebo projektu soubor, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e4969-110">where `<nuspecPath>` and `<projectPath>` specify the `.nuspec` or project file, respectively.</span></span>

## <a name="options"></a><span data-ttu-id="e4969-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e4969-111">Options</span></span>

| <span data-ttu-id="e4969-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="e4969-112">Option</span></span> | <span data-ttu-id="e4969-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e4969-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="e4969-114">BasePath</span><span class="sxs-lookup"><span data-stu-id="e4969-114">BasePath</span></span> | <span data-ttu-id="e4969-115">Nastaví základní cesta soubory definované v `.nuspec` souboru.</span><span class="sxs-lookup"><span data-stu-id="e4969-115">Sets the base path of the files defined in the `.nuspec` file.</span></span> |
| <span data-ttu-id="e4969-116">Sestavení</span><span class="sxs-lookup"><span data-stu-id="e4969-116">Build</span></span> | <span data-ttu-id="e4969-117">Určuje, že projekt by měly být vytvořeny před vytvořením balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-117">Specifies that the project should be built before building the package.</span></span> |
| <span data-ttu-id="e4969-118">Vyloučení</span><span class="sxs-lookup"><span data-stu-id="e4969-118">Exclude</span></span> | <span data-ttu-id="e4969-119">Určuje jeden nebo více vzory zástupných znaků, které chcete vyloučit při vytváření balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-119">Specifies one or more wildcard patterns to exclude when creating a package.</span></span> <span data-ttu-id="e4969-120">Chcete-li zadat více než jeden vzorek, opakujte příznak - vyloučení.</span><span class="sxs-lookup"><span data-stu-id="e4969-120">To specify more than one pattern, repeat the -Exclude flag.</span></span> <span data-ttu-id="e4969-121">Viz následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e4969-121">See example below.</span></span> |
| <span data-ttu-id="e4969-122">ExcludeEmptyDirectories</span><span class="sxs-lookup"><span data-stu-id="e4969-122">ExcludeEmptyDirectories</span></span> | <span data-ttu-id="e4969-123">Při vytváření balíčku, zabraňuje zahrnutí prázdných adresářů.</span><span class="sxs-lookup"><span data-stu-id="e4969-123">Prevents inclusion of empty directories when building the package.</span></span> |
| <span data-ttu-id="e4969-124">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="e4969-124">ForceEnglishOutput</span></span> | <span data-ttu-id="e4969-125">*(3.5 +)*  Vynutí nuget.exe ke spuštění pomocí invariantní, na základě angličtina jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="e4969-125">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="e4969-126">Nápověda</span><span class="sxs-lookup"><span data-stu-id="e4969-126">Help</span></span> | <span data-ttu-id="e4969-127">Zobrazí nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e4969-127">Displays help information for the command.</span></span> |
| <span data-ttu-id="e4969-128">IncludeReferencedProjects</span><span class="sxs-lookup"><span data-stu-id="e4969-128">IncludeReferencedProjects</span></span> | <span data-ttu-id="e4969-129">Označuje, že balíček integrovaný by měla zahrnovat odkazované projekty jako závislosti nebo jako součást balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-129">Indicates that the built package should include referenced projects either as dependencies or as part of the package.</span></span> <span data-ttu-id="e4969-130">Pokud odkazované projekt má odpovídající `.nuspec` soubor, který má stejný název jako projekt, pak tento odkazovaný projektu se přidal jako závislost.</span><span class="sxs-lookup"><span data-stu-id="e4969-130">If a referenced project has a corresponding `.nuspec` file that has the same name as the project, then that referenced project is added as a dependency.</span></span> <span data-ttu-id="e4969-131">Odkazovaný projekt, jinak se přidá jako součást balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-131">Otherwise, the referenced project is added as part of the package.</span></span> |
| <span data-ttu-id="e4969-132">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="e4969-132">MinClientVersion</span></span> | <span data-ttu-id="e4969-133">Nastavte *minClientVersion* atribut pro vytvoření balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-133">Set the *minClientVersion* attribute for the created package.</span></span> <span data-ttu-id="e4969-134">Tato hodnota se přepíše stávající hodnotu *minClientVersion* atribut (pokud existuje) `.nuspec` souboru.</span><span class="sxs-lookup"><span data-stu-id="e4969-134">This value will override the value of the existing *minClientVersion* attribute (if any) in the `.nuspec` file.</span></span> |
| <span data-ttu-id="e4969-135">MSBuildPath</span><span class="sxs-lookup"><span data-stu-id="e4969-135">MSBuildPath</span></span> | <span data-ttu-id="e4969-136">*(4.0 +)*  Určuje cestu MSBuild používat pomocí příkazu, přednost před `-MSBuildVersion`.</span><span class="sxs-lookup"><span data-stu-id="e4969-136">*(4.0+)* Specifies the path of MSBuild to use with the command, taking precedence over `-MSBuildVersion`.</span></span> |
| <span data-ttu-id="e4969-137">MSBuildVersion</span><span class="sxs-lookup"><span data-stu-id="e4969-137">MSBuildVersion</span></span> | <span data-ttu-id="e4969-138">*(3.2 +)*  Určuje verzi nástroje MSBuild k použití se tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="e4969-138">*(3.2+)* Specifies the version of MSBuild to be used with this command.</span></span> <span data-ttu-id="e4969-139">Podporované hodnoty jsou 4, 12, 14, 15.</span><span class="sxs-lookup"><span data-stu-id="e4969-139">Supported values are 4, 12, 14, 15.</span></span> <span data-ttu-id="e4969-140">Ve výchozím nastavení je zachyceny MSBuild ve své cestě jinak bude výchozí nejvyšší nainstalovanou verzi nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e4969-140">By default the MSBuild in your path is picked, otherwise it defaults to the highest installed version of MSBuild.</span></span> |
| <span data-ttu-id="e4969-141">NoDefaultExcludes</span><span class="sxs-lookup"><span data-stu-id="e4969-141">NoDefaultExcludes</span></span> | <span data-ttu-id="e4969-142">Zabraňuje výchozí vyloučení NuGet balíček soubory a soubory a složky začínající tečkou, jako například `.svn` a `.gitignore`.</span><span class="sxs-lookup"><span data-stu-id="e4969-142">Prevents default exclusion of NuGet package files and files and folders starting with a dot, such as `.svn` and `.gitignore`.</span></span> |
| <span data-ttu-id="e4969-143">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="e4969-143">NoPackageAnalysis</span></span> | <span data-ttu-id="e4969-144">Určuje, že sada by neměl spustit analysis balíčku po vytvoření balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-144">Specifies that pack should not run package analysis after building the package.</span></span> |
| <span data-ttu-id="e4969-145">Výstupnísložka</span><span class="sxs-lookup"><span data-stu-id="e4969-145">OutputDirectory</span></span> | <span data-ttu-id="e4969-146">Určuje složku, ve kterém je uložen balíček vytvořený.</span><span class="sxs-lookup"><span data-stu-id="e4969-146">Specifies the folder in which the created package is stored.</span></span> <span data-ttu-id="e4969-147">Pokud není zadaný žádný složky, se používá aktuální složky.</span><span class="sxs-lookup"><span data-stu-id="e4969-147">If no folder is specified, the current folder is used.</span></span> |
| <span data-ttu-id="e4969-148">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e4969-148">Properties</span></span> | <span data-ttu-id="e4969-149">By se zobrazit poslední na příkazovém řádku po další možnosti.</span><span class="sxs-lookup"><span data-stu-id="e4969-149">Should appear last on the command line after other options.</span></span> <span data-ttu-id="e4969-150">Určuje seznam vlastností, které potlačí hodnoty v souboru projektu; v tématu [běžné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties) pro názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="e4969-150">Specifies a list of properties that override values in the project file; see [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties) for property names.</span></span> <span data-ttu-id="e4969-151">Argument vlastnosti tady je seznam token = hodnota páry, oddělené středníky, kde každý výskyt `$token$` v `.nuspec` souboru se nahradí s danou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e4969-151">The Properties argument here is a list of token=value pairs, separated by semicolons, where each occurrence of `$token$` in the `.nuspec` file will be replaced with the given value.</span></span> <span data-ttu-id="e4969-152">Hodnoty mohou být řetězce v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="e4969-152">Values can be strings in quotation marks.</span></span> <span data-ttu-id="e4969-153">Všimněte si, že pro vlastnost "Konfigurace" Výchozí hodnota je "Debug".</span><span class="sxs-lookup"><span data-stu-id="e4969-153">Note that for the "Configuration" property, the default is "Debug".</span></span> <span data-ttu-id="e4969-154">Můžete změnit konfiguraci verze `-Properties Configuration=Release`.</span><span class="sxs-lookup"><span data-stu-id="e4969-154">To change to a Release configuration, use `-Properties Configuration=Release`.</span></span> |
| <span data-ttu-id="e4969-155">Přípona</span><span class="sxs-lookup"><span data-stu-id="e4969-155">Suffix</span></span> | <span data-ttu-id="e4969-156">*(3.4.4+)*  Připojí příponu k číslo verze generované interně, obvykle se používá pro připojování sestavení nebo dalších identifikátorů předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="e4969-156">*(3.4.4+)* Appends a suffix to the internally generated version number, typically used for appending build or other pre-release identifiers.</span></span> <span data-ttu-id="e4969-157">Například pomocí `-suffix nightly` vytvoří balíček s jako číslo verze `1.2.3-nightly`.</span><span class="sxs-lookup"><span data-stu-id="e4969-157">For example, using `-suffix nightly` will create a package with a version number like `1.2.3-nightly`.</span></span> <span data-ttu-id="e4969-158">Přípony musí začínat písmenem, aby se zabránilo upozornění, chyby a potenciální nekompatibilitu s různými verzemi nástroje NuGet a Správce balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="e4969-158">Suffixes must start with a letter to avoid warnings, errors, and potential incompatibilities with different versions of NuGet and the NuGet Package Manager.</span></span> |
| <span data-ttu-id="e4969-159">Symboly</span><span class="sxs-lookup"><span data-stu-id="e4969-159">Symbols</span></span> | <span data-ttu-id="e4969-160">Určuje, zda balíček obsahuje zdroje a symboly.</span><span class="sxs-lookup"><span data-stu-id="e4969-160">Specifies that the package contains sources and symbols.</span></span> <span data-ttu-id="e4969-161">Při použití s `.nuspec` souboru, tím se vytvoří soubor regulární balíčku NuGet a odpovídající balíčku symbolů.</span><span class="sxs-lookup"><span data-stu-id="e4969-161">When used with a `.nuspec` file, this creates a regular NuGet package file and the corresponding symbols package.</span></span> |
| <span data-ttu-id="e4969-162">Nástroj</span><span class="sxs-lookup"><span data-stu-id="e4969-162">Tool</span></span> | <span data-ttu-id="e4969-163">Určuje, že výstupních souborů projektu mají být umístěny v `tool` složky.</span><span class="sxs-lookup"><span data-stu-id="e4969-163">Specifies that the output files of the project should be placed in the `tool` folder.</span></span> |
| <span data-ttu-id="e4969-164">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e4969-164">Verbosity</span></span> | <span data-ttu-id="e4969-165">Určuje množství podrobností, které jsou zobrazené ve výstupu: *normální*, *quiet*, *podrobné*.</span><span class="sxs-lookup"><span data-stu-id="e4969-165">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |
| <span data-ttu-id="e4969-166">Version</span><span class="sxs-lookup"><span data-stu-id="e4969-166">Version</span></span> | <span data-ttu-id="e4969-167">Přepsání číslo verze z `.nuspec` souboru.</span><span class="sxs-lookup"><span data-stu-id="e4969-167">Overrides the version number from the `.nuspec` file.</span></span> |

<span data-ttu-id="e4969-168">Viz také [proměnné prostředí](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="e4969-168">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="excluding-development-dependencies"></a><span data-ttu-id="e4969-169">S výjimkou vývoj závislosti</span><span class="sxs-lookup"><span data-stu-id="e4969-169">Excluding development dependencies</span></span>

<span data-ttu-id="e4969-170">Některé balíčky NuGet jsou užitečné jako vývoj závislosti, které umožňují vytvářet vlastní knihovny, ale nejsou nezbytně potřebné jako závislosti skutečné balíčků.</span><span class="sxs-lookup"><span data-stu-id="e4969-170">Some NuGet packages are useful as development dependencies, which help you author your own library, but aren't necessarily needed as actual package dependencies.</span></span>

<span data-ttu-id="e4969-171">`pack` Příkaz bude ignorovat `package` položek v `packages.config` mají `developmentDependency` atribut nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="e4969-171">The `pack` command will ignore `package` entries in `packages.config` that have the `developmentDependency` attribute set to `true`.</span></span> <span data-ttu-id="e4969-172">Tyto položky nebudou obsahovat jako závislosti v vytvořený balíčku.</span><span class="sxs-lookup"><span data-stu-id="e4969-172">These entries will not be include as a dependencies in the created package.</span></span>

<span data-ttu-id="e4969-173">Například vezměte v úvahu následující `packages.config` v projektu zdroje:</span><span class="sxs-lookup"><span data-stu-id="e4969-173">For example, consider the following `packages.config` file in the source project:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="jQuery" version="1.5.2" />
    <package id="netfx-Guard" version="1.3.3.2" developmentDependency="true" />
    <package id="microsoft-web-helpers" version="1.15" />
</packages>
```

<span data-ttu-id="e4969-174">Pro tento projekt balíček vytvořený `nuget pack` bude mít závislost na `jQuery` a `microsoft-web-helpers` ale ne `netfx-Guard`.</span><span class="sxs-lookup"><span data-stu-id="e4969-174">For this project, the package created by `nuget pack` will have a dependency on `jQuery` and `microsoft-web-helpers` but not `netfx-Guard`.</span></span>

## <a name="examples"></a><span data-ttu-id="e4969-175">Příklady</span><span class="sxs-lookup"><span data-stu-id="e4969-175">Examples</span></span>

```cli
nuget pack

nuget pack foo.nuspec

nuget pack foo.csproj

nuget pack foo.csproj -Properties Configuration=Release

nuget pack foo.csproj -Build -Symbols -Properties owners=janedoe,xiaop;version="1.0.5"

# Create a package from project foo.csproj, using MSBuild version 12 to build the project
nuget pack foo.csproj -Build -Symbols -MSBuildVersion 12 -Properties owners=janedoe,xiaop;version="1.0.5

nuget pack foo.nuspec -Version 2.1.0

nuget pack foo.nuspec -Version 1.0.0 -MinClientVersion 2.5

nuget pack Package.nuspec -exclude "*.exe" -exclude "*.bat"
```