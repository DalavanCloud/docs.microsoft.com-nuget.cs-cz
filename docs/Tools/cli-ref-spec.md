---
title: "Specifikace příkaz NuGet rozhraní příkazového řádku | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 85611449-87e6-489b-8c6c-fe1d7be76c13
description: "Referenční dokumentace pro příkaz specifikace nuget.exe"
keywords: "Specifikace odkaz nuget, specifikace příkaz"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c32b23e66c8eb4db1c8fa6dc615589219c00239f
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="spec-command-nuget-cli"></a>Specifikace příkazu (NuGet CLI)

**Platí pro:** balíček vytvoření &bullet; **podporované verze:** všechny

Generuje `.nuspec` soubor pro nový balíček. Pokud ve stejné složce jako soubor projektu (`.csproj`, `.vbproj`, `.fsproj`), `spec` vytvoří tokenizovaná `.nuspec` souboru. Další informace najdete v tématu [vytváření balíčku](../create-packages/creating-a-package.md).

## <a name="usage"></a>Použití

```
nuget spec [<packageID>] [options]
```

kde `<packageID>` je identifikátor volitelné balíček uložit v `.nuspec` souboru.

## <a name="options"></a>Možnosti

| Možnost | Popis |
| --- | --- |
| AssemblyPath | Určuje cestu k sestavení, které má používat pro metadata. |
| Platnost | Přepíše všechny existující `.nuspec` souboru. |
| ForceEnglishOutput | *(3.5 +)*  Vynutí nuget.exe ke spuštění pomocí invariantní, na základě angličtina jazykové verze. |
| Nápověda | Zobrazí nápovědu pro příkaz. |
| Neinteraktivní | Potlačí výzvy pro vstup uživatele nebo potvrzení. |
| Podrobnosti | Určuje množství podrobností, které jsou zobrazené ve výstupu: *normální*, *quiet*, *podrobné (2.5 +)*. |

Viz také [proměnné prostředí](cli-ref-environment-variables.md)

## <a name="examples"></a>Příklady

```
nuget spec

nuget spec MyPackage

nuget spec -a MyAssembly.dll
```