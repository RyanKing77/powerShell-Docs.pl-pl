---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Praca z folderami plików i kluczy rejestru"
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: 22a2390686659033bfd8b02a151b3397cfd46a22
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="9e8cc-103">Praca z plików, folderów i kluczy rejestru</span><span class="sxs-lookup"><span data-stu-id="9e8cc-103">Working With Files, Folders and Registry Keys</span></span>
<span data-ttu-id="9e8cc-104">Program Windows PowerShell korzysta rzeczownikiem **elementu** do odwoływania się do elementów na dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="9e8cc-105">Podczas pracy z dostawcą programu Windows PowerShell w systemie plików **elementu** może być pliku, folderu lub dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="9e8cc-106">Wyświetlanie i Praca z tych elementów jest krytyczne zadanie podstawowe w większość ustawień administracyjnych, więc chcemy tych zadań szczegółowo omówiono w nim.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="9e8cc-107">Wyliczanie plików, folderów i kluczy rejestru (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="9e8cc-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>
<span data-ttu-id="9e8cc-108">Ponieważ pobierania kolekcję elementów z określonej lokalizacji jest takie typowe zadania, **Get-ChildItem** polecenia cmdlet zaprojektowane z myślą o zwraca wszystkie elementy znalezione w kontenerze, takie jak folder.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="9e8cc-109">Jeśli chcesz przywrócić wszystkie pliki i foldery, które znajdują się bezpośrednio w folderze C:\\systemu Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="9e8cc-110">Listę wygląda podobnie do będzie widoczna po wprowadzeniu **dir** w **Cmd.exe**, lub **ls** polecenie w powłoce poleceń systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="9e8cc-111">Listy bardzo skomplikowane, można wykonać przy użyciu parametrów **Get-ChildItem** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="9e8cc-112">Przedstawiono kilka scenariuszy dalej.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="9e8cc-113">Można sprawdzić składnię **Get-ChildItem** polecenia cmdlet, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```
PS> Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="9e8cc-114">Te parametry można mieszany i dopasować do pobrania danych wyjściowych wysoce dostosowane.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="9e8cc-115">Wyświetlanie wszystkich elementów zawartych (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="9e8cc-115">Listing all Contained Items (-Recurse)</span></span>
<span data-ttu-id="9e8cc-116">Aby wyświetlić elementów znajduje się w folderze systemu Windows i wszystkie elementy, które są zawarte w podfolderach, użyj **Recurse** parametr **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="9e8cc-117">Listę Wyświetla wszystkie elementy w folderze systemu Windows i elementów w jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="9e8cc-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="9e8cc-119">Filtrowanie elementów według nazwy (-Name)</span><span class="sxs-lookup"><span data-stu-id="9e8cc-119">Filtering Items by Name (-Name)</span></span>
<span data-ttu-id="9e8cc-120">Aby wyświetlić tylko nazwy elementów, użyj **nazwa** parametr **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="9e8cc-121">Wymuś wyświetlanie ukrytych elementów (-Force)</span><span class="sxs-lookup"><span data-stu-id="9e8cc-121">Forcibly Listing Hidden Items (-Force)</span></span>
<span data-ttu-id="9e8cc-122">Elementy, które nie są zwykle widoczne w Eksploratorze plików lub Cmd.exe nie są wyświetlane w danych wyjściowych **Get-ChildItem** polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="9e8cc-123">Aby wyświetlić ukryte elementy, użyj **życie** parametr **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="9e8cc-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-124">For example:</span></span>

```
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="9e8cc-125">Ten parametr jest o nazwie Force, ponieważ wymuszanie można zastąpić normalne zachowanie **Get-ChildItem** polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="9e8cc-126">Wymuś jest powszechnie używany parametr, który wymusza akcję, która zwykle nie może wykonać polecenia cmdlet, mimo że nie będzie wykonywać żadnych czynności, które obniża zabezpieczeń systemu.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="9e8cc-127">Zgodne z nazwami elementów z symbolami wieloznacznymi</span><span class="sxs-lookup"><span data-stu-id="9e8cc-127">Matching Item Names with Wildcards</span></span>
<span data-ttu-id="9e8cc-128">**Get-ChildItem** polecenie akceptuje symbole wieloznaczne w ścieżce elementów do listy.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="9e8cc-129">Ponieważ wieloznacznych jest obsługiwany przez aparat programu Windows PowerShell, wszystkie polecenia cmdlet, które akceptuje symboli wieloznacznych używają tego samego notacji i ma takie samo zachowanie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="9e8cc-130">Obejmuje notacji symbolu wieloznacznego środowiska Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="9e8cc-131">Znak gwiazdki (\*) dopasowuje dowolny znak zero lub więcej wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="9e8cc-132">Znak zapytania (?) odpowiada dokładnie jeden znak.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="9e8cc-133">Lewy nawias (\[) znaków i znak prawego nawiasu (]) otaczające zestaw znaków do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="9e8cc-134">Oto kilka przykładów działania Specyfikacja symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="9e8cc-135">Aby znaleźć wszystkie pliki w katalogu systemu Windows wraz z sufiksem **log** i dokładnie pięć znaków w nazwie podstawowej, wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="9e8cc-136">Aby znaleźć wszystkie pliki, które zaczynają się od litery **x** w katalogu systemu Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="9e8cc-137">Aby znaleźć wszystkie pliki, których nazwy zaczynają się od **x** lub **z**, wpisz:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="9e8cc-138">Wykluczanie elementów (— wyklucz)</span><span class="sxs-lookup"><span data-stu-id="9e8cc-138">Excluding Items (-Exclude)</span></span>
<span data-ttu-id="9e8cc-139">Można wykluczyć określone elementy za pomocą **wykluczyć** parametr Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="9e8cc-140">Dzięki temu można wykonywać złożonych filtrowanie w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="9e8cc-141">Na przykład załóżmy, że próbujesz odnaleźć biblioteki DLL usługi Czas systemu Windows w folderze System32, a wszystko, co może zapamiętać o nazwę biblioteki DLL jest zaczyna się od litery "W" i ma w nim "32".</span><span class="sxs-lookup"><span data-stu-id="9e8cc-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="9e8cc-142">Wyrażenie, takich jak **w\&#42; 32\&#42;. biblioteki dll** znajdziesz wszystkie biblioteki dll, które spełniają warunki, ale może również zwrócić Windows 95 i zgodności z systemem Windows 16-bitowych bibliotek DLL, które obejmują "95" lub "16" w ich nazwy.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="9e8cc-143">W przypadku pominięcia pliki, które nie ma żadnej z tych numerów w nazwach przy użyciu **wykluczyć** parametru za pomocą wzorca  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

<pre>PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*
Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll</pre>

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="9e8cc-144">Mieszanie Get-ChildItem parametrów</span><span class="sxs-lookup"><span data-stu-id="9e8cc-144">Mixing Get-ChildItem Parameters</span></span>
<span data-ttu-id="9e8cc-145">Można użyć kilku parametrów **Get-ChildItem** polecenia cmdlet w tym samym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="9e8cc-146">Przed mieszać parametrów, upewnij się, że rozumiesz wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="9e8cc-147">Na przykład poniższe polecenie zwraca nie zwróciło żadnych wyników:</span><span class="sxs-lookup"><span data-stu-id="9e8cc-147">For example, the following command returns no results:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="9e8cc-148">Nie ma żadnych wyników, nawet jeśli istnieją dwa pliki dll, które zaczynają się od litery "z" w folderze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="9e8cc-149">Ponieważ firma Microsoft określony jako część ścieżki symbolu wieloznacznego nie zwrócono żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="9e8cc-150">Mimo że polecenie to cykliczne, **Get-ChildItem** polecenia cmdlet ograniczone elementy do tych, które znajdują się w folderze systemu Windows z nazwami kończą się ciągiem "dll".</span><span class="sxs-lookup"><span data-stu-id="9e8cc-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="9e8cc-151">Aby określić cykliczne wyszukiwanie plików, których nazwy zgodne ze wzorcem specjalne, użyj **-obejmują** parametru.</span><span class="sxs-lookup"><span data-stu-id="9e8cc-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```

