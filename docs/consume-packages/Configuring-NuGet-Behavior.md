---
title: Konfigurace chování NuGet
description: NuGet.Config soubory řídit chování NuGet globálně i na jednotlivých projektů a jsou upraveny pomocí příkazu config nuget.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 10/25/2017
ms.topic: conceptual
ms.openlocfilehash: 02d9c0b20d3660d94ac4d80b7325f747675b0c12
ms.sourcegitcommit: 00c4c809c69c16fcf4d81012eb53ea22f0691d0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2018
---
# <a name="configuring-nuget-behavior"></a><span data-ttu-id="ae01e-103">Konfigurace chování NuGet</span><span class="sxs-lookup"><span data-stu-id="ae01e-103">Configuring NuGet behavior</span></span>

<span data-ttu-id="ae01e-104">Chování NuGet doprovází Akumulovaná nastavení v jedné nebo více `NuGet.Config` soubory (XML), které může existovat projektu - uživatel- a úrovně platná pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="ae01e-104">NuGet's behavior is driven by the accumulated settings in one or more `NuGet.Config` (XML) files that can exist at project-, user-, and computer-wide levels.</span></span> <span data-ttu-id="ae01e-105">Globální konfiguraci `NuGetDefaults.Config` soubor také konkrétně nakonfiguruje zdroje balíčků.</span><span class="sxs-lookup"><span data-stu-id="ae01e-105">A global `NuGetDefaults.Config` file also specifically configures package sources.</span></span> <span data-ttu-id="ae01e-106">Nastavení se vztahují na všechny příkazy vydané v rozhraní příkazového řádku, konzoly Správce balíčků a uživatelského rozhraní Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="ae01e-106">Settings apply to all commands issued in the CLI, the Package Manager Console, and the Package Manager UI.</span></span>

## <a name="config-file-locations-and-uses"></a><span data-ttu-id="ae01e-107">Umístění konfiguračního souboru a používá</span><span class="sxs-lookup"><span data-stu-id="ae01e-107">Config file locations and uses</span></span>

| <span data-ttu-id="ae01e-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ae01e-108">Scope</span></span> | <span data-ttu-id="ae01e-109">Umístění souboru NuGet.Config</span><span class="sxs-lookup"><span data-stu-id="ae01e-109">NuGet.Config file location</span></span> | <span data-ttu-id="ae01e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ae01e-110">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="ae01e-111">Projekt</span><span class="sxs-lookup"><span data-stu-id="ae01e-111">Project</span></span> | <span data-ttu-id="ae01e-112">Aktuální složce (neboli složky projektu) nebo libovolné složky až kořenové jednotce.</span><span class="sxs-lookup"><span data-stu-id="ae01e-112">Current folder (aka Project folder) or any folder up to the drive root.</span></span>| <span data-ttu-id="ae01e-113">Ve složce projektu nastavení platí pouze pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="ae01e-113">In a project folder, settings apply only to that project.</span></span> <span data-ttu-id="ae01e-114">V nadřazené složky, které obsahují více projektů podsložky nastavení se vztahují na všechny projekty v těchto podsložky.</span><span class="sxs-lookup"><span data-stu-id="ae01e-114">In parent folders that contain multiple projects subfolders, settings apply to all projects in those subfolders.</span></span> |
| <span data-ttu-id="ae01e-115">Uživatel</span><span class="sxs-lookup"><span data-stu-id="ae01e-115">User</span></span> | <span data-ttu-id="ae01e-116">Windows: `%appdata%\NuGet\NuGet.Config`</span><span class="sxs-lookup"><span data-stu-id="ae01e-116">Windows: `%appdata%\NuGet\NuGet.Config`</span></span><br/><span data-ttu-id="ae01e-117">Mac/Linux: `~/.config/NuGet/NuGet.Config` nebo `~/.nuget/NuGet/NuGet.Config` (se liší podle operačního systému distribučního)</span><span class="sxs-lookup"><span data-stu-id="ae01e-117">Mac/Linux: `~/.config/NuGet/NuGet.Config` or `~/.nuget/NuGet/NuGet.Config` (varies by OS distribution)</span></span> | <span data-ttu-id="ae01e-118">Nastavení platí pro všechny operace, ale jsou přepsány jakékoli nastavení projektu.</span><span class="sxs-lookup"><span data-stu-id="ae01e-118">Settings apply to all operations, but are overridden by any project-level settings.</span></span> |
| <span data-ttu-id="ae01e-119">Počítače</span><span class="sxs-lookup"><span data-stu-id="ae01e-119">Computer</span></span> | <span data-ttu-id="ae01e-120">Windows: `%ProgramFiles(x86)%\NuGet\Config`</span><span class="sxs-lookup"><span data-stu-id="ae01e-120">Windows: `%ProgramFiles(x86)%\NuGet\Config`</span></span><br/><span data-ttu-id="ae01e-121">Mac/Linux: `$XDG_DATA_HOME`.</span><span class="sxs-lookup"><span data-stu-id="ae01e-121">Mac/Linux: `$XDG_DATA_HOME`.</span></span> <span data-ttu-id="ae01e-122">Pokud `$XDG_DATA_HOME` má hodnotu null nebo prázdná, `~/.local/share` nebo `/usr/local/share` se použije (se liší podle operačního systému distribučního)</span><span class="sxs-lookup"><span data-stu-id="ae01e-122">If `$XDG_DATA_HOME` is null or empty, `~/.local/share` or `/usr/local/share` will be used (varies by OS distribution)</span></span>  | <span data-ttu-id="ae01e-123">Nastavení platí pro všechny operace v počítači, ale jsou všechna nastavení na úrovni uživatele nebo projektu přepsat.</span><span class="sxs-lookup"><span data-stu-id="ae01e-123">Settings apply to all operations on the computer, but are overridden by any user- or project-level settings.</span></span> |

