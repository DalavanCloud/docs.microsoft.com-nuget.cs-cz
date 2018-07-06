---
title: Přehled a pracovní postup pomocí balíčků NuGet
description: Přehled procesu využívání balíčků NuGet v projektu, s odkazy na další konkrétní části procesu.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 03/22/2018
ms.topic: conceptual
ms.openlocfilehash: 1c909a38fc48a7da7dd3bad25f34e0837d8b37bd
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34818605"
---
# <a name="package-consumption-workflow"></a>Pracovní postup spotřeba balíčku

Mezi nuget.org a privátní balíček galerie, které vaše organizace může vytvořit můžete najít desetitisíce velmi užitečné balíčků pro použití v aplikace a služby. Ale bez ohledu na zdroje, využívání balíček následuje stejné obecný postup.

![Tok přejdete ke zdroji balíčku, hledání balíček, nainstalujte ho v projektu a pak přidání pomocí příkazu a volání rozhraní API balíčku](media/Overview-01-GeneralFlow.png)

\* _Visual Studio a dotnet.ex' pouze. Příkaz instalace nuget neupravuje soubory projektu a packages.config; položky musí být spravovaný ručně._

Další podrobnosti najdete v tématu [vyhledání a výběr balíčky](../consume-packages/finding-and-choosing-packages.md) a [různé způsoby, jak nainstalovat balíček NuGet](ways-to-install-a-package.md).

NuGet pamatuje číslo identity a verze jednotlivých balíčků nainstalovaných záznam buď [ `packages.config` ](../reference/packages-config.md) nebo soubor projektu (pomocí [PackageReference](../consume-packages/package-references-in-project-files.md)), v závislosti na typu projektu a verze balíčku NuGet. U balíčku NuGet 4.0 +, je preferovaná, PackageReference, i když to lze nakonfigurovat v sadě Visual Studio prostřednictvím [možnosti uživatelského rozhraní Správce balíčků](../tools/package-manager-ui.md). V každém případě můžete prohlédnout v příslušné souboru vždy, když chcete zobrazit úplný seznam závislosti pro váš projekt.

> [!Tip]
> Je vhodné si vždycky prohlédněte licenci pro každý balíček, který chcete používat váš software. Na nuget.org, Najít **licenční informace** odkaz na pravé straně stránky popis každého balíčku. Pokud balíček neurčuje licenční podmínky, obraťte se na vlastníka balíčku přímo pomocí **obraťte se na vlastníky** odkaz na stránce balíček. Společnost Microsoft není licence duševního vlastnictví vám ze zprostředkovatelů balíček třetích stran a není zodpovědná za informace třetích stran.

Při instalaci balíčků, NuGet obvykle zkontroluje, zda balíček je již k dispozici, ze své mezipaměti. Tato mezipaměť z příkazového řádku, můžete ručně vymazat, jak je popsáno na [správy globální balíčky a složky mezipaměti](../consume-packages/managing-the-global-packages-and-cache-folders.md).

NuGet také zajišťuje, že jsou kompatibilní s projektu cílové rozhraní nepodporuje balíček. Pokud balíček neobsahuje kompatibilní sestavení, zobrazí se NuGet k chybě. V tématu [řešení chyb při nekompatibilní balíček](dependency-resolution.md#resolving-incompatible-package-errors).

Při přidávání kód projektu do zdrojové úložiště, obvykle nejsou zahrnuty balíčky NuGet. Uživatelům, kteří později klonovat úložiště nebo jinak získat projektu, včetně agenty sestavení v systémech například Visual Studio Team Services, musíte obnovit nezbytných balíčků před spuštěním sestavení:

![Tok klonování úložiště a pomocí příkazu restore Probíhá obnovení balíčků NuGet](media/Overview-02-RestoreFlow.png)

[Obnovení balíčků](../consume-packages/package-restore.md) používá informace v souboru projektu nebo `packages.config` znovu nainstalovat všechny závislosti. Všimněte si, že jsou rozdíly v procesu související se situací, jak je popsáno v [řešení závislostí](../consume-packages/dependency-resolution.md). Navíc diagramu výše nezobrazuje příkazu restore pro konzolu Správce balíčků proto, že jste s konzolou jste již v kontextu sady Visual Studio, která obvykle automaticky obnoví balíčky a obsahuje příkaz úrovni řešení, jak je vidět .

Někdy je nutné znovu nainstalovat balíčky, které jsou již zahrnuty v projektu, který může přeinstalovat také závislosti. Toto je snadné provést pomocí `nuget reinstall` příkaz nebo konzole Správce balíčků NuGet. Podrobnosti najdete v tématu [Reinstalling a balíčky, aktualizace](../consume-packages/reinstalling-and-updating-packages.md).

Nakonec se řídí chování NuGet `Nuget.Config` soubory. Více souborů umožňují centralizovat určitých nastavení na různých úrovních, jak je popsáno v [konfigurace chování NuGet](../consume-packages/configuring-nuget-behavior.md).

Užijte si ji produktivní kódování se balíčky NuGet!