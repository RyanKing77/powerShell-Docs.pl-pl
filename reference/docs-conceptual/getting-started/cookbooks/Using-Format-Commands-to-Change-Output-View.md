---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie widoku wyjściowego przy użyciu poleceń formatowania
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952787"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="253be-103">Zmienianie widoku wyjściowego przy użyciu poleceń formatowania</span><span class="sxs-lookup"><span data-stu-id="253be-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="253be-104">Środowisko Windows PowerShell jest zestaw poleceń cmdlet, które umożliwiają kontrolowanie właściwości, które są wyświetlane dla konkretnego obiektów.</span><span class="sxs-lookup"><span data-stu-id="253be-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="253be-105">Nazwy wszystkich poleceń cmdlet zaczynają się od zlecenie **Format**.</span><span class="sxs-lookup"><span data-stu-id="253be-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="253be-106">Umożliwiają one wybierz jedną lub więcej właściwości do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="253be-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="253be-107">**Format** polecenia cmdlet są **całej Format**, **Format-Lista**, **Format-Table**, i **Format-niestandardowe**.</span><span class="sxs-lookup"><span data-stu-id="253be-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="253be-108">Zostaną przedstawione tylko **całej Format**, **Format-Lista**, i **Format-Table** polecenia cmdlet w tym podręczniku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="253be-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="253be-109">Każde polecenie cmdlet format ma domyślne właściwości, które zostaną użyte, jeśli nie określisz określonych właściwości do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="253be-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="253be-110">Każde polecenie cmdlet używa również nazwę tego samego parametru **właściwości**, aby określić właściwości, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="253be-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="253be-111">Ponieważ **całej Format** przedstawia tylko jedną właściwość jego **właściwości** Parametr przyjmuje tylko pojedynczą wartość, ale parametry właściwości **listy Format** i **Format-Table** przyjmuje listę nazw właściwości.</span><span class="sxs-lookup"><span data-stu-id="253be-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="253be-112">Jeśli używasz polecenia **Get-Process - powershell nazwę** z dwoma wystąpieniami programu Windows PowerShell działa, możesz uzyskać dane wyjściowe, która wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="253be-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="253be-113">W dalszej części tej sekcji, przeanalizujemy sposobu używania **Format** polecenia cmdlet, aby zmienić sposób wyświetlania danych wyjściowych tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="253be-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="253be-114">Przy użyciu formatu na poziomie dla danych wyjściowych jednego elementu</span><span class="sxs-lookup"><span data-stu-id="253be-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="253be-115">**Całej Format** polecenia cmdlet, domyślnie są wyświetlane tylko domyślnej właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="253be-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="253be-116">Informacje skojarzone z każdego obiektu są wyświetlane w jednej kolumnie:</span><span class="sxs-lookup"><span data-stu-id="253be-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="253be-117">Można również określić właściwości innych niż domyślne:</span><span class="sxs-lookup"><span data-stu-id="253be-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="253be-118">Kontrolowanie Format całej wyświetlana z kolumną</span><span class="sxs-lookup"><span data-stu-id="253be-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="253be-119">Z **całej Format** polecenia cmdlet, możesz wyświetlić tylko jedną właściwość naraz.</span><span class="sxs-lookup"><span data-stu-id="253be-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="253be-120">Dzięki temu przydatne do wyświetlania listy proste, które zawierają tylko jeden element w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="253be-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="253be-121">Aby uzyskać listę proste, ustaw wartość **kolumny** parametru na wartość 1, wpisując:</span><span class="sxs-lookup"><span data-stu-id="253be-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="253be-122">Przy użyciu listy Format dla widoku listy</span><span class="sxs-lookup"><span data-stu-id="253be-122">Using Format-List for a List View</span></span>

