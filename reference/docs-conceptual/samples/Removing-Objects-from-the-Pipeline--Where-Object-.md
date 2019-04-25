---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Usuwanie obiektów z potoku gdzie obiektu
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057916"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="dcc93-103">Usuwanie obiektów z potoku (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="dcc93-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="dcc93-104">W programie Windows PowerShell możesz często Generowanie i przekazują więcej obiektów do potoku niż potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="dcc93-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="dcc93-105">Można określić właściwości określonego obiektów przeznaczonych do wyświetlenia przy użyciu **Format** poleceń cmdlet, ale nie jest pomocne w rozwiązaniu problemu usunięcia całe obiekty z widoku.</span><span class="sxs-lookup"><span data-stu-id="dcc93-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="dcc93-106">Można filtrować obiektów przed zakończeniem potoku, dzięki czemu można przeprowadzać na tylko podzbiór obiektów początkowo wygenerował.</span><span class="sxs-lookup"><span data-stu-id="dcc93-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="dcc93-107">Program Windows PowerShell zawiera `Where-Object` polecenia cmdlet, które umożliwia testowanie każdy obiekt w potoku i tylko przekazać go do potoku Jeśli dana jednostka spełnia warunek określonego testu.</span><span class="sxs-lookup"><span data-stu-id="dcc93-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="dcc93-108">Obiekty, które nie są przekazywane do testu są usuwane z potoku.</span><span class="sxs-lookup"><span data-stu-id="dcc93-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="dcc93-109">Możesz podać warunek testu jako wartość `Where-Object` **FilterScript** parametru.</span><span class="sxs-lookup"><span data-stu-id="dcc93-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="dcc93-110">Wykonując proste testy za pomocą Where-Object</span><span class="sxs-lookup"><span data-stu-id="dcc93-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="dcc93-111">Wartość **FilterScript** jest *blok skryptu* — jedno lub kilka poleceń programu Windows PowerShell, ujęte w nawiasy klamrowe {} — która daje w wyniku wartość true lub false.</span><span class="sxs-lookup"><span data-stu-id="dcc93-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="dcc93-112">Te bloki skryptu może być bardzo proste, ale są one tworzone wymaga, wiedząc o innym pojęcia programu Windows PowerShell, operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="dcc93-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="dcc93-113">Operator porównania porównuje elementów, które pojawiają się na każdej stronie.</span><span class="sxs-lookup"><span data-stu-id="dcc93-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="dcc93-114">Operatory porównania zaczynają się od "-" znaków i są następuje nazwa.</span><span class="sxs-lookup"><span data-stu-id="dcc93-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="dcc93-115">Operatory porównania podstawowe działa na prawie każdy rodzaj obiektu.</span><span class="sxs-lookup"><span data-stu-id="dcc93-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="dcc93-116">Więcej informacji o zaawansowanych operatory porównania może działać wyłącznie względem tekstu lub tablic.</span><span class="sxs-lookup"><span data-stu-id="dcc93-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="dcc93-117">Domyślnie podczas pracy z tekstem operatory porównania programu Windows PowerShell jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dcc93-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="dcc93-118">Ze względu na analizowanie zagadnienia, symbole, takie jak <>, i = nie są używane jako operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="dcc93-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="dcc93-119">Zamiast tego operatory porównania składają się z liter.</span><span class="sxs-lookup"><span data-stu-id="dcc93-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="dcc93-120">Operatory porównania podstawowe są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dcc93-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="dcc93-121">Operator porównania</span><span class="sxs-lookup"><span data-stu-id="dcc93-121">Comparison Operator</span></span>|<span data-ttu-id="dcc93-122">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="dcc93-122">Meaning</span></span>|<span data-ttu-id="dcc93-123">Przykład (zwraca wartość true)</span><span class="sxs-lookup"><span data-stu-id="dcc93-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="dcc93-124">-eq</span><span class="sxs-lookup"><span data-stu-id="dcc93-124">-eq</span></span>|<span data-ttu-id="dcc93-125">jest równa</span><span class="sxs-lookup"><span data-stu-id="dcc93-125">is equal to</span></span>|<span data-ttu-id="dcc93-126">1 - eq 1</span><span class="sxs-lookup"><span data-stu-id="dcc93-126">1 -eq 1</span></span>|
|<span data-ttu-id="dcc93-127">-ne</span><span class="sxs-lookup"><span data-stu-id="dcc93-127">-ne</span></span>|<span data-ttu-id="dcc93-128">Nie równa się</span><span class="sxs-lookup"><span data-stu-id="dcc93-128">Is not equal to</span></span>|<span data-ttu-id="dcc93-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="dcc93-129">1 -ne 2</span></span>|
|<span data-ttu-id="dcc93-130">-lt</span><span class="sxs-lookup"><span data-stu-id="dcc93-130">-lt</span></span>|<span data-ttu-id="dcc93-131">Jest mniejsza niż</span><span class="sxs-lookup"><span data-stu-id="dcc93-131">Is less than</span></span>|<span data-ttu-id="dcc93-132">1 - lt 2</span><span class="sxs-lookup"><span data-stu-id="dcc93-132">1 -lt 2</span></span>|
|<span data-ttu-id="dcc93-133">-le</span><span class="sxs-lookup"><span data-stu-id="dcc93-133">-le</span></span>|<span data-ttu-id="dcc93-134">jest mniejsze niż lub równe</span><span class="sxs-lookup"><span data-stu-id="dcc93-134">Is less than or equal to</span></span>|<span data-ttu-id="dcc93-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="dcc93-135">1 -le 2</span></span>|
|<span data-ttu-id="dcc93-136">-gt</span><span class="sxs-lookup"><span data-stu-id="dcc93-136">-gt</span></span>|<span data-ttu-id="dcc93-137">jest większa niż</span><span class="sxs-lookup"><span data-stu-id="dcc93-137">Is greater than</span></span>|<span data-ttu-id="dcc93-138">2 - > 1</span><span class="sxs-lookup"><span data-stu-id="dcc93-138">2 -gt 1</span></span>|
|<span data-ttu-id="dcc93-139">-ge</span><span class="sxs-lookup"><span data-stu-id="dcc93-139">-ge</span></span>|<span data-ttu-id="dcc93-140">jest większe lub równe</span><span class="sxs-lookup"><span data-stu-id="dcc93-140">Is greater than or equal to</span></span>|<span data-ttu-id="dcc93-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="dcc93-141">2 -ge 1</span></span>|
|<span data-ttu-id="dcc93-142">— np.</span><span class="sxs-lookup"><span data-stu-id="dcc93-142">-like</span></span>|<span data-ttu-id="dcc93-143">Przypomina (symbol wieloznaczny porównanie tekstu)</span><span class="sxs-lookup"><span data-stu-id="dcc93-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="dcc93-144">"file.doc" — takich jak "f\*.korzystać?"</span><span class="sxs-lookup"><span data-stu-id="dcc93-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="dcc93-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="dcc93-145">-notlike</span></span>|<span data-ttu-id="dcc93-146">Nie jest podobne (symbol wieloznaczny porównanie tekstu)</span><span class="sxs-lookup"><span data-stu-id="dcc93-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="dcc93-147">"file.doc"-notlike "p\*doc"</span><span class="sxs-lookup"><span data-stu-id="dcc93-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="dcc93-148">-zawiera</span><span class="sxs-lookup"><span data-stu-id="dcc93-148">-contains</span></span>|<span data-ttu-id="dcc93-149">zawiera</span><span class="sxs-lookup"><span data-stu-id="dcc93-149">Contains</span></span>|<span data-ttu-id="dcc93-150">1,2,3 - zawiera 1</span><span class="sxs-lookup"><span data-stu-id="dcc93-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="dcc93-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="dcc93-151">-notcontains</span></span>|<span data-ttu-id="dcc93-152">Nie zawiera</span><span class="sxs-lookup"><span data-stu-id="dcc93-152">Does not contain</span></span>|<span data-ttu-id="dcc93-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="dcc93-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="dcc93-154">WHERE-Object Bloki skryptu za pomocą specjalnych zmiennej `$_` do odwoływania się do bieżącego obiektu w potoku.</span><span class="sxs-lookup"><span data-stu-id="dcc93-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="dcc93-155">Oto przykład sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="dcc93-155">Here is an example of how it works.</span></span> <span data-ttu-id="dcc93-156">Jeśli masz listę liczb i tylko mają być zwracane te, które są mniej niż 3, można użyć Where-Object do filtrowania liczby, wpisując:</span><span class="sxs-lookup"><span data-stu-id="dcc93-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="dcc93-157">Filtrowanie oparte na właściwości obiektu</span><span class="sxs-lookup"><span data-stu-id="dcc93-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="dcc93-158">Ponieważ `$_` odwołuje się do bieżącego obiektu potoku, firma Microsoft będą mogli jej właściwości na potrzeby testów.</span><span class="sxs-lookup"><span data-stu-id="dcc93-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="dcc93-159">Na przykład można przyjrzymy się Klasa Win32_SystemDriver w usłudze WMI.</span><span class="sxs-lookup"><span data-stu-id="dcc93-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="dcc93-160">Mogą istnieć setki sterowników systemu w określonym systemie, ale może być tylko zainteresowana określony zestaw sterowników systemu, takie jak te, które są aktualnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="dcc93-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="dcc93-161">Jeśli używasz Get-Member, aby wyświetlić elementy członkowskie Win32_SystemDriver (**Get-WmiObject — Klasa Win32_SystemDriver | Właściwość Get-Member - MemberType**) widać to za pomocą odpowiednich właściwości stanu i że ma wartość "Uruchomiona", gdy sterownik jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="dcc93-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="dcc93-162">Możesz filtrować sterowniki systemowe, wybierając tylko uruchomione, wpisując:</span><span class="sxs-lookup"><span data-stu-id="dcc93-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="dcc93-163">Daje to nadal długą listę.</span><span class="sxs-lookup"><span data-stu-id="dcc93-163">This still produces a long list.</span></span> <span data-ttu-id="dcc93-164">Można filtrować tylko wybranym sterowniki uruchamiana automatycznie, testując również wartość StartMode:</span><span class="sxs-lookup"><span data-stu-id="dcc93-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

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