<span data-ttu-id="ae01e-124">Poznámky pro starší verze balíčku nuget:</span><span class="sxs-lookup"><span data-stu-id="ae01e-124">Notes for earlier versions of NuGet:</span></span>
- <span data-ttu-id="ae01e-125">NuGet 3.3 a dříve slouží `.nuget` složku pro nastavení celé řešení.</span><span class="sxs-lookup"><span data-stu-id="ae01e-125">NuGet 3.3 and earlier used a `.nuget` folder for solution-wide settings.</span></span> <span data-ttu-id="ae01e-126">Tento soubor není použit v NuGet 3.4 +.</span><span class="sxs-lookup"><span data-stu-id="ae01e-126">This file is not used in NuGet 3.4+.</span></span>
- <span data-ttu-id="ae01e-127">Pro NuGet 2.6 k 3.x, úrovni počítače konfiguračním souboru v systému Windows se nacházel v % ProgramData%\NuGet\Config [\\{IDE} [\\{Version} [\\{SKU}]]]\NuGet.Config, kde *{IDE}* může být  *Visual Studio*, *{Version}* verzi sady Visual Studio, jako byl *14.0*, a *{SKU}* je buď *komunity*, *Pro*, nebo *Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="ae01e-127">For NuGet 2.6 to 3.x, the computer-level config file on Windows was located in %ProgramData%\NuGet\Config[\\{IDE}[\\{Version}[\\{SKU}]]]\NuGet.Config, where *{IDE}* can be *VisualStudio*, *{Version}* was the Visual Studio version such as *14.0*, and *{SKU}* is either *Community*, *Pro*, or *Enterprise*.</span></span> <span data-ttu-id="ae01e-128">Migrace nastavení na NuGet 4.0 +, jednoduše zkopírujte do konfiguračního souboru % ProgramFiles(x86) % \NuGet\Config. V systému Linux, byl tento předchozího umístění /etc/opt a v systému Mac, Library/Application Support.</span><span class="sxs-lookup"><span data-stu-id="ae01e-128">To migrate settings to NuGet 4.0+, simply copy the config file to %ProgramFiles(x86)%\NuGet\Config. On Linux, this previous location was /etc/opt, and on Mac, /Library/Application Support.</span></span>

## <a name="changing-config-settings"></a><span data-ttu-id="ae01e-129">Změna nastavení konfigurace</span><span class="sxs-lookup"><span data-stu-id="ae01e-129">Changing config settings</span></span>

