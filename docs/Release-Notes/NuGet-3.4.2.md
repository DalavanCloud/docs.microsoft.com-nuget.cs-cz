---
title: "Poznámky k verzi NuGet 3.4.2 | Microsoft Docs"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: b514da09-da1f-416b-9bfc-692f08fb6957
description: "Poznámky k verzi pro NuGet 3.4.2 včetně – známé problémy, opravy chyb, přidaných funkcí a chcete."
keywords: "NuGet 3.4.2 poznámky k verzi, opravy chyb známé problémy, přidat funkce, chcete"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 6761c59b6dc85b9a8503041928c2707549006d9c
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-342-release-notes"></a>Poznámky k verzi NuGet 3.4.2

[Poznámky k verzi NuGet 3.4.1](../release-notes/nuget-3.4.1.md) | [NuGet 3.4.3 poznámky k verzi](../release-notes/nuget-3.4.3.md)

NuGet 3.4.2 byla vydána 8. dubna 2016 několik problémů, které byly identifikovány 3.4 a 3.4.1 verzi.

## <a name="nugetexe-342-rc-is-now-available"></a>nuget.exe 3.4.2 RC je nyní k dispozici

Si můžete stáhnout na verzi release candidate z nuget.exe 3.4.2 [zde](https://dist.nuget.org/index.html).

## <a name="updates-and-improvements"></a>Aktualizace a vylepšení

* Významně jsme vylepšili výkon aktualizace v konkrétní scénář, kde aktualizace na balíčky s grafy hloubkové závislostí trvalo skutečně dlouhou dobu a přestala Visual Studio.
* nuget restore bez síťový provoz je 2,5 x – 3 x rychlejší v sadě Visual Studio.
* Kromě tuto změnu vyřešili jsme problém kde jsme byly dvakrát při načítání aktualizace počet v uživatelském rozhraní VS stiskne sítě. To je částečně zodpovědná za někteří zákazníci problémy časový limit zkušenosti s 3.4 nebo 3.4.1.
* Přidaná podpora pro no_proxy nastavení

##<a name="fixes"></a>Opravy

* Kde nuget.org zdroje nebyl nalezen v NuGet nastavení nebo konfigurace po aktualizaci 3.4.1 opraven problém.
* Kde se malá a velká písmena změnu FindPackagesById v 3.4.1 dělí Artifactory opraven problém.
* Opraven problém se standardem FIPS, která způsobila selhání s obnovením NuGet s nuget.exe.
* Pevné havárie, při procházení zdroje s adresou URL ikona neplatné.
* Opravené problémy s slučování verze a záznamy z 'Všechny zdroje'.

## <a name="known-issues-in-342-windows-x86-commandline-rc"></a>Známé problémy v 3.4.2 příkazového řádku Windows x86 (RC)

Tyto problémy budou opraveny časná příští týden před jsme dosáhl RTM.

*  Spuštěné nuget obnovení řešení se nezdaří, pokud soubor řešení je umístěn v hierarchii složek nižší než soubory projektu.
*  Příkaz delete nuget systémem balíčku pomocí informačního kanálu V2 se nezdaří. Místo toho použijte V3 informačního kanálu.


Úplný seznam oprav a vylepšení v této verzi najdete seznam problémů [zde](https://github.com/NuGet/Home/issues?utf8=%E2%9C%93&q=is%3Aissue+milestone%3A3.4.2++is%3Aclosed+).