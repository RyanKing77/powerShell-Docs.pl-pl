---
title: Przykłady pomocy w sieci komentarz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083505"
---
# <a name="examples-of-comment-based-help"></a>Przykłady pomocy opartej na komentarzach

Ten temat zawiera przykładowy, które pokazują, jak korzystać z pomocy oparta na komentarzach dla skryptów i funkcji.

## <a name="example-1-comment-based-help-for-a-function"></a>Przykład 1: Pomoc oparta na komentarz dla funkcji

 Poniższy kod przykładowej funkcji zawiera Pomoc oparta na komentarz.

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

Następujące dane wyjściowe zawierają wyniki polecenia Get-Help, który wyświetla Pomoc dotyczącą funkcji Dodaj rozszerzenie.

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a>Przykład 2: Pomoc oparta na komentarz skryptu

Poniższy kod przykładowej funkcji zawiera Pomoc oparta na komentarz.

Zwróć uwagę, puste wiersze, między zamykającym **#>** i `Param` instrukcji. W skrypcie, który nie ma `Param` instrukcji, musi istnieć co najmniej dwa puste wiersze między ostatnim komentarz w temacie pomocy i pierwszej deklaracji funkcji. Bez tych puste wiersze Get-Help kojarzy tematu pomocy przy użyciu funkcji, zamiast skryptu.

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

Następujące polecenie pobiera skrypt pomocy. Ponieważ skrypt nie jest n katalogu, który znajduje się w zmiennej środowiskowej Path polecenia Get-Help, który pobiera skrypt pomocy należy określić ścieżkę skryptu.

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Przykład 3: Opisy parametrów w instrukcji Param

W tym przykładzie przedstawiono sposób wstawiania parameterdescriptions w `Param` instrukcji funkcji lub skryptu. Ten format jest najbardziej przydatne w przypadku krótkie opisy parametrów.

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

Wyniki są takie same wyniki, na przykład 1. Get-Help interpretuje opisy parametrów, tak, jakby były towarzyszy `.Parameter` — słowo kluczowe.

## <a name="example-4--redirecting-to-an-xml-file"></a>Przykład 4:  Trwa przekierowywanie do pliku XML

Możesz tworzyć oparte na języku XML tematy pomocy dla funkcji i skryptów. Pomoc oparta na komentarzach jest łatwiejsze do wdrożenia, oparty na składni XML pomocy jest wymagany, jeśli chcesz, aby bardziej precyzyjną kontrolę nad zawartością Pomocy lub jeśli tłumaczy tematów pomocy w wielu językach. Pierwszych kilka wierszy skryptu Month.ps1 aktualizacji można znaleźć w poniższym przykładzie. Skrypt używa `.ExternalHelp` — słowo kluczowe, aby określić ścieżkę do tematu pomocy oparty na składni XML dla skryptu.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

Poniższy przykład pokazuje użycie `.ExternalHelp` — słowo kluczowe w funkcji.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Przykład 5:  Trwa przekierowywanie do różnych tematów pomocy

Poniższy kod jest fragment początku wbudowane `Help` funkcji w programie Windows PowerShell, który wyświetla jeden ekran tekstu pomocy w danym momencie. Ponieważ tematu Pomocy dotyczącego polecenia cmdlet Get-Help zawiera opis funkcji pomocy, korzysta z funkcji pomocy `.ForwardHelpTargetName` i `.ForwardHelpCategory` słów kluczowych, aby przekierować użytkownika do tematu pomocy polecenia cmdlet Get-Help.

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

Następujące polecenie używa tej funkcji. Gdy użytkownik wpisze funkcji pomocy polecenia Get-Help, Get-Help Wyświetla tematu Pomocy dotyczącego polecenia cmdlet Get-Help.

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```