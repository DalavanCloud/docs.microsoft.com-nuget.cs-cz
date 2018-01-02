---
title: "Příkaz Přidat NuGet rozhraní příkazového řádku | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 4f68a016-ad4e-41fc-b869-88910fc5121e
description: "Referenční dokumentace pro nuget.exe přidat – příkaz"
keywords: "Přidat odkaz nuget, přidat balíček – příkaz"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: bf9a6e51dfbf1716ba40273487b76ae04c18e948
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="add-command-nuget-cli"></a>Přidat – příkaz (NuGet CLI)

**Platí pro**: balíček publikování &bullet; **podporované verze**: 3.3 +

Přidá zadaný balíček zdroj balíčku jiným protokolem než HTTP (složka nebo cesta UNC) v hierarchickém rozložení, ve kterém se vytvoří složky pro číslo ID a verzi balíčku. Příklad:

    \\myserver\packages
      └─<packageID>
        └─<version>
          ├─<packageID>.<version>.nupkg
          ├─<packageID>.<version>.nupkg.sha512
          └─<packageID>.nuspec

Při obnovení nebo aktualizaci na zdroji balíčku, hierarchickém rozložení poskytuje výrazně lepší výkon.

Všechny soubory v balíčku rozšířit do cílového zdroje balíčku, použít `-Expand` přepínače. To obvykle vede k další podsložky zobrazovaných v cílovém umístění, jako například `tools` a `lib`.

## <a name="usage"></a>Použití

```
nuget add <packagePath> -Source <sourcePath> [options]
```

kde `<packagePath>` je název cesty k balíčku, který chcete přidat, a `<sourcePath>` určuje zdroji na základě složky balíčku, do které budou přidány balíčku. Zdroje protokolu HTTP nejsou podporovány.

## <a name="options"></a>Možnosti

| Možnost | Popis |
| --- | --- |
| ConfigFile | Konfigurační soubor NuGet použít. Pokud není zadaný, *%AppData%\NuGet\NuGet.Config* se používá.| 
| Rozbalte položku | Přidá všechny soubory v balíčku ke zdroji balíčku. |
| ForceEnglishOutput | *(3.5 +)*  Vynutí nuget.exe ke spuštění pomocí invariantní, na základě angličtina jazykové verze. |
| Nápověda | Zobrazí nápovědu pro příkaz. |
| Neinteraktivní | Potlačí výzvy pro vstup uživatele nebo potvrzení. |
| Podrobnosti | Určuje množství podrobností, které jsou zobrazené ve výstupu: *normální*, *quiet*, *podrobné*. |

Viz také [proměnné prostředí](cli-ref-environment-variables.md)

## <a name="examples"></a>Příklady

```
nuget add foo.nupkg -Source c:\bar\

nuget add foo.nupkg -Source \\bar\packages\
```