---
title: "Referenční dokumentace rozhraní příkazového řádku (CLI) NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: d777c424-0cf3-4bc0-8abd-7ca16c22192b
description: "Reference k příkazovému řádku index pro nuget.exe rozhraní příkazového řádku"
keywords: "Rejstřík referenční dokumentace nuget.exe, rozhraní příkazového řádku nuget.exe, nuget.exe rozhraní příkazového řádku, příkaz nuget"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 3d1c3585d8bbf4c9bd9b50c8167e860594a42055
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-cli-reference"></a>Referenční dokumentace rozhraní příkazového řádku NuGet

NuGet rozhraní příkazového řádku (CLI) `nuget.exe`, poskytuje bude celkový rozsah funkcí NuGet k instalaci, vytvářet, publikovat a spravovat balíčky bez jakýchkoli změn souborů projektu.

Chcete-li používat všechny příkazy, otevřete okno příkazového řádku nebo prostředí bash a potom spusťte `nuget` následovaný příkazu a požadované možnosti, jako například `nuget help pack` (Chcete-li zobrazit nápovědu k příkazu pack).

## <a name="installing-nugetexe"></a>Instalace nuget.exe

[!INCLUDE[install-cli](../includes/install-cli.md)]

## <a name="availability"></a>Dostupnost

- Všechny příkazy jsou k dispozici v systému Windows.
- Všechny příkazy pro práci s [nuget.exe systémem Mono](../guides/install-nuget.md#mac-osx-and-linux) s výjimkou uvedenou pro `pack`, `restore`, a `update`.
- `pack`, `restore`, `delete`, `locals`, A `push` příkazy jsou také k dispozici na Mac a Linux pomocí [dotnet rozhraní příkazového řádku](dotnet-Commands.md). 

## <a name="commands-and-applicability"></a>Příkazy a použitelnosti

Dostupné příkazy a použitelnost k vytvoření balíčku, balíčku spotřebu nebo publikování balíčku na hostitele:

| Běžné příkazy | Platných rolí | Verze NuGet | Popis | 
| --- | --- | --- | --- |
| [pack](cli-ref-pack.md) | Vytvoření | 2.7+ | Vytvoří z balíčku NuGet `.nuspec` nebo soubor projektu. Při spuštění na Mono, vytváření balíčku ze souboru projektu není podporován. |
| [push](cli-ref-push.md) | Publikování | Všechny | Publikuje balíček ke zdroji balíčku. |
| [Konfigurace](cli-ref-config.md) | Všechny | Všechny | Získá nebo nastaví hodnoty konfigurace NuGet. |
| [Nápověda nebo?](cli-ref-help.md) | Všechny | Všechny | Zobrazí nápovědu informace nebo nápovědu pro příkaz. |
| [lokální proměnné](cli-ref-locals.md) | Spotřeba | 3.3+ | Vymaže nebo obsahuje seznam balíčků v různých mezipaměti nebo ve složce globální balíčky nebo identifikuje těchto složek. |
| [obnovení](cli-ref-restore.md) | Spotřeba | 2.7+ | Obnoví všechny balíčky odkazuje formátu odkaz balíčku používán. Při spuštění na Mono, Probíhá obnovení balíčků formátu PackageReference není podporována. | 
| [setapikey](cli-ref-setapikey.md) | Publikování, spotřeba | Všechny | Pokud tento zdroj balíčku vyžaduje klíče pro přístup, uloží klíč rozhraní API pro zdroj daného balíčku. |
| [specifikace](cli-ref-spec.md) | Vytvoření | Všechny | Generuje `.nuspec` souboru pomocí tokenů, je-li generování souboru z projektu sady Visual Studio. |


| Sekundární příkazy | Platných rolí | Verze NuGet | Popis | 
| --- | --- | --- | --- |
| [add](cli-ref-add.md) | Publikování | 3.3+ | Přidá balíček ke zdroji balíčku jiným protokolem než HTTP pomocí hierarchickém rozložení. Pro HTTP zdrojů, použijte *nabízené*. |
| [Odstranit](cli-ref-delete.md) | Publikování | Všechny | Odebere nebo unlists balíčku ze zdroje balíčku. |
| [Init –](cli-ref-init.md) | Vytvoření | 3.3+ | Přidá balíčky ze složky ke zdroji balíčku pomocí hierarchickém rozložení. |
| [instalace](cli-ref-install.md) | Spotřeba | Všechny | Nainstaluje balíček do aktuálního projektu, ale neupravuje projekty ani odkazovat soubory. |
| [seznam](cli-ref-list.md) | Využívání, případně publikování | Všechny | Zobrazí balíčky z daného zdroje. |
| [zrcadlení](cli-ref-mirror.md) | Publikování | Zastaralé v 3.2 + | Odráží balíček a jeho závislé součásti ze zdroje do cílového úložiště. |
| [zdroje](cli-ref-sources.md) | Spotřeba, publikování | Všechny | Spravuje zdroje balíčků v konfiguračních souborech. |
| [aktualizace](cli-ref-update.md) | Spotřeba | Všechny | Projektu balíčky aktualizací na nejnovější verze k dispozici. Není podporováno, když se používá Mono. |

Ujistěte se, jiné příkazy použití různých [proměnné prostředí](cli-ref-environment-variables.md).

Příkazy rozhraní příkazového řádku NuGet příslušné role:

| Role | Příkazy |
| --- | --- |
| Spotřeba | `config`, `help`, `install`, `list`, `locals`, `restore`, `setapikey`, `sources`, `update` | 
| Vytvoření | `config`, `help`, `init`, `pack`, `spec` |
| Publikování | `add`, `config`, `delete`, `help`, `list`, `push`, `setapikey`, `sources` |

Vývojáři pouze nevadí využívání balíčků, například potřebovat pouze pochopit tuto podmnožinu příkazy pro balíčky NuGet.

> [!Note]
> Příkaz možnost názvy jsou velká a malá písmena. Možnosti, které jsou zastaralé nejsou součástí tohoto odkazu, jako například `NoPrompt` (nahrazuje `NonInteractive`) a `Verbose` (nahrazuje `Verbosity`).