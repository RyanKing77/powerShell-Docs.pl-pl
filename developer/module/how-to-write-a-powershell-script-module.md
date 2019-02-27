---
title: Jak napisać modul Skriptu Powershellu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848916"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="cfbcf-102">Jak napisać moduł skryptu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfbcf-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="cfbcf-103">Moduł skryptu jest zasadniczo wszystkie prawidłowe skrypt programu PowerShell zaoszczędził rozszerzenia psm1.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="cfbcf-104">To rozszerzenie umożliwia aparatu programu PowerShell do użycia szereg reguł i polecenia cmdlet na plik.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="cfbcf-105">Większość tych funkcji, czy istnieją ułatwią zainstalowanie kodu w innych systemach również zarządzać zakresu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="cfbcf-106">Można również użyć w pliku manifestu modułu, który można opisać w bardziej złożonych instalacji i rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="cfbcf-107">Pisanie modułu programu skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfbcf-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="cfbcf-108">Zapisywanie pliku psm1 prawidłowy skrypt programu PowerShell, a następnie zapisz ten plik w katalogu znajdujących się gdzie PowerShell może okazać się możesz utworzyć moduł skryptu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="cfbcf-109">W tym folderze, możesz również umieścić wszelkie zasoby, należy uruchomić skrypt a także plik manifestu, który opisuje w programie PowerShell działania modułu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="cfbcf-110">Aby utworzyć podstawowy moduł programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfbcf-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="cfbcf-111">Wykonaj istniejącego skryptu programu PowerShell i Zapisz skrypt za pomocą rozszerzenia psm1.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="cfbcf-112">Zapisywanie skryptu za pomocą psm1 rozszerzenia oznacza, że polecenia cmdlet modułu, można użyć takich jak [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), na nim.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="cfbcf-113">Te polecenia cmdlet istnieją głównie tak, aby można łatwo importować i eksportować kodu na systemach innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="cfbcf-114">(Rozwiązanie alternatywne byłoby załadować zapasową swojego kodu na innych systemów, a następnie kropka źródła do aktywnej pamięci, która nie jest to szczególnie skalowalne rozwiązanie.) Aby uzyskać więcej informacji, zobacz **polecenia cmdlet modułu i zmienne** sekcji [moduły programu Windows PowerShell](./understanding-a-windows-powershell-module.md) należy pamiętać, że domyślnie wszystkie funkcje w skrypcie będą dostępne dla użytkowników, którzy zaimportować swoje psm1 plik, ale właściwości nie będzie.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script will be accessible to users who import your .psm1 file, but properties will not.</span></span>

   <span data-ttu-id="cfbcf-115">Przykładowy skrypt programu PowerShell uprawnionych Show-kalendarza, jest dostępna na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-115">An example PowerShell script, entitled Show-Calendar, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="cfbcf-116">Jeśli chcesz kontrolować dostęp użytkownika do określonych funkcji i właściwości, należy wywołać [ModuleMember eksportu](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-116">If you wish to control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="cfbcf-117">Przykładowy kod w dolnej części strony ma tylko jedną funkcję, domyślnie będzie widoczne.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="cfbcf-118">Jednak zaleca się, że należy jawnie wywołać funkcje, które chcesz udostępnić, zgodnie z opisem w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cfbcf-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="cfbcf-119">Można również ograniczyć, co jest importowany manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="cfbcf-120">Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md) i [jak napisać Manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cfbcf-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="cfbcf-121">Jeśli masz moduły, które własny moduł musi zostać załadowany, można ich użyć z wywołania `Import-Module`, w górnej części własny moduł.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="cfbcf-122">`Import-Module` to polecenie cmdlet importuje moduł docelowych do systemu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="cfbcf-123">W efekcie również służy w dowolnym momencie w procedurze do zainstalowania swój własny moduł, jak również.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="cfbcf-124">Przykładowy kod w dolnej części tej strony nie używa żadnych modułów importu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="cfbcf-125">Jeśli została jednak one będą wyświetlane w górnej części pliku, zgodnie z opisem w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cfbcf-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="cfbcf-126">Jeśli użytkownik chce opisać modułu do systemu pomocy programu PowerShell, możesz to zrobić z komentarzami pomoc standard wewnątrz pliku lub przy użyciu dodatkowego pliku pomocy.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-126">If you want to describe your module to the PowerShell Help system, you can do so either with the standard help comments inside the file, or with an additional Help file.</span></span>

   <span data-ttu-id="cfbcf-127">Przykładowy kod w dolnej części tego tematu zawiera informacje pomocy w komentarzach.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="cfbcf-128">Jeśli tak, można również zapisać rozwinięte pliki XML, które zawierają dodatkową zawartość pomocy.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-128">If you so choose, you could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="cfbcf-129">Aby uzyskać więcej informacji, zobacz [zapisywania pomocy dla Windows modułów programu PowerShell](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="cfbcf-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="cfbcf-130">Jeśli masz dodatkowe moduły, pliki XML lub innej zawartości, którą chcesz spakować z modułu, możesz to zrobić z manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="cfbcf-131">Manifest modułu jest plik, który zawiera nazwy inne moduły, układy katalogów, numery wersji, autor danych i innych rodzajów informacji.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="cfbcf-132">Program PowerShell używa pliku manifestu modułu do organizowania i wdrażać rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="cfbcf-133">Jednak ze względu na charakter stosunkowo proste, w tym przykładzie, plik manifestu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="cfbcf-134">Aby uzyskać więcej informacji, zobacz [manifesty modułu](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cfbcf-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="cfbcf-135">Do zainstalowania i uruchomienia modułu, Zapisz moduł do jednego z odpowiedniej ścieżki programu PowerShell, a wywołanie `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="cfbcf-136">Ścieżki, w którym można zainstalować modułu znajdują się w `$env:PSModulePath` zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="cfbcf-137">Na przykład będzie wspólną ścieżkę można zapisać modułu w systemie `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="cfbcf-138">Należy koniecznie Utwórz folder modułu istnieje, nawet jeśli jest to plik psm1 jednego.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="cfbcf-139">Jeśli nie została zapisana modułu do jednej z tych ścieżek, trzeba będzie przekazać w lokalizacji modułu w wywołaniu `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="cfbcf-140">(W przeciwnym razie program PowerShell będzie nie można go znaleźć.) Program PowerShell 3.0, począwszy od umieszczenie modułu w jednej ze ścieżek modułu programu PowerShell, nie trzeba jawnie go importują: po prostu poprosić użytkownika, wywołaj funkcję załaduje go automatycznie.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module on one of the PowerShell module paths, you do not need to explicitly import it: simply having a user call your function will automatically load it.</span></span> <span data-ttu-id="cfbcf-141">Aby uzyskać więcej informacji na temat ścieżka modułu, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md) i [zmienna środowiskowa PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="cfbcf-141">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="cfbcf-142">Aby usunąć moduł usługi active, wywoływania [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="cfbcf-142">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

<span data-ttu-id="cfbcf-143">Należy pamiętać, że [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) spowoduje usunięcie modułu z aktywnej pamięci — go nie rzeczywistego usunięcia go z którym zostały zapisane pliki modułu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-143">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="cfbcf-144">Pokaż kalendarz przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="cfbcf-144">Show-Calendar code example</span></span>

<span data-ttu-id="cfbcf-145">Poniższy przykład jest moduł prosty skrypt, który zawiera pojedynczą funkcję o nazwie Show kalendarza.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-145">The following example is a simple script module that contains a single function named Show-Calendar.</span></span> <span data-ttu-id="cfbcf-146">Funkcja ta wyświetla wizualną reprezentację kalendarza.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-146">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="cfbcf-147">Ponadto przykładu zawiera ciągi Pomoc programu PowerShell, streszczenie, opis, wartości parametrów oraz przykład.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-147">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="cfbcf-148">Należy pamiętać, że ostatni wiersz kodu wskazuje, że funkcja Pokaż kalendarz zostaną wyeksportowane jako członek modułu po zaimportowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="cfbcf-148">Note that the last line of code indicates that the Show-Calendar function will be exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