<span data-ttu-id="dcc93-165">To daje nam mnóstwo informacji, które firma Microsoft nie są już potrzebne, ponieważ wiemy, że sterowniki są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="dcc93-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="dcc93-166">W rzeczywistości tylko informacje, które prawdopodobnie należy w tym momencie są nazwę i nazwę wyświetlaną.</span><span class="sxs-lookup"><span data-stu-id="dcc93-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="dcc93-167">Poniższe polecenie uwzględnia tylko te dwie właściwości, co znacznie przyspiesza dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="dcc93-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

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

<span data-ttu-id="dcc93-168">Istnieją dwa elementy Where-Object w poleceniu powyżej, ale mogą być wyrażone w pojedynczym elemencie Where-Object przy użyciu i operatora logicznego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dcc93-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="dcc93-169">Standardowe operatory logiczne są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dcc93-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="dcc93-170">Operator logiczny</span><span class="sxs-lookup"><span data-stu-id="dcc93-170">Logical Operator</span></span>|<span data-ttu-id="dcc93-171">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="dcc93-171">Meaning</span></span>|<span data-ttu-id="dcc93-172">Przykład (zwraca wartość true)</span><span class="sxs-lookup"><span data-stu-id="dcc93-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="dcc93-173">- i</span><span class="sxs-lookup"><span data-stu-id="dcc93-173">-and</span></span>|<span data-ttu-id="dcc93-174">Logiczne i; wartość true, jeśli obie strony mają wartość true</span><span class="sxs-lookup"><span data-stu-id="dcc93-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="dcc93-175">(1 - eq 1) — a (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="dcc93-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="dcc93-176">— lub</span><span class="sxs-lookup"><span data-stu-id="dcc93-176">-or</span></span>|<span data-ttu-id="dcc93-177">Logiczne lub; wartość true, jeśli strona ma wartość true</span><span class="sxs-lookup"><span data-stu-id="dcc93-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="dcc93-178">(1 - eq 1) - lub (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="dcc93-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="dcc93-179">-nie</span><span class="sxs-lookup"><span data-stu-id="dcc93-179">-not</span></span>|<span data-ttu-id="dcc93-180">Logiczne not; Odwraca wartość PRAWDA i FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="dcc93-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="dcc93-181">-nie (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="dcc93-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="dcc93-182">Logiczne not; Odwraca wartość PRAWDA i FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="dcc93-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="dcc93-183">\!(1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="dcc93-183">\!(1 -eq 2)</span></span>|
