---
title: Příkaz rozhraní příkazového řádku NuGet restore
description: Referenční informace pro příkaz restore nuget.exe
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 06e3a26863761b7e7a42752866e7fe369f5be4ef
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43550349"
---
# <a name="restore-command-nuget-cli"></a>příkaz Restore (rozhraní příkazového řádku NuGet)

**Platí pro:** balíček spotřeby &bullet; **podporované verze:** 2.7 +

Stáhne a nainstaluje všechny balíčky, které chybí `packages` složky. Při použití s PackageReference formátu a NuGet 4.0 +, generuje `<project>.nuget.props` v případě potřeby v souboru `obj` složky. (Tento soubor můžete vynechat ze správy zdrojového kódu.)

Na Mac OSX a Linux s využitím rozhraní příkazového řádku v Mono obnovování balíčků se nepodporuje PackageReference.

## <a name="usage"></a>Použití

```cli
nuget restore <projectPath> [options]
```

kde `<projectPath>` Určuje umístění řešení nebo `packages.config` souboru. Zobrazit [poznámky](#remarks) níže chování podrobnosti.

## <a name="options"></a>Možnosti

| Možnost | Popis |
| --- | --- |
| ConfigFile | Konfigurační soubor NuGet použít. Pokud není zadán, `%AppData%\NuGet\NuGet.Config` (Windows) nebo `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) se používá.|
| DirectDownload | *(4.0 +)*  Stáhne balíčky přímo bez naplnění mezipaměti se binární soubory nebo metadata. |
| DisableParallelProcessing | Zakáže obnovování více balíčků paralelně. |
| FallbackSource | *(3.2 +)*  Seznam zdrojů balíčků, které má být použit jako náhrad balíček nebyl nalezen v primární nebo výchozí zdroj. |
| ForceEnglishOutput | *(3.5 +)*  Vynutí nuget.exe pro spuštění pomocí neutrální, základem je angličtina jazyková verze. |
| Nápověda | Zobrazí nápovědu pro příkaz. |
| MSBuildPath | *(4.0 +)*  Určuje cestu k používání pomocí příkazu, přednost `-MSBuildVersion`. |
| MSBuildVersion | *(3.2 +)*  Určuje verzi Msbuildu, který se má použít tento příkaz. Podporované hodnoty jsou 4, 12, 14, 15. Ve výchozím nastavení se vybere MSBuild na vaší cestě jinak je výchozí hodnotou nejvyšší nainstalovaná verze Msbuildu. |
| NoCache | Brání použití mezipaměti balíčků NuGet. Zobrazit [Správa globálních balíčků a složek mezipaměti](../consume-packages/managing-the-global-packages-and-cache-folders.md). |
| Neinteraktivní | Potlačí vyzve k zadání uživatele o vstup ani potvrzení. |
| OutputDirectory | Určuje složku, ve kterém jsou nainstalované balíčky. Pokud není zadána žádná složka, použije se aktuální složce. Při obnovení se vyžaduje `packages.config` souboru není-li `PackagesDirectory` nebo `SolutionDirectory` se používá.|
| PackageSaveMode | Určuje typy souborů, uložte po instalaci balíčku: jeden z `nuspec`, `nupkg`, nebo `nuspec;nupkg`. |
| PackagesDirectory | Stejné jako `OutputDirectory`. Při obnovení se vyžaduje `packages.config` souboru není-li `OutputDirectory` nebo `SolutionDirectory` se používá. |
| Project2ProjectTimeOut | Časový limit v sekundách pro odkazy typu projekt projekt řešení. |
| rekurzivní | *(4.0 +)*  Obnoví všechny odkazy na projekty pro projekty UPW a .NET Core. Se nedá použít u projektů s použitím `packages.config`. |
| RequireConsent | Ověří, zda je povoleno obnovují se balíčky před stažením a instalací balíčků. Podrobnosti najdete v tématu [obnovení balíčků](../consume-packages/package-restore.md). |
| SolutionDirectory | Určuje složku řešení. Není platný při obnovují se balíčky pro řešení. Při obnovení se vyžaduje `packages.config` souboru není-li `PackagesDirectory` nebo `OutputDirectory` se používá. |
| Zdroj | Určuje seznam zdrojů balíčků (jako adresy URL) pro obnovení. Pokud tento parametr vynechán, příkaz používá zdroje k dispozici v konfiguračních souborech naleznete v tématu [konfigurace NuGet chování](../consume-packages/configuring-nuget-behavior.md). |
| Podrobnosti |> určuje množství podrobností, na které se zobrazí ve výstupu: *normální*, *quiet*, *podrobné*. |

Viz také [proměnné prostředí](cli-ref-environment-variables.md)

## <a name="remarks"></a>Poznámky

Příkaz restore provede následující kroky:

1. Určete režim operace příkazu restore.

   | Typ souboru projectPath | Chování |
   | --- | --- |
   | Řešení (složka) | Vyhledá NuGet `.sln` Souborová služba a používá, je-li nalezena; v opačném případě vrátí chybu. `(SolutionDir)\.nuget` slouží jako počáteční složky. |
   | `.sln` Soubor | Obnovit balíčky uvedené řešení; Vrátí chybu, pokud `-SolutionDirectory` se používá. `$(SolutionDir)\.nuget` slouží jako počáteční složky. |
   | `packages.config` nebo soubor projektu | Obnovte balíčky uvedené v souboru, řešení a instalování závislostí. |
   | Jiný typ souboru | Soubor je považován za `.sln` souboru jako výše; Pokud není řešením, nabízí NuGet chybu. |
   | (projectPath nezadané) | <ul><li>NuGet hledá soubory řešení v aktuální složce. Pokud je nalezen jeden soubor, používá se pro obnovování balíčků; Pokud se najde více řešení, NuGet vrátí chybu.</li><li>Pokud nejsou žádné soubory řešení, hledá NuGet `packages.config` a použije ho k obnovení balíčků.</li><li>Pokud žádná řešení nebo `packages.config` soubor se nachází, NuGet vrátí chybu.</ul> |

2. Určení složky balíčků v následujícím pořadí priority (NuGet vrátí chybu, pokud se nenajdou žádné z těchto složek):

    - Zadaná složka s `-PackagesDirectory`.
    - `repositoryPath` Hodnotu v `Nuget.Config`
    - Zadaná složka s `-SolutionDirectory`
    - `$(SolutionDir)\packages`

3. Při obnovování balíčků pro řešení, NuGet provede následující akce:
    - Načte soubor řešení.
    - Obnoví balíčky na úrovni řešení uvedené v `$(SolutionDir)\.nuget\packages.config` do `packages` složky.
    - Obnovit balíčky uvedené v `$(ProjectDir)\packages.config` do `packages` složky. Pro každý balíček určený, obnovení balíčku paralelně, pokud `-DisableParallelProcessing` je zadán.

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
