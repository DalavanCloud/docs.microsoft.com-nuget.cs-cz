---
title: NuGet 2.6.1 poznámky k verzi služby WebMatrix
description: Poznámky k verzi pro NuGet 2.6.1 pro službu WebMatrix, včetně známé problémy, opravy chyb, přidaných funkcí a chcete.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 3d767788d348553cbb5cb82c6f70aac1894628c3
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31818402"
---
# <a name="nuget-261-for-webmatrix-release-notes"></a>NuGet 2.6.1 poznámky k verzi služby WebMatrix

[Poznámky k verzi NuGet 2.6](../release-notes/nuget-2.6.md) | [NuGet 2.7 poznámky k verzi](../release-notes/nuget-2.7.md)

Týmem NuGet vydala aktualizované rozšíření Správce balíčků NuGet pro službu WebMatrix 26 března 2014.  Tato aktualizace se dá nainstalovat z [Galerie rozšíření prostředí WebMatrix](https://blogs.iis.net/webmatrix/retiring-the-webmatrix-extensions-gallery) pomocí následujících kroků:

1. Otevřete službu WebMatrix 3
1. Klikněte na ikonu rozšíření na pásu karet Domů
1. Vyberte kartu aktualizace
1. Klikněte na tlačítko Aktualizovat na verzi 2.6.1 Správce balíčků NuGet
1. Zavřete a znovu spusťte službu WebMatrix 3

## <a name="notable-changes"></a>Upozorňují na důležité změny

Tato rozšíření aktualizace řeší dva největších problémů uživatelů mají potýkají náročné balíčků NuGet v rámci služby WebMatrix.  První došlo k chybě verze schématu NuGet a druhý byl chyby vedoucí k knihovny DLL nula bajtů v `bin` složky.

### <a name="nuget-schema-version-error"></a>Chyba verze schématu NuGet

Vzhledem k tomu, že byl vydán služba WebMatrix 3, byly zavedeny nové funkce do NuGet, které vyžadují novou verzi schématu pro balíčky NuGet.  Při pokusu o spravovat vaše balíčky NuGet ve vašem webu, tyto nové balíčky může vést k chybám, které se zobrazí ve službě WebMatrix.

![Došlo k chybě. Verze schématu není kompatibilní. Prosím upgradujte rozšíření NuGet na nejnovější verzi.](./media/NuGet-2.8/webmatrix-schema-version.png)

Tato nejnovější verze poskytuje kompatibilitu s nejnovější balíčky NuGet, brání výskytu této chyby. Nové verze, včetně Microsoft.AspNet.WebPages balíčky můžete nyní nainstalovat ve službě WebMatrix.  Některé z těchto balíčků byly pomocí funkce NuGet, jako [XDT konfigurační transformaci](../release-notes/nuget-2.6.md#xdt), který dosud nebyl podporován ve službě WebMatrix.

### <a name="zero-byte-dlls-in-bin-folder"></a>Nula bajtů knihovny DLL ve složce Koš

Někteří uživatelé hlásili, která po instalaci NuGet zabalí ve službě WebMatrix, které zahrnují knihovny DLL, které jsou kopírovány do přihrádky, který zobrazení knihovny DLL v `bin` složky jako soubory 0 bajtů.  Tím se přeruší aplikace za běhu.

[Tento problém](https://nuget.codeplex.com/workitem/4060) nyní byl opraven.

## <a name="other-recent-improvements"></a>Další vylepšení poslední

Když 2.8 Správce balíčků NuGet byl vydán pro sadu Visual Studio, vydala společnost Microsoft také Správce balíčků NuGet 2.5.0 pro službu WebMatrix.  Pokud to bylo uvedeno v [poznámky k verzi 2.8 NuGet](../release-notes/nuget-2.8.md#webmatrix-nuget-client-updates), nebyla jsme zmínili, konkrétní nových funkcí tuto aktualizaci zavedená.

### <a name="update-all"></a>Aktualizuje všechny

Teď můžete aktualizovat všechny balíčky webové stránky v jednom kroku!  Když otevřete rozšíření NuGet ve službě WebMatrix, zobrazí seznam všech balíčků v galerii, nainstalované a ty aktualizace, které jsou k dispozici.  Dříve se jednotlivě aktualizovat všechny balíčky, ale nyní je užitečné tlačítko "Aktualizovat vše", které se zobrazí na kartě aktualizace.

![Klikněte na Aktualizovat vše aktualizovat všechny balíčky s aktualizacemi, k dispozici](./media/NuGet-2.8/webmatrix-update-all.png)

### <a name="overwrite-existing-files"></a>Přepsat existující soubory

Při instalaci balíčků, které obsahují soubory, které již existují na webovém serveru, NuGet ignorovala vždy bezobslužně tyto soubory (a nechat existující soubory samostatně).  To může vést k dojem, že byl nainstalován balíček, nebo správně aktualizován, když ve skutečnosti fungovat.  NuGet se nyní zobrazí výzvu k přepisovat soubory.

![Řešení konfliktů souborů](./media/NuGet-2.8/webmatrix-overwrite-file.png)