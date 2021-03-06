---
title: Vytváření balíčků NuGet nativní
description: Podrobnosti o vytvoření nativní balíčky NuGet, které obsahují kód jazyka C++ místo spravovaného kódu pro použití v projektech C++.
author: karann-msft
ms.author: karann
ms.date: 01/09/2017
ms.topic: conceptual
ms.openlocfilehash: f054a1cae7328d3e910d11ac1bfc5f98505e5879
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43546530"
---
# <a name="creating-native-packages"></a>Vytvoření nativní balíčky

Nativní balíček obsahuje nativní kód C++ místo spravovaného kódu, díky kterému jej použít v rámci projektů v jazyce C++. (Viz [nativní balíčky C++](../consume-packages/finding-and-choosing-packages.md#native-c-packages) v části využívání.)

Chcete-li být použitelné v projektu jazyka C++, musí cílit na balíček `native` rozhraní framework. V současné době není všechna čísla verze přidružené k tento systém jako NuGet zpracovává všechny projekty C++ stejné.

> [!Note]
> Nezapomeňte zahrnout *nativní* v `<tags>` část vaší `.nuspec` , což vývojářům umožňuje další najít váš balíček tak, že tuto značku.

Nativní balíčky NuGet, které cílí na `native` pak můžou soubory v `\build`, `\content`, a `\tools` složky. `\lib` se nepoužívá v tomto případě (NuGet nelze přímo přidat odkazy na projekt jazyka C++). Balíček může zahrnovat také cíle a soubory vlastností v `\build` , bude automaticky importovat do projektech, které využívají balíček NuGet. Tyto soubory musí být pojmenován stejně jako ID balíčku s `.targets` a/nebo `.props` rozšíření. Například [cpprestsdk](https://nuget.org/packages/cpprestsdk/) balíček obsahuje `cpprestsdk.targets` soubor v jeho `\build` složky.

`\build` Složky lze použít pro všechny balíčky NuGet a ne jenom nativní balíčky. `\build` Složky respektuje cílové architektury, stejně jako `\content`, `\lib`, a `\tools` složek. To znamená, že můžete vytvořit `\build\net40` složky a `\build\net45` složky a NuGet se importu příslušné vlastnosti a cíle soubory do projektu. (Pomocí skriptů prostředí PowerShell k importu cíle nástroje MSBuild není potřebná.)
