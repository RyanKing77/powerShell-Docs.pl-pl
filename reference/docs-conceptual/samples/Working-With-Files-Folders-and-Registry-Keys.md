---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z folderami plików i kluczami rejestru
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086010"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="04d5f-103">Praca z plików, folderów i kluczy rejestru</span><span class="sxs-lookup"><span data-stu-id="04d5f-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="04d5f-104">Windows PowerShell korzysta z rzeczownikiem **elementu** do odwoływania się do elementów na dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04d5f-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="04d5f-105">Podczas pracy z dostawcą programu Windows PowerShell w systemie plików **elementu** może być pliku, folderu lub dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04d5f-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="04d5f-106">Lista i Praca z tych elementów jest krytyczne podstawowe zadania w większości ustawień administracyjnych, chcemy omówiono te zadania szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="04d5f-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="04d5f-107">Wyliczanie plików, folderów i kluczy rejestru (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="04d5f-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="04d5f-108">Ponieważ kolekcja elementów z określonej lokalizacji jest takiego typowe zadania, **Get-ChildItem** polecenia cmdlet jest zaprojektowany specjalnie w celu zwrócenie wszystkich elementów, które można znaleźć w kontenerze, takie jak folder.</span><span class="sxs-lookup"><span data-stu-id="04d5f-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="04d5f-109">Jeśli chcesz przywrócić wszystkie pliki i foldery, które znajdują się bezpośrednio z poziomu folderu C:\\Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="04d5f-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="04d5f-110">Listę wygląda podobnie do widoczne po wprowadzeniu **dir** polecenia w pliku **Cmd.exe**, lub **ls** polecenie w powłoce poleceń systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="04d5f-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="04d5f-111">Bardzo złożone oferty można wykonać przy użyciu parametrów **Get-ChildItem** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04d5f-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="04d5f-112">Przyjrzymy się kilka scenariuszy dalej.</span><span class="sxs-lookup"><span data-stu-id="04d5f-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="04d5f-113">Można zapoznać się ze składnią **Get-ChildItem** polecenia cmdlet, wpisując:</span><span class="sxs-lookup"><span data-stu-id="04d5f-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="04d5f-114">Te parametry można mieszać i dopasowane do uzyskania dopasowanego wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="04d5f-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="04d5f-115">Wyświetlanie wszystkich elementów znajdujących się (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="04d5f-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="04d5f-116">Aby wyświetlić elementy znajdujące się w folderze Windows i wszystkie elementy, które są zawarte w podfolderach, użyj **Recurse** parametru **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="04d5f-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="04d5f-117">Listę Wyświetla wszystkie elementy w folderze Windows i elementy w jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="04d5f-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="04d5f-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="04d5f-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="04d5f-119">Filtrując elementy według nazwy (-nazwa)</span><span class="sxs-lookup"><span data-stu-id="04d5f-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="04d5f-120">Aby wyświetlić tylko nazwy elementów, użyj **nazwa** parametru **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="04d5f-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="04d5f-121">Wymuś wyświetlanie ukrytych elementów (-Force)</span><span class="sxs-lookup"><span data-stu-id="04d5f-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="04d5f-122">Elementy, które są zwykle niewidoczne w Eksploratorze plików lub Cmd.exe nie są wyświetlane w danych wyjściowych **Get-ChildItem** polecenia.</span><span class="sxs-lookup"><span data-stu-id="04d5f-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="04d5f-123">Aby wyświetlić ukryte elementy, użyj **życie** parametru **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="04d5f-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="04d5f-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="04d5f-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="04d5f-125">Ten parametr nosi życie, ponieważ wymuszono można zastąpić normalnego zachowania **Get-ChildItem** polecenia.</span><span class="sxs-lookup"><span data-stu-id="04d5f-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="04d5f-126">Wymuś jest powszechnie używany parametr, który wymusza akcję, która nie wykona zazwyczaj polecenia cmdlet, mimo że nie będzie wykonywać żadnych działań, które obniża zabezpieczeń systemu.</span><span class="sxs-lookup"><span data-stu-id="04d5f-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="04d5f-127">Zgodne z nazwami elementów z symbolami wieloznacznymi</span><span class="sxs-lookup"><span data-stu-id="04d5f-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="04d5f-128">**Polecenie Get-ChildItem** polecenie akceptuje symbole wieloznaczne w ścieżce elementy do listy.</span><span class="sxs-lookup"><span data-stu-id="04d5f-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="04d5f-129">Ponieważ dopasowanie z symbolami wieloznacznymi jest obsługiwany przez aparatu programu Windows PowerShell, wszystkie polecenia cmdlet, które akceptuje symbole wieloznaczne Użyj takiej samej notacji i ma takie samo zachowanie pasujące.</span><span class="sxs-lookup"><span data-stu-id="04d5f-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="04d5f-130">Obejmuje notacji symbolu wieloznacznego programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="04d5f-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="04d5f-131">Gwiazdka (\*) dopasowuje zero lub więcej wystąpień dowolnego znaku.</span><span class="sxs-lookup"><span data-stu-id="04d5f-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="04d5f-132">Znak zapytania (?) dopasowuje dokładnie jeden znak.</span><span class="sxs-lookup"><span data-stu-id="04d5f-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="04d5f-133">Lewy nawias kwadratowy (\[) znaków prawego nawiasu (]) i otoczyć zestaw znaków, które mają zostać dopasowane.</span><span class="sxs-lookup"><span data-stu-id="04d5f-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="04d5f-134">Poniżej przedstawiono kilka przykładów sposobu działania Specyfikacja symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="04d5f-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="04d5f-135">Aby znaleźć wszystkie pliki w katalogu Windows wraz z sufiksem **.log** i dokładnie pięć znaków w nazwie podstawowej, wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="04d5f-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="04d5f-136">Aby znaleźć wszystkie pliki, które zaczynają się od litery **x** w katalogu Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="04d5f-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="04d5f-137">Aby znaleźć wszystkie pliki, których nazwy zaczynają się od **x** lub **z**, wpisz:</span><span class="sxs-lookup"><span data-stu-id="04d5f-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="04d5f-138">Wykluczanie elementów (— wyklucz)</span><span class="sxs-lookup"><span data-stu-id="04d5f-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="04d5f-139">Można wykluczyć konkretne elementy za pomocą **wykluczyć** parametr Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="04d5f-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="04d5f-140">Dzięki temu można wykonywać złożone filtrowanie w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="04d5f-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="04d5f-141">Na przykład załóżmy, że próbujesz odnaleźć biblioteki DLL Windows czasu usługi w folderze System32, a wszystko, czego należy pamiętać, o nazwie biblioteki DLL jest zaczyna się od "W" i zawiera "32".</span><span class="sxs-lookup"><span data-stu-id="04d5f-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="04d5f-142">Wyrażenie, takie jak **w\&#42; 32\&#42;. Biblioteka DLL** znajdzie wszystkie biblioteki dll, które spełniają warunki, ale może również zwrócić Windows 95 i zgodności Windows 16-bitowych bibliotek DLL, które zawierają "95" lub "16" w nazwach.</span><span class="sxs-lookup"><span data-stu-id="04d5f-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="04d5f-143">Możesz pominąć pliki, które nie ma żadnej z tych liczb w nazwach przy użyciu **wykluczyć** parametru za pomocą wzorca  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="04d5f-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

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
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="04d5f-144">Mieszanie polecenie Get-ChildItem parametrów</span><span class="sxs-lookup"><span data-stu-id="04d5f-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="04d5f-145">Można użyć kilku parametrów **Get-ChildItem** polecenia cmdlet w tym samym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="04d5f-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="04d5f-146">Zanim mieszać parametrów, upewnij się, że rozumiesz dopasowanie z symbolami wieloznacznymi.</span><span class="sxs-lookup"><span data-stu-id="04d5f-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="04d5f-147">Na przykład poniższe polecenie zwraca żadnych wyników:</span><span class="sxs-lookup"><span data-stu-id="04d5f-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="04d5f-148">Brak wyników, mimo że istnieją dwa pliki dll, które zaczynają się od litery "z" w folderze Windows.</span><span class="sxs-lookup"><span data-stu-id="04d5f-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="04d5f-149">Ponieważ firma Microsoft określona jako część ścieżki symbolu wieloznacznego nie zwrócono żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="04d5f-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="04d5f-150">Mimo że polecenie zostało rekursywny, **Get-ChildItem** polecenia cmdlet z ograniczeniami elementy do tych, które znajdują się w folderze Windows za pomocą nazwy kończące się ciągiem ".dll".</span><span class="sxs-lookup"><span data-stu-id="04d5f-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="04d5f-151">Aby określić wyszukiwania rekurencyjne dla plików, których nazwy odpowiadają wzorcowi specjalne, należy użyć **— obejmują** parametru.</span><span class="sxs-lookup"><span data-stu-id="04d5f-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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