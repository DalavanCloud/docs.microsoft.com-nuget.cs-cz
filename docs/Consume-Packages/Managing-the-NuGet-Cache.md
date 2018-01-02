---
title: "Jak spravovat balíček ukládání do mezipaměti v NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 7/26/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 3932217d-780d-4bd1-ad15-767acd3e8870
description: "Jak spravovat jiný balíček NuGet ukládá do mezipaměti, který neexistuje na počítači, které se používají při instalaci nebo obnovují se balíčky."
keywords: "Mezipaměť balíčku NuGet, balíček ukládání do mezipaměti, mezipaměti NuGet, Správa mezipaměti, místní mezipaměti NuGet, globální mezipaměti NuGet, místní hodnoty – příkaz NuGet, vymazání mezipaměti"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 6e76c219ba420eb285af20e67b26dcdceebb6bab
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="managing-the-nuget-cache"></a>Správa mezipaměti NuGet

NuGet spravuje několik místní mezipaměti, aby se zabránilo stahovali balíčky, které jsou již v počítači a zajistit podporu offline režimu. NuGet 2.8 + automaticky spadne zpět do mezipaměti při instalaci nebo přeinstalování balíčky bez připojení k síti.

Umístění mezipaměti, jsou k dispozici pomocí [místní hodnoty – příkaz](../tools/cli-ref-locals.md):

```
nuget locals all -list
```

Typické výstup vypadá takto:

    http-cache: C:\Users\user\AppData\Local\NuGet\v3-cache   #NuGet 3.x+ cache
    packages-cache: C:\Users\user\AppData\Local\NuGet\Cache  #NuGet 2.x cache
    global-packages: C:\Users\user\.nuget\packages\          #Global packages folder
    temp: C:\Users\user\AppData\Local\Temp\NuGetScratch      #Temp folder

Pokud dojde k potížím instalace balíčku nebo jinak potřeba zajistit, že instalujete balíčky ze vzdáleného galerie, použijte `locals -clear` možnost:

```
nuget locals http-cache -clear        #Clear the 3.x+ cache
nuget locals packages-cache -clear    #Clear the 2.x cache
nuget locals global-packages -clear   #Clear the global packages folder
nuget locals temp -clear              #Clear the temporary cache
nuget locals all -clear               #Clear all caches
```

Všimněte si, že správa mezipaměti v současné době podporuje pouze z příkazového řádku NuGet a není v sadě Visual Studio nebo pomocí konzoly Správce balíčků. Navíc Správa mezipaměti 2.x není podporována v NuGet 3.6 nebo novější.

Následující chyby může stát při použití `nuget locals`:

* **Vymazání místních prostředků se nezdařilo: nelze odstranit jeden nebo více souborů**
* **Adresář není prázdná**

Ty naznačují, buď nemáte oprávnění k odstranění souborů v mezipaměti, nebo že jeden nebo více souborů v mezipaměti jsou v používá jiný proces, který musí být uzavřeny před ty soubory je možné odstranit.