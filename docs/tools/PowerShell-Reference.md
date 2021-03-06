---
title: Referenční informace prostředí PowerShell NuGet
description: Úplný odkaz na příkazy Powershellu, které jsou k dispozici v konzole Správce balíčků NuGet v sadě Visual Studio.
author: karann-msft
ms.author: karann
ms.date: 10/02/2017
ms.topic: reference
ms.openlocfilehash: 45c8be9956ceaab844bdcd89f1b96adc256f805c
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43546661"
---
# <a name="powershell-reference"></a>Referenční informace prostředí PowerShell

Konzola správce balíčků zajišťuje rozhraní prostředí PowerShell v rámci sady Visual Studio ve Windows pro interakci s NuGet přes konkrétní příkazy uvedené níže. (Konzola není v současné době k dispozici v sadě Visual Studio for Mac) Návod k použití konzole, najdete v článku [Konzola správce balíčků](../tools/package-manager-console.md) tématu.

> [!Tip]
> Všechny příkazy prostředí PowerShell se vztahují pouze na využití balíčků. Žádné příkazy prostředí PowerShell se vztahují k vytváření a publikování balíčků s výjimkou rozsahu, balíčku může být také příjemce další balíčky.

> [!Important]
> Zde uvedené příkazy jsou specifické pro Konzola správce balíčků v sadě Visual Studio a liší [příkazy modulu správy balíčků](/powershell/module/packagemanagement/?view=powershell-6) , které jsou k dispozici v obecné prostředí PowerShell. Konkrétně každé prostředí má příkazy, které nejsou k dispozici v jiném a příkazy se stejným názvem, může se také liší v jejich konkrétním argumenty. Při použití konzole pro správu balíčků v sadě Visual Studio, použijte příkazy a argumenty popsané v tomto tématu k dispozici.

| Běžné příkazy | Popis | Verze NuGet |
| --- | --- | --- |
| [Install-Package](ps-ref-install-package.md) | Nainstaluje do projektu balíček a jeho závislosti. | Všechny |
| [Update-Package](ps-ref-update-package.md) | Aktualizuje balíček a jeho závislosti nebo všechny balíčky v projektu. | Všechny |
| [Find-Package](ps-ref-find-package.md) | Hledat zdroj balíčku pomocí ID balíčku nebo klíčová slova. | 3.0+ |
| [Get-Package](ps-ref-get-package.md) | Načte seznam balíčků nainstalovaných v místním úložišti nebo vypíše dostupné balíčky ze zdroje balíčku. | Všechny |

| Sekundární příkazy | Popis | Verze NuGet |
| --- | --- | --- |
| [Add-BindingRedirect](ps-ref-add-bindingredirect.md) | Ve všech sestaveních ve výstupní cestě projektu zkontroluje a přidá přesměrování vazby do `app.config` nebo `web.config` v případě potřeby. | Všechny |
| [Get-Project](ps-ref-get-project.md) | Zobrazí informace o výchozích nebo zadaný projekt. | 3.0+ |
| [Open-PackagePage](ps-ref-open-packagepage.md) | Spustí výchozí prohlížeč s projektem, licenci nebo adresa URL sestavy zneužití pro zadaný balíček. | Zastaralé v 3.0 |
| [Register-TabExpansion](ps-ref-register-tabexpansion.md) | Zaregistruje rozšíření tab pro parametry příkazu, umožňuje vytvářet vlastní rozšíření pro běžně používané parametr hodnoty. | Všechny |
| [Sync-Package](ps-ref-sync-package.md) | Získat verzi nainstalovaného balíčku z zadaný projekt a synchronizuje na verzi, aby Zbývající projekty v řešení. | 3.0+ |
| [Uninstall-Package](ps-ref-uninstall-package.md) | Odebere balíček z projektu, případně odebrání jeho závislostí. | Všechny |

Kompletní a podrobný nápovědu k jakémukoli z těchto příkazů v rámci konzoly stačí spusťte následující pomocí příkazu názvu:

```ps
Get-Help <command> -full
```

Všechny příkazy konzoly Správce balíčků podporují následující [společné parametry prostředí PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216):

- Ladit
- ErrorAction
- ErrorVariable
- OutBuffer
- OutVariable
- PipelineVariable
- verbose
- WarningAction
- WarningVariable

Podrobnosti najdete v [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216) v dokumentaci k Powershellu.
