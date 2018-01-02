---
title: "Push a odstranit, NuGet rozhraní API | Microsoft Docs"
author:
- joelverhagen
- kraigb
ms.author:
- joelverhagen
- kraigb
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 1eaa403a-5c13-4c05-9352-2f791b98aa7e
description: "Služba publikování umožňuje klientům publikování nové balíčky a unlist nebo odstranit existující balíčky."
keywords: "Nabízené balíček NuGet rozhraní API, rozhraní API NuGet odstranit balíček NuGet API unlist balíčku, nahrajte balíček NuGet rozhraní API, rozhraní API NuGet vytvořit balíček"
ms.reviewer:
- karann
- unniravindranathan
ms.openlocfilehash: 1fa3c0e1698a11208d9ef29fdf26a4980cb60cf5
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="push-and-delete"></a>Push a odstranění

Je možné nabízené a odstranit (nebo unlist, v závislosti na implementaci serveru) balíčky, pomocí rozhraní API V3 NuGet.
Obě tyto operace jsou na základě odhlásit z `PackagePublish` v nalezen prostředek [indexu služby](service-index.md).

## <a name="versioning"></a>Správa verzí

Následující `@type` hodnota se používá:

@typeHodnota          | Poznámky
-------------------- | -----
PackagePublish/2.0.0 | Původní verze

## <a name="base-url"></a>Základní adresu URL

Základní adresu URL pro následující rozhraní API je hodnota `@id` vlastnost `PackagePublish/2.0.0` prostředků ve zdroji balíčků [indexu služby](service-index.md). Adresa URL nuget.org v dokumentaci je použita. Vezměte v úvahu `https://www.nuget.org/api/v2/package` jako zástupný symbol pro `@id` nalezena hodnota v indexu služby.

Všimněte si, že tato adresa URL odkazuje do stejného umístění jako starší verze koncový bod nabízené V2 vzhledem k tomu, že protokol je stejný.

## <a name="http-methods"></a>Metody HTTP

`PUT` a `DELETE` metody HTTP podporuje tento prostředek. Které metody jsou podporovány na každém koncovém bodu najdete níže.

## <a name="push-a-package"></a>Push balíčku

nuget.org podporuje vkládání nové balíčky pomocí následující rozhraní API. Pokud balíček s zadané ID a verzí již existuje, odmítnou nuget.org nabízeného oznámení. Další zdroje balíčku může podporovat nahrazování existujícího balíčku.

```
PUT https://www.nuget.org/api/v2/package
```

### <a name="request-parameters"></a>Parametry žádosti

Název           | V     | Typ   | Požadováno | Poznámky
-------------- | ------ | ------ | -------- | -----
X-NuGet-ApiKey | Záhlaví | odkazy řetězců | Ano      | Třeba `X-NuGet-ApiKey: {USER_API_KEY}`.

Klíč rozhraní API je neprůhledný řetězec, že podmínky ze zdroje balíčků uživatelem a nakonfigurované do klienta. Je vyžadováno žádné konkrétní řetězec formátu, ale nesmí překročit délka klíč rozhraní API přiměřené velikosti pro hodnoty hlavičky protokolu HTTP.

### <a name="request-body"></a>Text žádosti

Textu požadavku musí pocházet v následující podobě:

#### <a name="multipart-form-data"></a>Dat vícedílného formuláře

Hlavička požadavku `Content-Type` je `multipart/form-data` a první položky v těle žádosti je nezpracované bajtů .nupkg se instaluje. Následující položky v textu vícedílné zprávy se ignorují. Název souboru nebo jiné záhlaví položek s více částmi se ignorují.

### <a name="response"></a>Odpověď

Stavový kód | Význam
----------- | -------
201, 202    | Balíček byl úspěšně poslat.
400         | Zadaný balíček je neplatná
409         | Balíček s zadané ID a verzí již existuje.

Implementace serveru lišit vráceny v případě, že balíček je úspěšně nabídnutých úspěch stavový kód.

## <a name="delete-a-package"></a>Odstranění balíčku

nuget.org interpretuje požadavku na odstranění balíčku jako na "unlist". To znamená, že balíček je stále k dispozici pro existující příjemce balíčku, ale balíček už se zobrazí ve výsledcích hledání nebo webové rozhraní. Další informace o tento postup najdete v tématu [odstranit balíčky](../policies/deleting-packages.md) zásad. Jiných implementacích serveru jsou volně interpretovat jako pevný odstranění tohoto signálu, soft odstranit nebo unlist. Například [NuGet.Server](https://www.nuget.org/packages/NuGet.Server) (implementaci serveru pouze podpora starší API V2) podporuje zpracování této žádosti jako unlist nebo pevné odstranění podle možnosti konfigurace.

```
DELETE https://www.nuget.org/api/v2/package/{ID}/{VERSION}
```

### <a name="request-parameters"></a>Parametry žádosti

Název           | V     | Typ   | Požadováno | Poznámky
-------------- | ------ | ------ | -------- | -----
ID             | Adresa URL    | odkazy řetězců | Ano      | ID balíčku se má odstranit
VERZE        | Adresa URL    | odkazy řetězců | Ano      | Verze balíčku odstranit
X-NuGet-ApiKey | Záhlaví | odkazy řetězců | Ano      | Třeba `X-NuGet-ApiKey: {USER_API_KEY}`.

### <a name="response"></a>Odpověď

Stavový kód | Význam
----------- | -------
204         | Balíček byl odstraněn.
404         | Žádný balíček poskytnutým `ID` a `VERSION` existuje