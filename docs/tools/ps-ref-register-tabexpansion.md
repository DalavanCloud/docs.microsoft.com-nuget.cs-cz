---
title: Referenční informace prostředí PowerShell NuGet Register-TabExpansion
description: Referenční dokumentace pro příkaz prostředí PowerShell Register-TabExpansion v konzole Správce balíčků NuGet v sadě Visual Studio.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: 8011c0e6aa951a32114d460803c493810964a7e0
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34818410"
---
# <a name="register-tabexpansion-package-manager-console-in-visual-studio"></a>Register-TabExpansion (konzola Správce balíčků v sadě Visual Studio)

*K dispozici pouze v rámci [Konzola správce balíčků NuGet](package-manager-console.md) v sadě Visual Studio v systému Windows.*

Zaregistruje karta rozšíření pro parametry zadaný příkaz tak, aby při karta se používá, když zadáte příkaz, rozšířená hodnoty se zobrazí jako dostupné možnosti pro parametr nejistá. Všechny předchozí rozšíření pro příkaz se přepíší.

## <a name="syntax"></a>Syntaxe

```ps
Register-TabExpansion [-Name] <String> [-Definition] <Object> [<CommonParameters>]
```

## <a name="parameters"></a>Parametry

| Parametr | Popis |
| --- | --- |
| Název | (Povinné) Příkaz, do které chcete zaregistrovat rozšíření. -Název je volitelný přepínač sám sebe. |
| Definice | (Povinné) Objekt popisující argumentem v syntaxi `@{'<parameter>' = {'<value1>', '<value2>', ...}}` kde `<parameter>` je název parametru upravit a každý `<value>` poskytuje konkrétní rozšíření. Jednoduché i dvojité uvozovky, jsou přijaty. |

Žádná z těchto parametrů přijmout kanálu vstup nebo zástupné znaky.

## <a name="common-parameters"></a>Společné parametry

`Register-TabExpansion` podporuje následující [společné parametry prostředí PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): ladění, Chyba akce, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, podrobná, WarningAction a WarningVariable.

## <a name="examples"></a>Příklady

Vezměte v úvahu řešení, které obsahuje tři názvy projektů EventManager, nástrojů a SpecialParser. Vývojář se často používá `Update-Package` příkazu v různých časech s každou z těchto projekty. Jana vyhledá vhodné používat `Update-Package` příkaz zadejte automatické dokončování rozšíření pro `-ProjectName` argument, takže se nemusí na název projektu zadejte pokaždé, když. 

Následující příkaz, pak zaregistruje názvy těchto tří projektů jako rozšíření pro `-ProjectName` parametr:

```ps
Register-TabExpansion Update-Package @{'ProjectName' = {'EventManager', 'Utilities', 'SpecialParser'}}    
```

Vývojář může zadejte `Update-Package -ProjectName `, stiskněte klávesu Tab a rozšíření nabízeny jako možnosti automatického dokončování v tématu:

![Příklad použití Register-TabExpansion](media/Register-TabExpansion-Example.png)