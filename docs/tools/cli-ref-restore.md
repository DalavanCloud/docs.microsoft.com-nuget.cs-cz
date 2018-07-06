---
title: Příkaz Obnovit NuGet rozhraní příkazového řádku
description: Referenční dokumentace pro příkaz restore nuget.exe
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 4df7685883fea78428c6744bdbf4c66d83e469bc
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34817915"
---
# <a name="restore-command-nuget-cli"></a>příkaz Restore (NuGet CLI)

**Platí pro:** balíček spotřeba &bullet; **podporované verze:** 2.7 +

Stáhne a nainstaluje všechny balíčky chybí `packages` složky. Při použití s NuGet 4.0 + a formát PackageReference, generuje `<project>.nuget.props` v případě potřeby v souboru `obj` složky. (Soubor lze vynechat od správy zdrojového kódu.)

Na Mac OSX a Linux pomocí rozhraní příkazového řádku na Mono Probíhá obnovení balíčků nepodporuje PackageReference.

## <a name="usage"></a>Použití

```cli
nuget restore <projectPath> [options]
```

kde `<projectPath>` Určuje umístění řešení nebo `packages.config` souboru. V tématu [poznámky](#remarks) níže chování podrobnosti.

## <a name="options"></a>Možnosti

| Možnost | Popis |
| --- | --- |
| ConfigFile | Konfigurační soubor NuGet použít. Pokud není zadaný, `%AppData%\NuGet\NuGet.Config` (Windows) nebo `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) se používá.|
| DirectDownload | *(4.0 +)*  Balíčky stahuje přímo bez naplnění mezipaměti se binární soubory nebo metadata. |
| DisableParallelProcessing | Zakáže obnovení více balíčky současně. |
| FallbackSource | *(3.2 +)*  Seznam zdroje balíčku pro použití jako případech přejít v případě, že daný balíček nebyl nalezen v primární nebo výchozí zdroj. |
| ForceEnglishOutput | *(3.5 +)*  Vynutí nuget.exe ke spuštění pomocí invariantní, na základě angličtina jazykové verze. |
| Nápověda | Zobrazí nápovědu pro příkaz. |
| MSBuildPath | *(4.0 +)*  Určuje cestu MSBuild používat pomocí příkazu, přednost před `-MSBuildVersion`. |
| MSBuildVersion | *(3.2 +)*  Určuje verzi nástroje MSBuild k použití se tento příkaz. Podporované hodnoty jsou 4, 12, 14, 15. Ve výchozím nastavení je zachyceny MSBuild ve své cestě jinak bude výchozí nejvyšší nainstalovanou verzi nástroje MSBuild. |
| NoCache | NuGet bránit v použití balíčky v mezipaměti. V tématu [správy globální balíčky a složky mezipaměti](../consume-packages/managing-the-global-packages-and-cache-folders.md). |
| Neinteraktivní | Potlačí výzvy pro vstup uživatele nebo potvrzení. |
| Výstupnísložka | Určuje složku, ve kterém jsou nainstalované balíčky. Pokud není zadaný žádný složky, se používá aktuální složky. Při obnovení s vyžaduje `packages.config` souboru Pokud `PackagesDirectory` nebo `SolutionDirectory` se používá.|
| PackageSaveMode | Určuje typy souborů, uložte po instalaci balíčku: jeden z `nuspec`, `nupkg`, nebo `nuspec;nupkg`. |
| PackagesDirectory | Stejné jako `OutputDirectory`. Při obnovení s vyžaduje `packages.config` souboru Pokud `OutputDirectory` nebo `SolutionDirectory` se používá. |
| Project2ProjectTimeOut | Časový limit v sekundách pro odkazy na projekt na projekt řešení. |
| Rekurzivní | *(4.0 +)*  Obnoví všechny odkazy na projekty pro projekty UWP a .NET Core. Nelze použít u projektů pomocí `packages.config`. |
| RequireConsent | Ověří, že probíhá obnovení balíčků je zapnutá před stažením a instalací balíčky. Podrobnosti najdete v tématu [obnovení balíčků](../consume-packages/package-restore.md). |
| SolutionDirectory | Určuje složku řešení. Není platný při obnovení balíčků pro řešení. Při obnovení s vyžaduje `packages.config` souboru Pokud `PackagesDirectory` nebo `OutputDirectory` se používá. |
| Zdroj | Určuje seznam zdrojů balíčku (jako adresy URL) pro obnovení. Pokud tento parametr vynechán, příkaz používá zdrojů, součástí konfigurační soubory, najdete v části [konfigurace NuGet chování](../consume-packages/configuring-nuget-behavior.md). |
| Podrobnosti |> určuje množství podrobností, které jsou zobrazené ve výstupu: *normální*, *quiet*, *podrobné*. |

Viz také [proměnné prostředí](cli-ref-environment-variables.md)

## <a name="remarks"></a>Poznámky

Příkaz restore provede následující kroky:

1. Určení režimu operace příkazu restore.

   | Typ souboru projectPath | Chování |
   | --- | --- |
   | Řešení (složka) | Hledá NuGet `.sln` souborů a použije je-li nalezen; jinak vrátí chybu. `(SolutionDir)\.nuget` slouží jako výchozí složku. |
   | `.sln` Soubor | Obnovení balíčků se identifikovanou pomocí řešení; Vrátí chybu, pokud `-SolutionDirectory` se používá. `$(SolutionDir)\.nuget` slouží jako výchozí složku. |
   | `packages.config` nebo soubor projektu | Obnovte balíčky uvedené v souboru, řešení a instalování závislostí. |
   | Další typ souboru | Soubor se předpokládá, že se `.sln` souboru jak je uvedeno výše; Pokud není řešením, nabízí NuGet se chyba. |
   | (není zadaný projectPath) | <ul><li>NuGet vyhledá soubory řešení v aktuální složce. Pokud je nalezen jeden soubor, než se používá k obnovení balíčků; Pokud je nalezeno více řešení, NuGet obsahuje chybu.</li><li>Pokud nejsou žádné soubory řešení, hledá NuGet `packages.config` a použije ho k obnovení balíčků.</li><li>Pokud žádné řešení nebo `packages.config` je nalezeno, vrátí chybu NuGet.</ul> |

2. Můžete určete složky balíčků v následujícím pořadí priority (NuGet vrátí chybu, pokud se nenajdou žádné z těchto složek):

    - Zadaná složka s `-PackagesDirectory`.
    - `repositoryPath` Vale v `Nuget.Config`
    - Zadaná složka s `-SolutionDirectory`
    - `$(SolutionDir)\packages`

3. Při obnovování balíčků pro řešení, NuGet provede následující akce:
    - Načte soubor řešení.
    - Obnoví řešení úrovně balíčky uvedené v `$(SolutionDir)\.nuget\packages.config` do `packages` složky.
    - Obnovení balíčků, které jsou uvedené v `$(ProjectDir)\packages.config` do `packages` složky. Pro každý balíček určený obnovení balíčku paralelně, pokud `-DisableParallelProcessing` je zadán.

## <a name="examples"></a>Příklady

```cli
# Restore packages for a solution file
nuget restore a.sln

# Restore packages for a solution file, using MSBuild version 14.0 to load the solution and its project(s)
nuget restore a.sln -MSBuildVersion 14

# Restore packages for a project's packages.config file, with the packages folder at the parent
nuget restore proj1\packages.config -PackagesDirectory ..\packages

# Restore packages for the solution in the current folder, specifying package sources
nuget restore -source "https://api.nuget.org/v3/index.json;https://www.myget.org/F/nuget"
```