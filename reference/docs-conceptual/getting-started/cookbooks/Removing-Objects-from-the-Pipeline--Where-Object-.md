---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Usuwanie obiektów z potoku gdzie obiektów"
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 4140c4c3ebb26223d03ca139992fedf6e184a38b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="9c439-103">Usuwanie obiektów z potoku (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="9c439-103">Removing Objects from the Pipeline (Where-Object)</span></span>
<span data-ttu-id="9c439-104">W programie Windows PowerShell można często generować i przekazują więcej obiektów dla potoku nie ma.</span><span class="sxs-lookup"><span data-stu-id="9c439-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="9c439-105">Możesz określić właściwości określonym obiektów do wyświetlenia za pomocą **Format** poleceń cmdlet, ale nie pomaga problemu usunięcie całych obiektów z ekranu.</span><span class="sxs-lookup"><span data-stu-id="9c439-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="9c439-106">Można filtrować obiektów przed zakończeniem potoku, więc dostępne akcje na podzbiorze wstępnie wygenerowane obiekty.</span><span class="sxs-lookup"><span data-stu-id="9c439-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="9c439-107">Program Windows PowerShell zawiera **Where-Object** polecenia cmdlet, które umożliwia testowanie każdego obiektu w potoku i tylko przekazywanie ich do potoku spełniający określonego warunku.</span><span class="sxs-lookup"><span data-stu-id="9c439-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="9c439-108">Obiekty, które nie przejdą testów są usuwane z potoku.</span><span class="sxs-lookup"><span data-stu-id="9c439-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="9c439-109">Podaj warunku w postaci wartości **Where ObjectFilterScript** parametru.</span><span class="sxs-lookup"><span data-stu-id="9c439-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="9c439-110">Wykonywanie prostych testów z Where-Object</span><span class="sxs-lookup"><span data-stu-id="9c439-110">Performing Simple Tests with Where-Object</span></span>
<span data-ttu-id="9c439-111">Wartość **FilterScript** jest *bloku skryptu* — jeden lub więcej poleceń programu Windows PowerShell otoczona nawiasów klamrowych {} - który daje w wyniku wartość true lub false.</span><span class="sxs-lookup"><span data-stu-id="9c439-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="9c439-112">Te bloki skryptu może być bardzo proste, ale są one tworzone wymaga wiedzy pojęcie innego środowiska Windows PowerShell i operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="9c439-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="9c439-113">Operator porównania porównuje elementy, które są wyświetlane na każdej stronie.</span><span class="sxs-lookup"><span data-stu-id="9c439-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="9c439-114">Operatory porównania rozpoczynać się od "-" znak i zostaną wykonane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="9c439-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="9c439-115">Operatory porównania podstawowe działają w niemal każdego rodzaju obiektu.</span><span class="sxs-lookup"><span data-stu-id="9c439-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="9c439-116">Bardziej zaawansowane operatory porównania może działać tylko na tekst lub tablic.</span><span class="sxs-lookup"><span data-stu-id="9c439-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="9c439-117">Domyślnie podczas pracy z tekstem programu Windows PowerShell operatory porównania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9c439-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="9c439-118">Z powodu analizy zagadnienia, symbole, takie jak <>, i = nie są używane jako operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="9c439-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="9c439-119">Zamiast tego operatory porównania składają się z liter.</span><span class="sxs-lookup"><span data-stu-id="9c439-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="9c439-120">Operatory porównania podstawowe są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9c439-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="9c439-121">Operator porównania</span><span class="sxs-lookup"><span data-stu-id="9c439-121">Comparison Operator</span></span>|<span data-ttu-id="9c439-122">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="9c439-122">Meaning</span></span>|<span data-ttu-id="9c439-123">Przykład (zwraca wartość true)</span><span class="sxs-lookup"><span data-stu-id="9c439-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="9c439-124">-eq</span><span class="sxs-lookup"><span data-stu-id="9c439-124">-eq</span></span>|<span data-ttu-id="9c439-125">jest równa</span><span class="sxs-lookup"><span data-stu-id="9c439-125">is equal to</span></span>|<span data-ttu-id="9c439-126">1 - eq 1</span><span class="sxs-lookup"><span data-stu-id="9c439-126">1 -eq 1</span></span>|
|<span data-ttu-id="9c439-127">-ne</span><span class="sxs-lookup"><span data-stu-id="9c439-127">-ne</span></span>|<span data-ttu-id="9c439-128">Nie równa się</span><span class="sxs-lookup"><span data-stu-id="9c439-128">Is not equal to</span></span>|<span data-ttu-id="9c439-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="9c439-129">1 -ne 2</span></span>|
|<span data-ttu-id="9c439-130">lt —</span><span class="sxs-lookup"><span data-stu-id="9c439-130">-lt</span></span>|<span data-ttu-id="9c439-131">Jest mniejsza niż</span><span class="sxs-lookup"><span data-stu-id="9c439-131">Is less than</span></span>|<span data-ttu-id="9c439-132">1 - lt 2</span><span class="sxs-lookup"><span data-stu-id="9c439-132">1 -lt 2</span></span>|
|<span data-ttu-id="9c439-133">-le</span><span class="sxs-lookup"><span data-stu-id="9c439-133">-le</span></span>|<span data-ttu-id="9c439-134">Jest mniejsze niż lub równe</span><span class="sxs-lookup"><span data-stu-id="9c439-134">Is less than or equal to</span></span>|<span data-ttu-id="9c439-135">le 1 - 2</span><span class="sxs-lookup"><span data-stu-id="9c439-135">1 -le 2</span></span>|
|<span data-ttu-id="9c439-136">-></span><span class="sxs-lookup"><span data-stu-id="9c439-136">-gt</span></span>|<span data-ttu-id="9c439-137">Jest większa niż</span><span class="sxs-lookup"><span data-stu-id="9c439-137">Is greater than</span></span>|<span data-ttu-id="9c439-138">2 - gt-1</span><span class="sxs-lookup"><span data-stu-id="9c439-138">2 -gt 1</span></span>|
|<span data-ttu-id="9c439-139">-ge</span><span class="sxs-lookup"><span data-stu-id="9c439-139">-ge</span></span>|<span data-ttu-id="9c439-140">Jest większe lub równe</span><span class="sxs-lookup"><span data-stu-id="9c439-140">Is greater than or equal to</span></span>|<span data-ttu-id="9c439-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="9c439-141">2 -ge 1</span></span>|
|<span data-ttu-id="9c439-142">— przykład</span><span class="sxs-lookup"><span data-stu-id="9c439-142">-like</span></span>|<span data-ttu-id="9c439-143">Przypomina (symbol wieloznaczny porównanie tekstu)</span><span class="sxs-lookup"><span data-stu-id="9c439-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="9c439-144">"file.doc" — takie jak "f\*.korzystać?"</span><span class="sxs-lookup"><span data-stu-id="9c439-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="9c439-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="9c439-145">-notlike</span></span>|<span data-ttu-id="9c439-146">Nie jest jak (symbol wieloznaczny porównanie tekstu)</span><span class="sxs-lookup"><span data-stu-id="9c439-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="9c439-147">"file.doc"-notlike "p\*doc"</span><span class="sxs-lookup"><span data-stu-id="9c439-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="9c439-148">-zawiera</span><span class="sxs-lookup"><span data-stu-id="9c439-148">-contains</span></span>|<span data-ttu-id="9c439-149">zawiera</span><span class="sxs-lookup"><span data-stu-id="9c439-149">Contains</span></span>|<span data-ttu-id="9c439-150">1,2,3 - zawiera 1</span><span class="sxs-lookup"><span data-stu-id="9c439-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="9c439-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="9c439-151">-notcontains</span></span>|<span data-ttu-id="9c439-152">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="9c439-152">Does not contain</span></span>|<span data-ttu-id="9c439-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="9c439-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="9c439-154">WHERE-Object blokach skryptu za pomocą specjalnych zmiennej '$_' do odwoływania się do bieżącego obiektu w potoku.</span><span class="sxs-lookup"><span data-stu-id="9c439-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="9c439-155">Poniżej przedstawiono przykładowy sposób jej działania.</span><span class="sxs-lookup"><span data-stu-id="9c439-155">Here is an example of how it works.</span></span> <span data-ttu-id="9c439-156">Jeśli masz listę liczb i chcesz tylko te, które są mniej niż 3 zwracać, umożliwia Where-Object filtrować liczb, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9c439-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="9c439-157">Filtrowanie oparte na właściwości obiektu</span><span class="sxs-lookup"><span data-stu-id="9c439-157">Filtering Based on Object Properties</span></span>
<span data-ttu-id="9c439-158">Ponieważ $_ odwołuje się do bieżącego obiektu potoku, firma Microsoft dostęp do jej właściwości na potrzeby testów.</span><span class="sxs-lookup"><span data-stu-id="9c439-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="9c439-159">Na przykład można przyjrzymy się Klasa Win32_SystemDriver w usłudze WMI.</span><span class="sxs-lookup"><span data-stu-id="9c439-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="9c439-160">Może to być setki sterowników systemu w określonym systemie, ale może być zainteresowany określony zestaw sterowników systemu, takich jak te, które są aktualnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="9c439-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="9c439-161">Jeśli element członkowski Get służy do wyświetlania elementów członkowskich Win32_SystemDriver (**Get-WmiObject — Klasa Win32_SystemDriver | Właściwość Get-Member - MemberType**) pojawi się stan jest odpowiednie właściwości i że ma wartość "Działa" po uruchomieniu sterownika.</span><span class="sxs-lookup"><span data-stu-id="9c439-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="9c439-162">Można filtrować sterowniki systemu wybranie tylko uruchomione te, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9c439-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

<span data-ttu-id="9c439-163">Daje to nadal długą listę.</span><span class="sxs-lookup"><span data-stu-id="9c439-163">This still produces a long list.</span></span> <span data-ttu-id="9c439-164">Można filtrować można wybrać tylko sterowniki uruchamiana automatycznie, sprawdzając wartość StartMode również:</span><span class="sxs-lookup"><span data-stu-id="9c439-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="9c439-165">Daje wiele informacji, które firma Microsoft nie jest już potrzebny, ponieważ wiemy, że sterowniki są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="9c439-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="9c439-166">W rzeczywistości tylko informacje, które prawdopodobnie potrzebujemy w tym momencie są nazwa i nazwę wyświetlaną.</span><span class="sxs-lookup"><span data-stu-id="9c439-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="9c439-167">Polecenie zawiera tylko te dwie właściwości, co znacznie prostsze danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="9c439-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="9c439-168">Istnieją dwa elementy Where-Object w poleceniu powyżej, ale może zostać wyrażona w jednym elemencie Where-Object przy użyciu i operatora logicznego następująco:</span><span class="sxs-lookup"><span data-stu-id="9c439-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="9c439-169">Standardowe operatory logiczne są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9c439-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="9c439-170">Operator logiczny</span><span class="sxs-lookup"><span data-stu-id="9c439-170">Logical Operator</span></span>|<span data-ttu-id="9c439-171">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="9c439-171">Meaning</span></span>|<span data-ttu-id="9c439-172">Przykład (zwraca wartość true)</span><span class="sxs-lookup"><span data-stu-id="9c439-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="9c439-173">- i</span><span class="sxs-lookup"><span data-stu-id="9c439-173">-and</span></span>|<span data-ttu-id="9c439-174">Logiczne i; wartość true, jeśli obie strony mają wartość true</span><span class="sxs-lookup"><span data-stu-id="9c439-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="9c439-175">(1 - eq 1) - i (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="9c439-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="9c439-176">- lub</span><span class="sxs-lookup"><span data-stu-id="9c439-176">-or</span></span>|<span data-ttu-id="9c439-177">Logiczna lub; wartość true, jeśli jedna strona ma wartość true</span><span class="sxs-lookup"><span data-stu-id="9c439-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="9c439-178">(1 - eq 1) - lub (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="9c439-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="9c439-179">-nie</span><span class="sxs-lookup"><span data-stu-id="9c439-179">-not</span></span>|<span data-ttu-id="9c439-180">Negacja; Odwraca wartość true i false</span><span class="sxs-lookup"><span data-stu-id="9c439-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="9c439-181">-nie (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="9c439-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="9c439-182">Negacja; Odwraca wartość true i false</span><span class="sxs-lookup"><span data-stu-id="9c439-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="9c439-183">\!(1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="9c439-183">\!(1 -eq 2)</span></span>|

