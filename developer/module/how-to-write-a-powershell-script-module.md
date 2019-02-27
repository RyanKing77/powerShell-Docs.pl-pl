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
# <a name="how-to-write-a-powershell-script-module"></a>Jak napisać moduł skryptu programu PowerShell

Moduł skryptu jest zasadniczo wszystkie prawidłowe skrypt programu PowerShell zaoszczędził rozszerzenia psm1. To rozszerzenie umożliwia aparatu programu PowerShell do użycia szereg reguł i polecenia cmdlet na plik. Większość tych funkcji, czy istnieją ułatwią zainstalowanie kodu w innych systemach również zarządzać zakresu. Można również użyć w pliku manifestu modułu, który można opisać w bardziej złożonych instalacji i rozwiązań.

## <a name="writing-a-powershell-script-module"></a>Pisanie modułu programu skrypt programu PowerShell

Zapisywanie pliku psm1 prawidłowy skrypt programu PowerShell, a następnie zapisz ten plik w katalogu znajdujących się gdzie PowerShell może okazać się możesz utworzyć moduł skryptu. W tym folderze, możesz również umieścić wszelkie zasoby, należy uruchomić skrypt a także plik manifestu, który opisuje w programie PowerShell działania modułu.

#### <a name="to-create-a-basic-powershell-module"></a>Aby utworzyć podstawowy moduł programu PowerShell

1. Wykonaj istniejącego skryptu programu PowerShell i Zapisz skrypt za pomocą rozszerzenia psm1.

   Zapisywanie skryptu za pomocą psm1 rozszerzenia oznacza, że polecenia cmdlet modułu, można użyć takich jak [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), na nim. Te polecenia cmdlet istnieją głównie tak, aby można łatwo importować i eksportować kodu na systemach innych użytkowników. (Rozwiązanie alternatywne byłoby załadować zapasową swojego kodu na innych systemów, a następnie kropka źródła do aktywnej pamięci, która nie jest to szczególnie skalowalne rozwiązanie.) Aby uzyskać więcej informacji, zobacz **polecenia cmdlet modułu i zmienne** sekcji [moduły programu Windows PowerShell](./understanding-a-windows-powershell-module.md) należy pamiętać, że domyślnie wszystkie funkcje w skrypcie będą dostępne dla użytkowników, którzy zaimportować swoje psm1 plik, ale właściwości nie będzie.

   Przykładowy skrypt programu PowerShell uprawnionych Show-kalendarza, jest dostępna na końcu tego tematu.

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

2. Jeśli chcesz kontrolować dostęp użytkownika do określonych funkcji i właściwości, należy wywołać [ModuleMember eksportu](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) na końcu skryptu.

   Przykładowy kod w dolnej części strony ma tylko jedną funkcję, domyślnie będzie widoczne. Jednak zaleca się, że należy jawnie wywołać funkcje, które chcesz udostępnić, zgodnie z opisem w poniższym kodzie:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Można również ograniczyć, co jest importowany manifestu modułu. Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md) i [jak napisać Manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Jeśli masz moduły, które własny moduł musi zostać załadowany, można ich użyć z wywołania `Import-Module`, w górnej części własny moduł.

   `Import-Module` to polecenie cmdlet importuje moduł docelowych do systemu. W efekcie również służy w dowolnym momencie w procedurze do zainstalowania swój własny moduł, jak również. Przykładowy kod w dolnej części tej strony nie używa żadnych modułów importu. Jeśli została jednak one będą wyświetlane w górnej części pliku, zgodnie z opisem w poniższym kodzie:

   ```powershell
   Import-Module GenericModule
   ```

4. Jeśli użytkownik chce opisać modułu do systemu pomocy programu PowerShell, możesz to zrobić z komentarzami pomoc standard wewnątrz pliku lub przy użyciu dodatkowego pliku pomocy.

   Przykładowy kod w dolnej części tego tematu zawiera informacje pomocy w komentarzach. Jeśli tak, można również zapisać rozwinięte pliki XML, które zawierają dodatkową zawartość pomocy. Aby uzyskać więcej informacji, zobacz [zapisywania pomocy dla Windows modułów programu PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Jeśli masz dodatkowe moduły, pliki XML lub innej zawartości, którą chcesz spakować z modułu, możesz to zrobić z manifestu modułu.

   Manifest modułu jest plik, który zawiera nazwy inne moduły, układy katalogów, numery wersji, autor danych i innych rodzajów informacji. Program PowerShell używa pliku manifestu modułu do organizowania i wdrażać rozwiązania. Jednak ze względu na charakter stosunkowo proste, w tym przykładzie, plik manifestu nie jest wymagane. Aby uzyskać więcej informacji, zobacz [manifesty modułu](./how-to-write-a-powershell-module-manifest.md).

6. Do zainstalowania i uruchomienia modułu, Zapisz moduł do jednego z odpowiedniej ścieżki programu PowerShell, a wywołanie `Import-Module`.

   Ścieżki, w którym można zainstalować modułu znajdują się w `$env:PSModulePath` zmiennej globalnej. Na przykład będzie wspólną ścieżkę można zapisać modułu w systemie `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Należy koniecznie Utwórz folder modułu istnieje, nawet jeśli jest to plik psm1 jednego. Jeśli nie została zapisana modułu do jednej z tych ścieżek, trzeba będzie przekazać w lokalizacji modułu w wywołaniu `Import-Module`. (W przeciwnym razie program PowerShell będzie nie można go znaleźć.) Program PowerShell 3.0, począwszy od umieszczenie modułu w jednej ze ścieżek modułu programu PowerShell, nie trzeba jawnie go importują: po prostu poprosić użytkownika, wywołaj funkcję załaduje go automatycznie. Aby uzyskać więcej informacji na temat ścieżka modułu, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md) i [zmienna środowiskowa PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Aby usunąć moduł usługi active, wywoływania [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Należy pamiętać, że [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) spowoduje usunięcie modułu z aktywnej pamięci — go nie rzeczywistego usunięcia go z którym zostały zapisane pliki modułu.

### <a name="show-calendar-code-example"></a>Pokaż kalendarz przykładowy kod

Poniższy przykład jest moduł prosty skrypt, który zawiera pojedynczą funkcję o nazwie Show kalendarza. Funkcja ta wyświetla wizualną reprezentację kalendarza. Ponadto przykładu zawiera ciągi Pomoc programu PowerShell, streszczenie, opis, wartości parametrów oraz przykład. Należy pamiętać, że ostatni wiersz kodu wskazuje, że funkcja Pokaż kalendarz zostaną wyeksportowane jako członek modułu po zaimportowaniu modułu.

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