<span data-ttu-id="ae01e-130">A `NuGet.Config` soubor je jednoduchý textový soubor XML obsahující dvojice klíč/hodnota, jak je popsáno v [nastavení konfigurace NuGet](../reference/nuget-config-file.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ae01e-130">A `NuGet.Config` file is a simple XML text file containing key/value pairs as described in the [NuGet Configuration Settings](../reference/nuget-config-file.md) topic.</span></span>

<span data-ttu-id="ae01e-131">Nastavení se spravují pomocí rozhraní příkazového řádku NuGet [příkazu config](../tools/cli-ref-config.md):</span><span class="sxs-lookup"><span data-stu-id="ae01e-131">Settings are managed using the NuGet CLI [config command](../tools/cli-ref-config.md):</span></span>
- <span data-ttu-id="ae01e-132">Ve výchozím nastavení provedení změn na úrovni uživatele konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ae01e-132">By default, changes are made to the user-level config file.</span></span>
- <span data-ttu-id="ae01e-133">Chcete-li změnit nastavení v jiném souboru, použijte `-configFile` přepínače.</span><span class="sxs-lookup"><span data-stu-id="ae01e-133">To change settings in a different file, use the `-configFile` switch.</span></span> <span data-ttu-id="ae01e-134">Soubory v tomto případě můžete použít libovolný název souboru.</span><span class="sxs-lookup"><span data-stu-id="ae01e-134">In this case files can use any filename.</span></span>
- <span data-ttu-id="ae01e-135">Klíče jsou vždy velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="ae01e-135">Keys are always case sensitive.</span></span>
- <span data-ttu-id="ae01e-136">Chcete-li změnit nastavení v souboru nastavení na úrovni počítače se vyžaduje zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ae01e-136">Elevation is required to change settings in the computer-level settings file.</span></span>

> [!Warning]
> <span data-ttu-id="ae01e-137">I když můžete upravit soubor v každém textovém editoru, NuGet (v3.4.3 a novější) bezobslužně ignoruje celý konfigurační soubor, pokud obsahuje poškozený obsah XML (Neshoda značek, neplatné znaky uvozovek atd.).</span><span class="sxs-lookup"><span data-stu-id="ae01e-137">Although you can modify the file in any text editor, NuGet (v3.4.3 and later) silently ignores the entire configuration file if it contains malformed XML (mismatched tags, invalid quotation marks, etc.).</span></span> <span data-ttu-id="ae01e-138">To je důvod, proč je vhodnější ke správě nastavení pomocí `nuget config`.</span><span class="sxs-lookup"><span data-stu-id="ae01e-138">This is why it's preferable to manage setting using `nuget config`.</span></span>

### <a name="setting-a-value"></a><span data-ttu-id="ae01e-139">Nastavení hodnoty</span><span class="sxs-lookup"><span data-stu-id="ae01e-139">Setting a value</span></span>

<span data-ttu-id="ae01e-140">Windows:</span><span class="sxs-lookup"><span data-stu-id="ae01e-140">Windows:</span></span>

```cli
# Set repositoryPath in the user-level config file
nuget config -set repositoryPath=c:\packages 

# Set repositoryPath in project-level files
nuget config -set repositoryPath=c:\packages -configfile c:\my.Config
nuget config -set repositoryPath=c:\packages -configfile .\myApp\NuGet.Config

# Set repositoryPath in the computer-level file (requires elevation)
nuget config -set repositoryPath=c:\packages -configfile %ProgramFiles(x86)%\NuGet\Config\NuGet.Config
```

<span data-ttu-id="ae01e-141">Mac/Linux:</span><span class="sxs-lookup"><span data-stu-id="ae01e-141">Mac/Linux:</span></span>

```cli
# Set repositoryPath in the user-level config file
nuget config -set repositoryPath=/home/packages 

# Set repositoryPath in project-level files
nuget config -set repositoryPath=/home/projects/packages -configfile /home/my.Config
nuget config -set repositoryPath=/home/packages -configfile home/myApp/NuGet.Config

# Set repositoryPath in the computer-level file (requires elevation)
nuget config -set repositoryPath=/home/packages -configfile $XDG_DATA_HOME/NuGet.Config
```

> [!Note]
> <span data-ttu-id="ae01e-142">V NuGet 3.4 a novější proměnné prostředí v jakákoli hodnota, můžete použít jako v `repositoryPath=%PACKAGEHOME%` (Windows) a `repositoryPath=%PACKAGEHOME` (Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="ae01e-142">In NuGet 3.4 and later you can use environment variables in any value, as in `repositoryPath=%PACKAGEHOME%` (Windows) and `repositoryPath=%PACKAGEHOME` (Mac/Linux).</span></span>

### <a name="removing-a-value"></a><span data-ttu-id="ae01e-143">Odebrání hodnotu</span><span class="sxs-lookup"><span data-stu-id="ae01e-143">Removing a value</span></span>

<span data-ttu-id="ae01e-144">Odebrat hodnotu, zadejte klíč s prázdnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ae01e-144">To remove a value, specify a key with an empty value.</span></span>

```cli
# Windows
nuget config -set repositoryPath= -configfile c:\my.Config

# Mac/Linux
nuget config -set repositoryPath= -configfile /home/my.Config
```

### <a name="creating-a-new-config-file"></a><span data-ttu-id="ae01e-145">Vytvoření nového souboru config</span><span class="sxs-lookup"><span data-stu-id="ae01e-145">Creating a new config file</span></span>

<span data-ttu-id="ae01e-146">Zkopírujte šablony níže do nového souboru a pak použijte `nuget config -configFile <filename>` nastavit hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ae01e-146">Copy the template below into the new file and then use `nuget config -configFile <filename>` to set values:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
</configuration>
```

## <a name="how-settings-are-applied"></a><span data-ttu-id="ae01e-147">Jak se používají nastavení</span><span class="sxs-lookup"><span data-stu-id="ae01e-147">How settings are applied</span></span>

<span data-ttu-id="ae01e-148">Více `NuGet.Config` soubory můžete ukládat nastavení v různých umístěních, tak, aby se vztahují na jeden projekt, skupinu projektů nebo všechny projekty.</span><span class="sxs-lookup"><span data-stu-id="ae01e-148">Multiple `NuGet.Config` files allow you to store settings in different locations so that they apply to a single project, a group of projects, or all projects.</span></span> <span data-ttu-id="ae01e-149">Toto nastavení se souhrnně platí pro všechny operace NuGet vyvolat z příkazového řádku nebo ze sady Visual Studio, s nastavením, které existují "nejbližší" do projektu nebo aktuální složce trvá prioritu.</span><span class="sxs-lookup"><span data-stu-id="ae01e-149">These settings collectively apply to any NuGet operation invoked from the command line or from Visual Studio, with settings that exist "closest" to a project or the current folder taking precedence.</span></span>

<span data-ttu-id="ae01e-150">Konkrétně NuGet načte nastavení z jiné konfigurační soubory v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="ae01e-150">Specifically, NuGet loads settings from the different config files in the following order:</span></span>

1. <span data-ttu-id="ae01e-151">[NuGetDefaults.Config souboru](#nuget-defaults-file), který obsahuje nastavení týkající se pouze zdroje balíčků.</span><span class="sxs-lookup"><span data-stu-id="ae01e-151">The [NuGetDefaults.Config file](#nuget-defaults-file), which contains settings related only to package sources.</span></span>
1. <span data-ttu-id="ae01e-152">Soubor úrovni počítačů.</span><span class="sxs-lookup"><span data-stu-id="ae01e-152">The computer-level file.</span></span>
1. <span data-ttu-id="ae01e-153">Soubor úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="ae01e-153">The user-level file.</span></span>
1. <span data-ttu-id="ae01e-154">Zadaný soubor s `-configFile`.</span><span class="sxs-lookup"><span data-stu-id="ae01e-154">The file specified with `-configFile`.</span></span>
1. <span data-ttu-id="ae01e-155">Soubory, které jsou v každé složky v cestě z kořenového adresáře disku do aktuální složky (kde je volána nuget.exe nebo složku obsahující projekt Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="ae01e-155">Files found in every folder in the path from the drive root to the current folder (where nuget.exe is invoked or the folder containing the Visual Studio project).</span></span> <span data-ttu-id="ae01e-156">Například pokud je příkaz je vyvolána v c:\A\B\C, NuGet vyhledá a načte konfigurační soubory v c:\, pak c:\A, pak c:\A\B a nakonec c:\A\B\C.</span><span class="sxs-lookup"><span data-stu-id="ae01e-156">For example, if a command is invoked in c:\A\B\C, NuGet looks for and loads config files in c:\, then c:\A, then c:\A\B, and finally c:\A\B\C.</span></span>

<span data-ttu-id="ae01e-157">Jako NuGet najde nastavení v těchto souborech, se používají takto:</span><span class="sxs-lookup"><span data-stu-id="ae01e-157">As NuGet finds settings in these files, they are applied as follows:</span></span>

1. <span data-ttu-id="ae01e-158">U jedné položky elementů NuGet nahradit hodnotou dřív nalezený pro stejný klíč.</span><span class="sxs-lookup"><span data-stu-id="ae01e-158">For single-item elements, NuGet replaced any previously-found value for the same key.</span></span> <span data-ttu-id="ae01e-159">To znamená, že nastavení, které jsou "nejbližší" do aktuální složky nebo projektu přepsat všechny další nalezeny dříve.</span><span class="sxs-lookup"><span data-stu-id="ae01e-159">This means that settings that are "closest" to the current folder or project override any others found earlier.</span></span> <span data-ttu-id="ae01e-160">Například `defaultPushSource` nastavení v `NuGetDefaults.Config` je přepsat, pokud existuje v jiné konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="ae01e-160">For example, the `defaultPushSource` setting in `NuGetDefaults.Config` is overridden if it exists in any other config file.</span></span>

1. <span data-ttu-id="ae01e-161">Pro elementy v kolekci (například `<packageSources>`), NuGet kombinuje hodnoty z všechny konfigurační soubory do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="ae01e-161">For collection elements (such as `<packageSources>`), NuGet combines the values from all configuration files into a single collection.</span></span>

1. <span data-ttu-id="ae01e-162">Když `<clear />` je k dispozici pro daný uzel NuGet ignoruje dříve definovaném konfigurační hodnoty pro tento uzel.</span><span class="sxs-lookup"><span data-stu-id="ae01e-162">When `<clear />` is present for a given node, NuGet ignores previously defined configuration values for that node.</span></span>

### <a name="settings-walkthrough"></a><span data-ttu-id="ae01e-163">Postup nastavení</span><span class="sxs-lookup"><span data-stu-id="ae01e-163">Settings walkthrough</span></span>

<span data-ttu-id="ae01e-164">Může se stát, že máte následující strukturu složek na dvě samostatné jednotky:</span><span class="sxs-lookup"><span data-stu-id="ae01e-164">Let's say you have the following folder structure on two separate drives:</span></span>

    disk_drive_1
        User
    disk_drive_2
       Project1
         Source
       Project2
         Source
       tmp

<span data-ttu-id="ae01e-165">Budete mít čtyři `NuGet.Config` soubory v následujících umístěních s daný obsah.</span><span class="sxs-lookup"><span data-stu-id="ae01e-165">You then have four `NuGet.Config` files in the following locations with the given content.</span></span> <span data-ttu-id="ae01e-166">(Soubor úrovni počítače není zahrnutý v tomto příkladu, ale budou chovat podobně do souboru úrovni uživatele.)</span><span class="sxs-lookup"><span data-stu-id="ae01e-166">(The computer-level file is not included in this example, but would behave similarly to the user-level file.)</span></span>

<span data-ttu-id="ae01e-167">Soubor A. individuální souborů, (`%appdata%\NuGet\NuGet.Config` v systému Windows, `~/.config/NuGet/NuGet.Config` na Mac/Linux):</span><span class="sxs-lookup"><span data-stu-id="ae01e-167">File A. User-level file, (`%appdata%\NuGet\NuGet.Config` on Windows, `~/.config/NuGet/NuGet.Config` on Mac/Linux):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <activePackageSource>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
    </activePackageSource>
</configuration>
```

<span data-ttu-id="ae01e-168">Soubor B. disk_drive_2/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="ae01e-168">File B. disk_drive_2/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <add key="repositoryPath" value="disk_drive_2/tmp" />
    </config>
    <packageRestore>
        <add key="enabled" value="True" />
    </packageRestore>
</configuration>
```

<span data-ttu-id="ae01e-169">File C. disk_drive_2/Project1/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="ae01e-169">File C. disk_drive_2/Project1/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <add key="repositoryPath" value="External/Packages" />
        <add key="defaultPushSource" value="https://MyPrivateRepo/ES/api/v2/package" />
    </config>
    <packageSources>
        <clear /> <!-- ensure only the sources defined below are used -->
        <add key="MyPrivateRepo - ES" value="https://MyPrivateRepo/ES/nuget" />
    </packageSources>
</configuration>
```

<span data-ttu-id="ae01e-170">File D. disk_drive_2/Project2/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="ae01e-170">File D. disk_drive_2/Project2/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <packageSources>
        <!-- Add this repository to the list of available repositories -->
        <add key="MyPrivateRepo - DQ" value="https://MyPrivateRepo/DQ/nuget" />
    </packageSources>
</configuration>
```

<span data-ttu-id="ae01e-171">NuGet potom načte a aplikuje nastavení následujícím způsobem v závislosti na tom, kde je možné:</span><span class="sxs-lookup"><span data-stu-id="ae01e-171">NuGet then loads and applies settings as follows, depending on where it's invoked:</span></span>

- <span data-ttu-id="ae01e-172">**Volat z disk_drive_1 či uživatelů**: se používá pouze výchozí úložiště uvedené v souboru konfigurace na uživatelské úrovni (A), protože se jedná o jediný soubor na disk_drive_1 nalezen.</span><span class="sxs-lookup"><span data-stu-id="ae01e-172">**Invoked from disk_drive_1/users**: Only the default repository listed in the user-level configuration file (A) is used, because that's the only file found on disk_drive_1.</span></span>

- <span data-ttu-id="ae01e-173">**Volat z disk_drive_2 / nebo disk_drive_/tmp**: nejdřív načtení individuální souboru (A) a NuGet přejde do kořenového adresáře disk_drive_2 a najde soubor (B).</span><span class="sxs-lookup"><span data-stu-id="ae01e-173">**Invoked from disk_drive_2/ or disk_drive_/tmp**: The user-level file (A) is loaded first, then NuGet goes to the root of disk_drive_2 and finds file (B).</span></span> <span data-ttu-id="ae01e-174">NuGet rovněž vyhledává konfigurační soubor v TMP však nebyl nalezen jeden.</span><span class="sxs-lookup"><span data-stu-id="ae01e-174">NuGet also looks for a configuration file in /tmp but does not find one.</span></span> <span data-ttu-id="ae01e-175">V důsledku toho se používá výchozí úložiště na nuget.org, je povoleno obnovení balíčků a balíčky získat rozšířit disk_drive_2/tmp.</span><span class="sxs-lookup"><span data-stu-id="ae01e-175">As a result, the default repository on nuget.org is used, package restore is enabled, and packages get expanded in disk_drive_2/tmp.</span></span>

- <span data-ttu-id="ae01e-176">**Volána z disk_drive_2/Project1 nebo disk_drive_2/Project1/zdroje**: nejdřív načtení individuální souboru (A) a potom NuGet načítání souboru (B) z kořenové složky disk_drive_2, za nímž následuje souboru (C).</span><span class="sxs-lookup"><span data-stu-id="ae01e-176">**Invoked from disk_drive_2/Project1 or disk_drive_2/Project1/Source**: The user-level file (A) is loaded first, then NuGet loads file (B) from the root of disk_drive_2, followed by file (C).</span></span> <span data-ttu-id="ae01e-177">Nastavení v (C) přepíšou nastavení v (B) (A) a proto `repositoryPath` získat nainstalovanou balíčků je disk_drive_2/Project1/externí nebo balíčky místo *disk_drive_2/tmp*.</span><span class="sxs-lookup"><span data-stu-id="ae01e-177">Settings in (C) override those in (B) and (A), so the `repositoryPath` where packages get installed is disk_drive_2/Project1/External/Packages instead of *disk_drive_2/tmp*.</span></span> <span data-ttu-id="ae01e-178">Navíc vzhledem k tomu, že (C) vymaže `<packageSources>`, nuget.org již není k dispozici jako zdroj ponechat pouze `https://MyPrivateRepo/ES/nuget`.</span><span class="sxs-lookup"><span data-stu-id="ae01e-178">Also, because (C) clears `<packageSources>`, nuget.org is no longer available as a source leaving only `https://MyPrivateRepo/ES/nuget`.</span></span>

- <span data-ttu-id="ae01e-179">**Volána z disk_drive_2/projektu2 nebo disk_drive_2/projektu2/zdroje**: načtení individuální souboru (A) nejprve následuje soubor (B) a soubor (D).</span><span class="sxs-lookup"><span data-stu-id="ae01e-179">**Invoked from disk_drive_2/Project2 or disk_drive_2/Project2/Source**: The user-level file (A) is loaded first followed by file (B) and file (D).</span></span> <span data-ttu-id="ae01e-180">Protože `packageSources` není zaškrtnuto, obě `nuget.org` a `https://MyPrivateRepo/DQ/nuget` jsou k dispozici jako zdroje.</span><span class="sxs-lookup"><span data-stu-id="ae01e-180">Because `packageSources` is not cleared, both `nuget.org` and `https://MyPrivateRepo/DQ/nuget` are available as sources.</span></span> <span data-ttu-id="ae01e-181">Balíčky získat rozšířit disk_drive_2/tmp zadané v (B).</span><span class="sxs-lookup"><span data-stu-id="ae01e-181">Packages get expanded in disk_drive_2/tmp as specified in (B).</span></span>

## <a name="nuget-defaults-file"></a><span data-ttu-id="ae01e-182">Výchozí nastavení souboru NuGet</span><span class="sxs-lookup"><span data-stu-id="ae01e-182">NuGet defaults file</span></span>

<span data-ttu-id="ae01e-183">`NuGetDefaults.Config` Soubor existuje, můžete určit zdroje balíčků, ze kterých jsou nainstalované a aktualizovat balíčky a řídit výchozí cíl pro publikování balíčků s `nuget push`.</span><span class="sxs-lookup"><span data-stu-id="ae01e-183">The `NuGetDefaults.Config` file exists to specify package sources from which packages are installed and updated, and to control the default target for publishing packages with `nuget push`.</span></span> <span data-ttu-id="ae01e-184">Protože správci můžou pohodlně (například pomocí zásad skupiny) nasadit konzistentní `NuGetDefaults.Config` soubory na vývojáře a sestavení počítače, můžete zajistit, že všichni uživatelé v organizaci používá správný balíček zdroje místo nuget.org.</span><span class="sxs-lookup"><span data-stu-id="ae01e-184">Because administrators can conveniently (using Group Policy, for example) deploy consistent `NuGetDefaults.Config` files to developer and build machines, they can ensuring that everyone in the organization is using the correct package sources rather than nuget.org.</span></span>

> [!Important]
> <span data-ttu-id="ae01e-185">`NuGetDefaults.Config` Souboru nikdy způsobí, že zdroj balíčku, který se odeberou z konfigurace NuGet pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="ae01e-185">The `NuGetDefaults.Config` file never causes a package source to be removed from a developer's NuGet configuration.</span></span> <span data-ttu-id="ae01e-186">To znamená, pokud vývojář již použit NuGet a proto má zdroj balíčku nuget.org registrován, nebude odebraný po vytvoření `NuGetDefaults.Config` souboru.</span><span class="sxs-lookup"><span data-stu-id="ae01e-186">That means if the developer has already used NuGet and therefore has the nuget.org package source registered, it won't be removed after the creation of a `NuGetDefaults.Config` file.</span></span>
>
> <span data-ttu-id="ae01e-187">Kromě toho, ani `NuGetDefaults.Config` ani jiným mechanismem v NuGet můžete zabránit přístupu do zdroje balíčků jako nuget.org. Pokud organizace chce blokovat takový přístup, použijte mnohem jiným způsobem, jako jsou brány firewall tak.</span><span class="sxs-lookup"><span data-stu-id="ae01e-187">Furthermore, neither `NuGetDefaults.Config` nor any other mechanism in NuGet can prevent access to package sources like nuget.org. If an organization wishes to block such access, it much use other means such as firewalls to do so.</span></span>

### <a name="nugetdefaultsconfig-location"></a><span data-ttu-id="ae01e-188">NuGetDefaults.Config umístění</span><span class="sxs-lookup"><span data-stu-id="ae01e-188">NuGetDefaults.Config location</span></span>

<span data-ttu-id="ae01e-189">Následující tabulka popisuje, kde `NuGetDefaults.Config` souboru by měly být uložené v závislosti na cílový operační systém:</span><span class="sxs-lookup"><span data-stu-id="ae01e-189">The following table describes where the `NuGetDefaults.Config` file should be stored, depending on the target OS:</span></span>

| <span data-ttu-id="ae01e-190">Platforma operačního systému</span><span class="sxs-lookup"><span data-stu-id="ae01e-190">OS Platform</span></span>  | <span data-ttu-id="ae01e-191">NuGetDefaults.Config umístění</span><span class="sxs-lookup"><span data-stu-id="ae01e-191">NuGetDefaults.Config Location</span></span> |
| --- | --- |
| <span data-ttu-id="ae01e-192">Windows</span><span class="sxs-lookup"><span data-stu-id="ae01e-192">Windows</span></span>      | <span data-ttu-id="ae01e-193">**Visual Studio 2017 nebo NuGet 4.x+:** `%ProgramFiles(x86)%\NuGet\Config`</span><span class="sxs-lookup"><span data-stu-id="ae01e-193">**Visual Studio 2017 or NuGet 4.x+:** `%ProgramFiles(x86)%\NuGet\Config`</span></span> <br /><span data-ttu-id="ae01e-194">**Visual Studio 2015 a starší nebo NuGet 3.x a dříve:** `%PROGRAMDATA%\NuGet`</span><span class="sxs-lookup"><span data-stu-id="ae01e-194">**Visual Studio 2015 and earlier or NuGet 3.x and earlier:** `%PROGRAMDATA%\NuGet`</span></span> |
| <span data-ttu-id="ae01e-195">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="ae01e-195">Mac/Linux</span></span>    | <span data-ttu-id="ae01e-196">`$XDG_DATA_HOME` (obvykle `~/.local/share` nebo `/usr/local/share`, v závislosti na distribuce operačního systému)</span><span class="sxs-lookup"><span data-stu-id="ae01e-196">`$XDG_DATA_HOME` (typically `~/.local/share` or `/usr/local/share`, depending on OS distribution)</span></span>|

### <a name="nugetdefaultsconfig-settings"></a><span data-ttu-id="ae01e-197">Nastavení NuGetDefaults.Config</span><span class="sxs-lookup"><span data-stu-id="ae01e-197">NuGetDefaults.Config settings</span></span>

- <span data-ttu-id="ae01e-198">`packageSources`: Tato kolekce nemá stejný význam jako `packageSources` v regulárním konfigurační soubory a určí výchozí zdroje.</span><span class="sxs-lookup"><span data-stu-id="ae01e-198">`packageSources`: this collection has the same meaning as `packageSources` in regular config files and specifies the default sources.</span></span> <span data-ttu-id="ae01e-199">NuGet používá zdroje v pořadí při instalaci nebo aktualizaci balíčků v projektech pomocí `packages.config` formátu správy.</span><span class="sxs-lookup"><span data-stu-id="ae01e-199">NuGet uses the sources in order when installing or updating packages in projects using the `packages.config` management format.</span></span> <span data-ttu-id="ae01e-200">Pro projekty formátu PackageReference NuGet nejprve používá místní zdroje a pak zdroje v síťové sdílené složky a zdrojů HTTP, bez ohledu na pořadí v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="ae01e-200">For projects using the PackageReference format, NuGet uses local sources first, then sources on network shares, then HTTP sources, regardless of the order in the configuration files.</span></span> <span data-ttu-id="ae01e-201">NuGet vždy ignoruje pořadí zdrojů s operací obnovení.</span><span class="sxs-lookup"><span data-stu-id="ae01e-201">NuGet always ignores the order of sources with restore operations.</span></span>

- <span data-ttu-id="ae01e-202">`disabledPackageSources`: Tato kolekce také nemá stejný význam jako v `NuGet.Config` soubory, kde každý ovlivněných zdroj uvedené podle jeho název a hodnotu true nebo false, která určuje, zda je zakázána.</span><span class="sxs-lookup"><span data-stu-id="ae01e-202">`disabledPackageSources`: this collection also has the same meaning as in `NuGet.Config` files, where each affected source is listed by its name and a true/false value indicating whether it's disabled.</span></span> <span data-ttu-id="ae01e-203">To umožňuje zdroj název a adresu URL zůstat v `packageSources` bez nutnosti ho ve výchozím nastavení zapnuto.</span><span class="sxs-lookup"><span data-stu-id="ae01e-203">This allows the source name and URL to remain in `packageSources` without having it turned on by default.</span></span> <span data-ttu-id="ae01e-204">Jednotlivé vývojáři mohou pak znovu povolit zdroj nastavením hodnoty na zdroji na hodnotu false v jiných `NuGet.Config` soubory bez nutnosti znovu najít správnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ae01e-204">Individual developers can then re-enable the source by setting the source's value to false in other `NuGet.Config` files without having to find the correct URL again.</span></span> <span data-ttu-id="ae01e-205">To je užitečné k poskytování vývojářům úplný seznam adres URL vnitřní zdroj pro organizaci při povolování pouze jednotlivé team zdroje ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ae01e-205">This is also useful to supply developers with a full list of internal source URLs for an organization while enabling only an individual team's source by default.</span></span>

- <span data-ttu-id="ae01e-206">`defaultPushSource`: Určuje výchozí cíl pro `nuget push` operace, přepsání předdefinovaných výchozí nuget.org. Správci mohou nasadit toto nastavení, aby se zabránilo publikování interní balíčky do veřejné nuget.org omylem odstraněný, jako vývojáři, konkrétně musí používat `nuget push -Source` publikovat do nuget.org.</span><span class="sxs-lookup"><span data-stu-id="ae01e-206">`defaultPushSource`: specifies the default target for `nuget push` operations, overriding the built-in default of nuget.org. Administrators can deploy this setting to avoid publishing internal packages to the public nuget.org by accident, as developers specifically need to use `nuget push -Source` to publish to nuget.org.</span></span>

### <a name="example-nugetdefaultsconfig-and-application"></a><span data-ttu-id="ae01e-207">Příklad NuGetDefaults.Config a aplikací</span><span class="sxs-lookup"><span data-stu-id="ae01e-207">Example NuGetDefaults.Config and application</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!-- defaultPushSource key works like the 'defaultPushSource' key of NuGet.Config files. -->
    <!-- This can be used by administrators to prevent accidental publishing of packages to nuget.org. -->
    <config>
        <add key="defaultPushSource" value="https://contoso.com/packages/" />
    </config>

    <!-- Default Package Sources; works like the 'packageSources' section of NuGet.Config files. -->
    <!-- This collection cannot be deleted or modified but can be disabled/enabled by users. -->
    <packageSources>
        <add key="Contoso Package Source" value="https://contoso.com/packages/" />
        <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
    </packageSources>

    <!-- Default Package Sources that are disabled by default. -->
    <!-- Works like the 'disabledPackageSources' section of NuGet.Config files. -->
    <!-- Sources cannot be modified or deleted either but can be enabled/disabled by users. -->
    <disabledPackageSources>
        <add key="nuget.org" value="true" />
    </disabledPackageSources>
</configuration>
```