<span data-ttu-id="253be-123">**Format-Lista** polecenie cmdlet wyświetla obiektu w postaci listy, z każdej właściwości z etykietą i wyświetlane w oddzielnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="253be-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="253be-124">Można określić dowolną liczbę właściwości:</span><span class="sxs-lookup"><span data-stu-id="253be-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="253be-125">Pobieranie szczegółowych informacji przy użyciu listy formatów z symbolami wieloznacznymi</span><span class="sxs-lookup"><span data-stu-id="253be-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="253be-126">**Format-Lista** polecenie cmdlet pozwala używać symboli wieloznacznych jako wartości jego **właściwości** parametru.</span><span class="sxs-lookup"><span data-stu-id="253be-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="253be-127">Dzięki temu można wyświetlić szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="253be-127">This lets you display detailed information.</span></span> <span data-ttu-id="253be-128">Często obiekty zawierają więcej informacji niż to konieczne, dlatego środowiska Windows PowerShell nie są wyświetlane wszystkie wartości właściwości domyślnie.</span><span class="sxs-lookup"><span data-stu-id="253be-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="253be-129">Aby wyświetlić wszystkie właściwości obiektu, należy użyć **listy Format — właściwość \&#42;** polecenia.</span><span class="sxs-lookup"><span data-stu-id="253be-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="253be-130">Polecenie generuje ponad 60 wiersze danych wyjściowych dla pojedynczego procesu:</span><span class="sxs-lookup"><span data-stu-id="253be-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="253be-131">Mimo że **Format-Lista** polecenie jest przydatne do wyświetlania szczegółów, jeśli chcesz przejrzeć dane wyjściowe, który zawiera wiele elementów prostsze widoku tabelarycznego jest często bardziej użyteczne.</span><span class="sxs-lookup"><span data-stu-id="253be-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="253be-132">Przy użyciu formatu tabeli dla tabelaryczne dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="253be-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="253be-133">Jeśli używasz **Format-Table** określone polecenie cmdlet z żadnych nazw właściwości do formatowania danych wyjściowych **Get-Process** polecenia Pobierz dokładnie takie same dane wyjściowe, jak bez formatowania.</span><span class="sxs-lookup"><span data-stu-id="253be-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="253be-134">Dzieje się tak że procesy są zwykle wyświetlane w formacie tabelarycznym są większość obiektów programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="253be-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="253be-135">Poprawa tabeli Format danych wyjściowych (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="253be-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="253be-136">Mimo że widoku tabelarycznego jest przydatne w przypadku wyświetlania wielu porównywalne informacji, może być trudne interpretować Jeśli ekran jest zbyt ograniczone danych.</span><span class="sxs-lookup"><span data-stu-id="253be-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="253be-137">Na przykład próba ścieżka procesu, identyfikator, nazwę wyświetlaną i firmy, możesz uzyskać skróconą dane wyjściowe ścieżka procesu i kolumn firmy:</span><span class="sxs-lookup"><span data-stu-id="253be-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="253be-138">Jeśli określisz **AutoSize** parametru podczas uruchamiania **Format-Table** poleceń programu Windows PowerShell obliczy szerokości kolumn na podstawie rzeczywistych danych mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="253be-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="253be-139">Dzięki temu **ścieżki** skróconą pozostaje kolumnę do odczytu, ale kolumna firmy:</span><span class="sxs-lookup"><span data-stu-id="253be-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="253be-140">**Format-Table** polecenia cmdlet nadal może obciąć danych, ale będzie tylko dokonywać na końcu ekranu.</span><span class="sxs-lookup"><span data-stu-id="253be-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="253be-141">Właściwości, innym niż ostatnio wyświetlane, są podane tyle rozmiar potrzebują ich najdłuższym elementu danych do poprawnego wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="253be-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="253be-142">Widać, że nazwa firmy jest widoczny, ale ścieżka zostanie obcięta, jeśli wymiany lokalizacje **ścieżki** i **firmy** w **właściwości** listy wartości:</span><span class="sxs-lookup"><span data-stu-id="253be-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="253be-143">**Format-Table** poleceniu założono, że nearer właściwości znajduje się na początku listy właściwości jest ważniejsze.</span><span class="sxs-lookup"><span data-stu-id="253be-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="253be-144">Dlatego próbuje wyświetlić właściwości najbliższej początku całkowicie.</span><span class="sxs-lookup"><span data-stu-id="253be-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="253be-145">Jeśli **Format-Table** polecenia nie można wyświetlić wszystkie właściwości, będzie usunąć niektóre kolumny z ekranu i ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="253be-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="253be-146">To zachowanie można wyświetlić, musisz wprowadzić **nazwa** ostatnich właściwości na liście:</span><span class="sxs-lookup"><span data-stu-id="253be-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="253be-147">W powyższych danych wyjściowych w kolumnie identyfikator został obcięty w celu dopasowania do listy, a nagłówki kolumn są ułożone w.</span><span class="sxs-lookup"><span data-stu-id="253be-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="253be-148">Automatyczna zmiana rozmiaru kolumn zawsze nie chcesz.</span><span class="sxs-lookup"><span data-stu-id="253be-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="253be-149">Zawijanie tabeli Format danych wyjściowych w kolumnach (zawijania)</span><span class="sxs-lookup"><span data-stu-id="253be-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="253be-150">Możesz wymusić, długotrwałą **Format-Table** danych do zakodowania w jego kolumnie jest wyświetlana przy użyciu **zawijanie** parametru.</span><span class="sxs-lookup"><span data-stu-id="253be-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="253be-151">Przy użyciu **zawijanie** samego parametru niekoniecznie nie ma oczekiwanego, ponieważ wykorzystuje ustawienia domyślne, jeśli nie określono również **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="253be-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="253be-152">Zaletą używania **zawijanie** parametr samodzielnie jest, że spowolnienia przetwarzania bardzo.</span><span class="sxs-lookup"><span data-stu-id="253be-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="253be-153">Jeśli na liście plików cykliczne systemu dużego katalogu, może zająć bardzo dużo czasu i używać dużej ilości pamięci, przed wyświetleniem pierwsze elementów danych wyjściowych, jeśli używasz **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="253be-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="253be-154">Jeśli nie masz obawy obciążenia systemu, następnie **AutoSize** dobrze działa z **zawijanie** parametru.</span><span class="sxs-lookup"><span data-stu-id="253be-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="253be-155">Początkowych kolumn zawsze są przydzielony tyle szerokość potrzebują do wyświetlania elementów w jednym wierszu, tak jak w przypadku określenia **AutoSize** bez **zawijanie** parametru.</span><span class="sxs-lookup"><span data-stu-id="253be-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="253be-156">Jedyna różnica polega na tym, że w razie potrzeby zostaną opakowane ostatniej kolumny:</span><span class="sxs-lookup"><span data-stu-id="253be-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="253be-157">Niektóre kolumny mogą nie być wyświetlane określenia najszerszego kolumn, dlatego jest najbezpieczniejszy określić najmniejszy elementy danych w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="253be-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="253be-158">W poniższym przykładzie, możemy Określ elementu bardzo szeroki ścieżki najpierw, a nawet z zawijaniem, będziemy nadal utratę ostatecznego **nazwa** kolumny:</span><span class="sxs-lookup"><span data-stu-id="253be-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="253be-159">Organizowanie w tabeli danych wyjściowych (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="253be-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="253be-160">Inny parametr przydatne do kontroli tabelaryczne dane wyjściowe jest **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="253be-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="253be-161">W szczególności już tabelarycznych listy może być trudne do porównania.</span><span class="sxs-lookup"><span data-stu-id="253be-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="253be-162">**GroupBy** parametru grupuje dane wyjściowe na podstawie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="253be-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="253be-163">Na przykład możemy grupy procesów przez firmę do kontroli łatwiejsze, pomijając wartość firmy z listy właściwości:</span><span class="sxs-lookup"><span data-stu-id="253be-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```