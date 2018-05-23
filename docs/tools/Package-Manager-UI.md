---
title: Odkaz uživatelského rozhraní Správce balíčků NuGet
description: Pokyny k používání uživatelského rozhraní Správce balíčků NuGet v sadě Visual Studio pro práci s balíčky NuGet.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/08/2017
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
- vs.nuget.packagemanager.ui
ms.openlocfilehash: 1d8cb8186b9cedb29918d48539bdf45b130030c0
ms.sourcegitcommit: 00c4c809c69c16fcf4d81012eb53ea22f0691d0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2018
---
# <a name="nuget-package-manager-ui"></a><span data-ttu-id="1af2b-103">Uživatelského rozhraní Správce balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="1af2b-103">NuGet Package Manager UI</span></span>

<span data-ttu-id="1af2b-104">Uživatelské rozhraní Správce balíčků NuGet v sadě Visual Studio v systému Windows umožňuje snadno nainstalování, odinstalování a aktualizovat balíčky NuGet ve projekty a řešení.</span><span class="sxs-lookup"><span data-stu-id="1af2b-104">The NuGet Package Manager UI in Visual Studio on Windows allows you to easily install, uninstall, and update NuGet packages in projects and solutions.</span></span> <span data-ttu-id="1af2b-105">Pro prostředí v sadě Visual Studio pro Mac, najdete v části [balíček včetně NuGet ve vašem projektu](/visualstudio/mac/nuget-walkthrough).</span><span class="sxs-lookup"><span data-stu-id="1af2b-105">For the experience in Visual Studio for Mac, see [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span> <span data-ttu-id="1af2b-106">Uživatelské rozhraní Správce balíčků není součástí Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1af2b-106">The Package Manager UI is not included with Visual Studio Code.</span></span>

<span data-ttu-id="1af2b-107">V tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="1af2b-107">In this topic:</span></span>

- [<span data-ttu-id="1af2b-108">Hledání a instalaci balíčku (Procházet karta)</span><span class="sxs-lookup"><span data-stu-id="1af2b-108">Finding and installing a package (Browse tab)</span></span>](#finding-and-installing-a-package)
- [<span data-ttu-id="1af2b-109">Odinstalace balíčku (karta nainstalovaná)</span><span class="sxs-lookup"><span data-stu-id="1af2b-109">Uninstalling a package (Installed tab)</span></span>](#uninstalling-a-package)
- <span data-ttu-id="1af2b-110">[Aktualizace balíčku (karty nainstalovaná a aktualizace)](#updating-a-package) (zahrnuje ["Implicitně odkazuje sady SDK" nebo "AutoReferenced" zprávy](#implicit_reference))</span><span class="sxs-lookup"><span data-stu-id="1af2b-110">[Updating a package (Installed and Updates tabs)](#updating-a-package) (includes the ["Implicitly referenced by an SDK" or "AutoReferenced" message](#implicit_reference))</span></span>
- <span data-ttu-id="1af2b-111">[Spravovat balíčky pro řešení](#managing-packages-for-the-solution) (práce s více projektů současně).</span><span class="sxs-lookup"><span data-stu-id="1af2b-111">[Managing packages for the solution](#managing-packages-for-the-solution) (working with multiple projects at the same time).</span></span>
- [<span data-ttu-id="1af2b-112">Zdroje balíčků</span><span class="sxs-lookup"><span data-stu-id="1af2b-112">Package sources</span></span>](#package-sources)
- [<span data-ttu-id="1af2b-113">Ovládání možnosti Správce balíčku</span><span class="sxs-lookup"><span data-stu-id="1af2b-113">Package manager Options control</span></span>](#package-manager-options-control)

> [!Note]
> <span data-ttu-id="1af2b-114">Pokud jste chybí Správce balíčků NuGet v sadě Visual Studio 2015, zkontrolujte **nástroje > rozšíření a aktualizace...**  a vyhledejte *Správce balíčků NuGet* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1af2b-114">If you're missing the NuGet Package Manager in Visual Studio 2015, check **Tools > Extensions and Updates...** and search for the *NuGet Package Manager* extension.</span></span> <span data-ttu-id="1af2b-115">Pokud nemůžete použít instalační program rozšíření v sadě Visual Studio, stáhněte si rozšíření přímo z [ https://dist.nuget.org/index.html ](https://dist.nuget.org/index.html).</span><span class="sxs-lookup"><span data-stu-id="1af2b-115">If you're unable to use the extensions installer in Visual Studio, download the extension directly from [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html).</span></span>
>
> <span data-ttu-id="1af2b-116">V aplikaci Visual Studio 2017 jsou NuGet a Správce balíčků NuGet automaticky nainstalovány s žádným. NET související úlohy.</span><span class="sxs-lookup"><span data-stu-id="1af2b-116">In Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed with any .NET-related workloads.</span></span> <span data-ttu-id="1af2b-117">Nainstalujte ji jednotlivě výběrem **jednotlivých součástí > Code nástroje > Správce balíčků NuGet** možnosti v instalačním programu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1af2b-117">Install it individually by selecting the **Individual components > Code tools > NuGet package manager** option in the Visual Studio 2017 installer.</span></span>

## <a name="finding-and-installing-a-package"></a><span data-ttu-id="1af2b-118">Hledání a instalaci balíčku</span><span class="sxs-lookup"><span data-stu-id="1af2b-118">Finding and installing a package</span></span>

1. <span data-ttu-id="1af2b-119">V **Průzkumníku řešení**, klikněte pravým tlačítkem na buď **odkazy** nebo projekt a vyberte **spravovat balíčky NuGet...** .</span><span class="sxs-lookup"><span data-stu-id="1af2b-119">In **Solution Explorer**, right-click either **References**  or a project and select **Manage NuGet Packages...**.</span></span>

    ![Spravovat balíčky NuGet nabídky](media/ManagePackagesUICommand.png)

1. <span data-ttu-id="1af2b-121">**Procházet** karta zobrazí balíčky podle oblíbenosti z aktuálně vybraného zdroje (najdete v části [balíček zdroje](#package-sources)).</span><span class="sxs-lookup"><span data-stu-id="1af2b-121">The **Browse** tab displays packages by popularity from the currently selected source (see [package sources](#package-sources)).</span></span> <span data-ttu-id="1af2b-122">Vyhledejte konkrétní balíček pomocí vyhledávacího pole v levé horní části.</span><span class="sxs-lookup"><span data-stu-id="1af2b-122">Search for a specific package using the search box on the upper left.</span></span> <span data-ttu-id="1af2b-123">Vyberte balíček ze seznamu zobrazíte její informace, které taky umožňuje **nainstalovat** tlačítko společně s rozevírací výběr verze.</span><span class="sxs-lookup"><span data-stu-id="1af2b-123">Select a package from the list to display its information, which also enables the **Install** button along with a version-selection drop-down.</span></span>

    ![Spravovat kartu Procházet dialogové okno balíčky NuGet](media/Search.png)

1. <span data-ttu-id="1af2b-125">Vyberte požadovanou verzi z rozevíracího seznamu a vyberte **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="1af2b-125">Select the desired version from the drop-down and select **Install**.</span></span> <span data-ttu-id="1af2b-126">Visual Studio nainstaluje do projektu balíček a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="1af2b-126">Visual Studio installs the package and its dependencies into the project.</span></span> <span data-ttu-id="1af2b-127">Můžete být vyzváni k potvrzení licenčních podmínek.</span><span class="sxs-lookup"><span data-stu-id="1af2b-127">You may be asked to accept license terms.</span></span> <span data-ttu-id="1af2b-128">Po dokončení instalace se přidané balíčky zobrazí na **nainstalovaná** kartě. Balíčky jsou také uvedeny v **odkazy** uzlu Průzkumníka řešení, která určuje, zda mohou odkazovat na ně v projektu s `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="1af2b-128">When installation is complete, the added packages appear on the **Installed** tab. Packages are also listed in the **References** node of Solution Explorer, indicating that you can refer to them in the project with `using` statements.</span></span>

    ![Odkazy v Průzkumníku řešení](media/References.png)

> [!Tip]
> <span data-ttu-id="1af2b-130">Při hledání zahrnout předprodejní verze a aby předprodejní verze dostupné ve verzi rozevíracího seznamu, vyberte **zahrnout předběžné verze** možnost.</span><span class="sxs-lookup"><span data-stu-id="1af2b-130">To include prerelease versions in the search, and to make prerelease versions available in the version drop-down, select the **Include prerelease** option.</span></span>

## <a name="uninstalling-a-package"></a><span data-ttu-id="1af2b-131">Odinstalace balíčku</span><span class="sxs-lookup"><span data-stu-id="1af2b-131">Uninstalling a package</span></span>

1. <span data-ttu-id="1af2b-132">V **Průzkumníku řešení**, klikněte pravým tlačítkem na buď **odkazy** nebo požadovaný projekt a vyberte **spravovat balíčky NuGet...** .</span><span class="sxs-lookup"><span data-stu-id="1af2b-132">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**.</span></span>
1. <span data-ttu-id="1af2b-133">Vyberte **nainstalovaná** kartě.</span><span class="sxs-lookup"><span data-stu-id="1af2b-133">Select the **Installed** tab.</span></span>
1. <span data-ttu-id="1af2b-134">Vyberte balíček, který chcete odinstalovat (pomocí vyhledávání pro filtrování seznamu v případě potřeby) a vyberte **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="1af2b-134">Select the package to uninstall (using search to filter the list if necessary) and select **Uninstall**.</span></span>

    ![Odinstalace balíčku](media/UninstallPackage.png)

1. <span data-ttu-id="1af2b-136">Všimněte si, že **zahrnout předběžné verze** a **zdroj balíčku** ovládací prvky mít žádný vliv, při odinstalaci balíčků.</span><span class="sxs-lookup"><span data-stu-id="1af2b-136">Note that the **Include prerelease** and **Package source** controls have no effect when uninstalling packages.</span></span>

## <a name="updating-a-package"></a><span data-ttu-id="1af2b-137">Aktualizace balíčku</span><span class="sxs-lookup"><span data-stu-id="1af2b-137">Updating a package</span></span>

1. <span data-ttu-id="1af2b-138">V **Průzkumníku řešení**, klikněte pravým tlačítkem na buď **odkazy** nebo požadovaný projekt a vyberte **spravovat balíčky NuGet...** . (V projektech webových stránek, klikněte pravým tlačítkem myši **Bin** složky.)</span><span class="sxs-lookup"><span data-stu-id="1af2b-138">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**. (In web site projects, right-click the **Bin** folder.)</span></span>
1. <span data-ttu-id="1af2b-139">Vyberte **aktualizace** karty zobrazíte balíčky, které jsou k dispozici aktualizace ze zdroje vybraný balíček.</span><span class="sxs-lookup"><span data-stu-id="1af2b-139">Select the **Updates** tab to see packages that have available updates from the selected package sources.</span></span> <span data-ttu-id="1af2b-140">Vyberte **zahrnout předběžné verze** zahrnout předběžné verze balíčků v seznamu aktualizací.</span><span class="sxs-lookup"><span data-stu-id="1af2b-140">Select **Include prerelease** to include prerelease packages in the update list.</span></span>
1. <span data-ttu-id="1af2b-141">Vyberte balíček, který chcete aktualizovat, vyberte požadovanou verzi z rozevíracího seznamu na pravé straně a vyberte **aktualizace**.</span><span class="sxs-lookup"><span data-stu-id="1af2b-141">Select the package to update, select the desired version from the drop-down on the right, and select **Update**.</span></span>

    ![Aktualizace balíčku](media/UpdatePackages.png)

1. <a name="implicit_reference"></a><span data-ttu-id="1af2b-143">Pro některé balíčky **aktualizace** tlačítko je zakázané a zobrazí se zpráva s informacemi o tom, že ji "implicitně odkazuje sady SDK" (nebo "AutoReferenced").</span><span class="sxs-lookup"><span data-stu-id="1af2b-143">For some packages, the **Update** button is disabled and a message appears saying that it's "Implicitly referenced by an SDK" (or "AutoReferenced").</span></span> <span data-ttu-id="1af2b-144">Zpráva označuje, že balíčku, například Microsoft.NETCore.App nebo Microsoft.NETStandard.Library, je součástí větší framework nebo sady SDK a nesmí být aktualizovány nezávisle.</span><span class="sxs-lookup"><span data-stu-id="1af2b-144">The message indicates that the package, such as Microsoft.NETCore.App or Microsoft.NETStandard.Library, is part of a larger framework or SDK and should not be updated independently.</span></span> <span data-ttu-id="1af2b-145">(Tyto balíčky jsou interně označené `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) Pokud chcete aktualizovat balíček, aktualizujte sadu SDK do které patří, odvození obsahující SDK název balíčku.</span><span class="sxs-lookup"><span data-stu-id="1af2b-145">(Such packages are internally marked with `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) To update the package, update the SDK to which it belongs, inferring the containing SDK from the package name.</span></span> <span data-ttu-id="1af2b-146">Například balíček jako Microsoft.NETCore.App je součástí rozhraní .NET Core SDK, proto musíte aktualizovat instalaci .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1af2b-146">For example, a package like Microsoft.NETCore.App is part of the .NET Core SDK, therefore you need to update your  .NET Core SDK installation.</span></span>

    ![Příklad balíček označen jako implicitně odkazy nebo AutoReferenced](media/PackageManagerUIAutoReferenced.png)

1. <span data-ttu-id="1af2b-148">Chcete-li aktualizovat více balíčků jejich nejnovější verze, vyberte je v seznamu a vyberte **aktualizace** tlačítko výše v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-148">To update multiple packages to their newest versions, select  them in the list and select the **Update** button above the list.</span></span>
1. <span data-ttu-id="1af2b-149">Můžete také aktualizovat individuální balíčku z **nainstalovaná** kartě. V takovém případě podrobnosti balíčku zahrnout selektor verze (podléhají **zahrnout předběžné verze** možnost) a **aktualizace** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1af2b-149">You can also update an individual package from the **Installed** tab. In this case, the details for the package include a version selector (subject to the **Include prerelease** option) and an **Update** button.</span></span>

## <a name="managing-packages-for-the-solution"></a><span data-ttu-id="1af2b-150">Spravovat balíčky pro řešení</span><span class="sxs-lookup"><span data-stu-id="1af2b-150">Managing packages for the solution</span></span>

<span data-ttu-id="1af2b-151">Spravovat balíčky pro řešení je pohodlný způsob pro práci s více projektů současně.</span><span class="sxs-lookup"><span data-stu-id="1af2b-151">Managing packages for a solution is a convenient means to work with multiple projects simultaneously.</span></span>

1. <span data-ttu-id="1af2b-152">Vyberte **nástroje > Správce balíčků NuGet > Správa balíčků NuGet pro řešení...**  nabídky příkazu, nebo klikněte pravým tlačítkem na řešení a vyberte **spravovat balíčky NuGet...** :</span><span class="sxs-lookup"><span data-stu-id="1af2b-152">Select the **Tools > NuGet Package Manager > Manage NuGet Packages for Solution...** menu command, or right-click the solution and select **Manage NuGet Packages...**:</span></span>

    ![Správa balíčků NuGet pro řešení](media/ManagePackagesSolutionUICommand.png)

1. <span data-ttu-id="1af2b-154">Při správě balíčky pro řešení, uživatelské rozhraní umožní vám vybrat projektů, které jsou ovlivněné operace:</span><span class="sxs-lookup"><span data-stu-id="1af2b-154">When managing packages for the solution, the UI lets you select the projects that are affected by the operations:</span></span>

    ![Selektor projektu při správě balíčky pro řešení](media/SolutionPackagesUI.png)

### <a name="consolidate-tab"></a><span data-ttu-id="1af2b-156">Konsolidovat karta</span><span class="sxs-lookup"><span data-stu-id="1af2b-156">Consolidate tab</span></span>

<span data-ttu-id="1af2b-157">Vývojáři obvykle považuje za chybný postup používat různé verze stejného balíčku NuGet v různých projektů ve stejném řešení.</span><span class="sxs-lookup"><span data-stu-id="1af2b-157">Developers typically consider it bad practice to use different versions of the same NuGet package across different projects in the same solution.</span></span> <span data-ttu-id="1af2b-158">Pokud zvolíte možnost spravovat balíčky pro řešení, poskytuje uživatelské rozhraní Správce balíčků **konsolidace** karty, na které můžete snadno zobrazit kde balíčky s čísla různých verzí používají různé projekty v řešení:</span><span class="sxs-lookup"><span data-stu-id="1af2b-158">When you choose to manage packages for a solution, the Package Manager UI provides a **Consolidate** tab on which you can easily see where packages with distinct version numbers are used by different projects in the solution:</span></span>

![Karta konsolidovat uživatelského rozhraní Správce balíčků](media/ConsolidateTab.png)

<span data-ttu-id="1af2b-160">V tomto příkladu je projektu ClassLibrary1 využitím objektu EntityFramework 6.2.0, zatímco ConsoleApp1 je s využitím objektu EntityFramework 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="1af2b-160">In this example, the ClassLibrary1 project is using EntityFramework 6.2.0, whereas ConsoleApp1 is using EntityFramework 6.1.0.</span></span> <span data-ttu-id="1af2b-161">Pro konsolidaci verze balíčku, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="1af2b-161">To consolidate package versions, do the following:</span></span>

- <span data-ttu-id="1af2b-162">Vyberte projekty k aktualizaci v seznamu projektu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-162">Select the projects to update in the project list.</span></span>
- <span data-ttu-id="1af2b-163">Vyberte verze se má použít na všechny projekty v **verze** ovládací prvek, jako je například EntityFramework 6.2.0.</span><span class="sxs-lookup"><span data-stu-id="1af2b-163">Select the version to use in all those projects in the **Version** control, such as EntityFramework 6.2.0.</span></span>
- <span data-ttu-id="1af2b-164">Vyberte **nainstalovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1af2b-164">Select the **Install** button.</span></span>

<span data-ttu-id="1af2b-165">Správce balíčků nainstaluje verzi vybraný balíček do všech vybraných projektů, po které balíčku již nadále nebude zobrazovat na **konsolidace** kartě.</span><span class="sxs-lookup"><span data-stu-id="1af2b-165">The Package Manager installs the selected package version into all selected projects, after which the package no longer appears on the **Consolidate** tab.</span></span>

## <a name="package-sources"></a><span data-ttu-id="1af2b-166">Zdroje balíčků</span><span class="sxs-lookup"><span data-stu-id="1af2b-166">Package sources</span></span>

<span data-ttu-id="1af2b-167">Chcete-li změnit zdroj, ze kterého Visual Studio získá balíčky, vyberte jednu z modulu pro výběr zdroje:</span><span class="sxs-lookup"><span data-stu-id="1af2b-167">To change the source from which Visual Studio obtains packages, select one from the source selector:</span></span>

![Výběr zdroje balíčku v uživatelské rozhraní Správce balíčků](media/PackageSourceDropDown.png)

<span data-ttu-id="1af2b-169">Správa zdrojů balíčků:</span><span class="sxs-lookup"><span data-stu-id="1af2b-169">To manage package sources:</span></span>

1. <span data-ttu-id="1af2b-170">Vyberte **nastavení** ikony v uživatelském rozhraní Správce balíčků uvedených níže nebo používat **nástroje > Možnosti** příkazů a přejděte k položce **Správce balíčků NuGet**:</span><span class="sxs-lookup"><span data-stu-id="1af2b-170">Select the **Settings** icon in the Package Manager UI outlined below or use the **Tools > Options** command and scroll to **NuGet Package Manager**:</span></span>

    ![Ikona nastavení uživatelského rozhraní správce balíčku](media/PackageSourceSettings.png)

1. <span data-ttu-id="1af2b-172">Vyberte **zdroje balíčků** uzlu:</span><span class="sxs-lookup"><span data-stu-id="1af2b-172">Select the **Package Sources** node:</span></span>

    ![Možnosti zdroje balíčku](media/options.png)

1. <span data-ttu-id="1af2b-174">Přidat zdroj, vyberte **+**, upravit název, zadejte adresu URL nebo cestu **zdroj** řízení a vyberte **aktualizace**.</span><span class="sxs-lookup"><span data-stu-id="1af2b-174">To add a source, select **+**, edit the name, enter the URL or path in the **Source** control, and select  **Update**.</span></span> <span data-ttu-id="1af2b-175">Zdroj se teď zobrazí v modulu pro výběr rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-175">The source now appears in the selector drop-down.</span></span>
1. <span data-ttu-id="1af2b-176">Chcete-li změnit zdroj balíčku, vyberte ho, proveďte úpravy v **název** a **zdroj** pole a vyberte **aktualizace**.</span><span class="sxs-lookup"><span data-stu-id="1af2b-176">To change a package source, select it, make edits in the **Name** and **Source** boxes, and select **Update**.</span></span>
1. <span data-ttu-id="1af2b-177">Zakázat zdroj balíčku, zrušte zaškrtnutí políčka nalevo od názvu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-177">To disable a package source, clear the box to the left of the name in the list.</span></span>
1. <span data-ttu-id="1af2b-178">Pokud chcete odebrat zdroj balíčku, vyberte ho a pak vyberte **X** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1af2b-178">To remove a package source, select it and then select the **X** button.</span></span>
1. <span data-ttu-id="1af2b-179">Pomocí nahoru a dolů tlačítek Chcete-li změnit pořadí priority zdroje balíčku.</span><span class="sxs-lookup"><span data-stu-id="1af2b-179">Use the up and down arrow buttons to change the priority order of the package sources.</span></span> <span data-ttu-id="1af2b-180">Při obnovování balíčků pro projekt sady Visual Studio vyhledá tyto zdroje v pořadí podle priority.</span><span class="sxs-lookup"><span data-stu-id="1af2b-180">Visual Studio searches these sources in the priority order when restoring packages for a project.</span></span> <span data-ttu-id="1af2b-181">Další informace najdete v tématu [obnovení balíčků](../consume-packages/package-restore.md).</span><span class="sxs-lookup"><span data-stu-id="1af2b-181">For more information, see [Package restore](../consume-packages/package-restore.md).</span></span>

> [!Tip]
> <span data-ttu-id="1af2b-182">Pokud je zdroj balíčku se znovu zobrazí po odstranění, nemusí být zobrazeny v úrovni počítače nebo individuální `NuGet.Config` soubory.</span><span class="sxs-lookup"><span data-stu-id="1af2b-182">If a package source reappears after deleting it, it may be listed in a computer-level or user-level `NuGet.Config` files.</span></span> <span data-ttu-id="1af2b-183">V tématu [konfigurace NuGet chování](../consume-packages/configuring-nuget-behavior.md) pro umístění tyto soubory pak odebrat zdroj upravit soubory ručně nebo pomocí [nuget zdroje příkaz](../tools/nuget-exe-CLI-reference.md).</span><span class="sxs-lookup"><span data-stu-id="1af2b-183">See [Configuring NuGet behavior](../consume-packages/configuring-nuget-behavior.md) for the location of these files, then remove the source by editing the files manually or using the [nuget sources command](../tools/nuget-exe-CLI-reference.md).</span></span>

## <a name="package-manager-options-control"></a><span data-ttu-id="1af2b-184">Ovládání možnosti Správce balíčku</span><span class="sxs-lookup"><span data-stu-id="1af2b-184">Package manager Options control</span></span>

<span data-ttu-id="1af2b-185">Pokud je vybraná balíčku, uživatelské rozhraní Správce balíčků zobrazí malá, rozšíření **možnosti** řízení níže modulu pro výběr verze (viz zde i sbalené a rozbalené).</span><span class="sxs-lookup"><span data-stu-id="1af2b-185">When a package is selected, the Package Manager UI displays a small, expandable **Options** control below the version selector (shown here both collapsed and expanded).</span></span> <span data-ttu-id="1af2b-186">Všimněte si, že pro některé projekt typy pouze **zobrazit okno náhledu** možnost je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1af2b-186">Note that for some project types, only the **Show preview window** option is provided.</span></span>

![Možnosti správce balíčku](media/PackageManagerUIOptions.png)

<span data-ttu-id="1af2b-188">Následující části popisují tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="1af2b-188">The following sections explain these options.</span></span>

### <a name="show-preview-window"></a><span data-ttu-id="1af2b-189">Zobrazit okno náhledu</span><span class="sxs-lookup"><span data-stu-id="1af2b-189">Show preview window</span></span>

<span data-ttu-id="1af2b-190">Při výběru modální okna zobrazí který závislosti zvolené balíčku před instalací balíčku:</span><span class="sxs-lookup"><span data-stu-id="1af2b-190">When selected, a modal window displays which the dependencies of a chosen package before the package is installed:</span></span>

![Dialogové okno náhledu příklad](media/InstallPreviewDialog.png)

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="install-options"></a>

### <a name="install-and-update-options"></a><span data-ttu-id="1af2b-192">Možnosti instalace a aktualizace</span><span class="sxs-lookup"><span data-stu-id="1af2b-192">Install and Update Options</span></span>

<span data-ttu-id="1af2b-193">(Není k dispozici pro všechny typy projektů.)</span><span class="sxs-lookup"><span data-stu-id="1af2b-193">(Not available for all project types.)</span></span>

<span data-ttu-id="1af2b-194">**Chování závislostí** konfiguruje, jak NuGet rozhodne, která verze závislé balíčky pro instalaci:</span><span class="sxs-lookup"><span data-stu-id="1af2b-194">**Dependency behavior** configures how NuGet decides which versions of dependent packages to install:</span></span>

- <span data-ttu-id="1af2b-195">*Ignorovat závislosti* přeskočí instalaci všechny závislosti, které obvykle dělí instalovaného balíčku.</span><span class="sxs-lookup"><span data-stu-id="1af2b-195">*Ignore dependencies* skips installing any dependencies, which typically breaks the package being installed.</span></span>
- <span data-ttu-id="1af2b-196">*Nejnižší* [výchozí] nainstaluje závislost číslo minimální verze, který splňuje požadavky na primární zvolené balíčku.</span><span class="sxs-lookup"><span data-stu-id="1af2b-196">*Lowest* [Default] installs the dependency with the minimal version number that meets the requirements of the primary chosen package.</span></span>
- <span data-ttu-id="1af2b-197">*Nejvyšší oprava* nainstaluje verzi s stejná hlavní verze a podverze čísla, ale nejvyšší číslo opravy.</span><span class="sxs-lookup"><span data-stu-id="1af2b-197">*Highest Patch* installs the version with the same major and minor version numbers, but the highest patch number.</span></span> <span data-ttu-id="1af2b-198">Například pokud je zadaná verze 1.2.2 pak nejvyšší verzi, která začíná 1.2 bude nainstalována</span><span class="sxs-lookup"><span data-stu-id="1af2b-198">For example, if version 1.2.2 is specified then the highest version that starts with 1.2 will be installed</span></span>
- <span data-ttu-id="1af2b-199">*Nejvyšší vedlejší* nainstaluje verze se stejnou hlavní číslo verze, ale číslem a oprava číslo.</span><span class="sxs-lookup"><span data-stu-id="1af2b-199">*Highest Minor* installs the version with the same major version number but the highest minor number and patch number.</span></span> <span data-ttu-id="1af2b-200">Pokud je určená verze 1.2.2, pak nejvyšší verzi, která začíná 1 budou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="1af2b-200">If version 1.2.2 is specified, then the highest version that starts with 1 will be installed</span></span>
- <span data-ttu-id="1af2b-201">*Nejvyšší* nainstaluje nejvyšší dostupné verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="1af2b-201">*Highest* installs the highest available version of the package.</span></span>

<span data-ttu-id="1af2b-202">**Soubor konflikt akce** určuje způsob zpracování NuGet balíčky, které již existují v projektu nebo místního počítače:</span><span class="sxs-lookup"><span data-stu-id="1af2b-202">**File conflict action** specifies how NuGet should handle packages that already exist in the project or local machine:</span></span>

- <span data-ttu-id="1af2b-203">*Výzva* dá pokyn k dotaz, zda chcete zachovat nebo přepsat existující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="1af2b-203">*Prompt* instructs NuGet to ask whether to keep or overwrite existing packages.</span></span>
- <span data-ttu-id="1af2b-204">*Ignorovat všechny* dá pokyn tak, aby přeskočil přepsal všechny existující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="1af2b-204">*Ignore All* instructs NuGet to skip overwriting any existing packages.</span></span>
- <span data-ttu-id="1af2b-205">*Přepsat všechny* dá pokyn k přepsání všechny existující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="1af2b-205">*Overwrite All* instructs NuGet to overwrite any existing packages.</span></span>

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="uninstall-options"></a>

### <a name="uninstall-options"></a><span data-ttu-id="1af2b-206">Odinstalování možností</span><span class="sxs-lookup"><span data-stu-id="1af2b-206">Uninstall Options</span></span>

<span data-ttu-id="1af2b-207">(Není k dispozici pro všechny typy projektů.)</span><span class="sxs-lookup"><span data-stu-id="1af2b-207">(Not available for all project types.)</span></span>

<span data-ttu-id="1af2b-208">**Odebrání závislostí**: při výběru odebere všechny závislé balíčky, pokud nejsou jinde odkazovaná v projektu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-208">**Remove dependencies**: when selected, removes any dependent packages if they're not referenced elsewhere in the project.</span></span>

<span data-ttu-id="1af2b-209">**Vynutit odinstalaci i v případě, že neexistují závislosti na něm**: při výběru Odinstaluje balíček i v případě, že je stále odkazováno v projektu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-209">**Force uninstall even if there are dependencies on it**: when selected, uninstalls a package even if it's still being referenced in the project.</span></span> <span data-ttu-id="1af2b-210">To se obvykle používá v kombinaci s **odebrání závislostí** odebrat balíček a to bez ohledu závislostí je nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="1af2b-210">This is typically used in combination with **Remove dependencies** to remove a package and whatever dependencies it installed.</span></span> <span data-ttu-id="1af2b-211">Pomocí této možnosti může, ale vést ke poškozenými odkazy v projektu.</span><span class="sxs-lookup"><span data-stu-id="1af2b-211">Using this option may, however, lead to broken references in the project.</span></span> <span data-ttu-id="1af2b-212">V takových případech budete muset [znovu nainstalujte tyto další balíčky](../consume-packages/reinstalling-and-updating-packages.md).</span><span class="sxs-lookup"><span data-stu-id="1af2b-212">In such cases, you may need to [reinstall those other packages](../consume-packages/reinstalling-and-updating-packages.md).</span></span>