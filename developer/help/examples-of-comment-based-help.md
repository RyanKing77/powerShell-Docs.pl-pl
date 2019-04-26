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
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="4f07d-102">Przykłady pomocy opartej na komentarzach</span><span class="sxs-lookup"><span data-stu-id="4f07d-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="4f07d-103">Ten temat zawiera przykładowy, które pokazują, jak korzystać z pomocy oparta na komentarzach dla skryptów i funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f07d-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="4f07d-104">Przykład 1: Pomoc oparta na komentarz dla funkcji</span><span class="sxs-lookup"><span data-stu-id="4f07d-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="4f07d-105">Poniższy kod przykładowej funkcji zawiera Pomoc oparta na komentarz.</span><span class="sxs-lookup"><span data-stu-id="4f07d-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="4f07d-106">Następujące dane wyjściowe zawierają wyniki polecenia Get-Help, który wyświetla Pomoc dotyczącą funkcji Dodaj rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="4f07d-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="4f07d-107">Przykład 2: Pomoc oparta na komentarz skryptu</span><span class="sxs-lookup"><span data-stu-id="4f07d-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="4f07d-108">Poniższy kod przykładowej funkcji zawiera Pomoc oparta na komentarz.</span><span class="sxs-lookup"><span data-stu-id="4f07d-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="4f07d-109">Zwróć uwagę, puste wiersze, między zamykającym **#>** i `Param` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4f07d-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="4f07d-110">W skrypcie, który nie ma `Param` instrukcji, musi istnieć co najmniej dwa puste wiersze między ostatnim komentarz w temacie pomocy i pierwszej deklaracji funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f07d-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="4f07d-111">Bez tych puste wiersze Get-Help kojarzy tematu pomocy przy użyciu funkcji, zamiast skryptu.</span><span class="sxs-lookup"><span data-stu-id="4f07d-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="4f07d-112">Następujące polecenie pobiera skrypt pomocy.</span><span class="sxs-lookup"><span data-stu-id="4f07d-112">The following command gets the script Help.</span></span> <span data-ttu-id="4f07d-113">Ponieważ skrypt nie jest n katalogu, który znajduje się w zmiennej środowiskowej Path polecenia Get-Help, który pobiera skrypt pomocy należy określić ścieżkę skryptu.</span><span class="sxs-lookup"><span data-stu-id="4f07d-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="4f07d-114">Przykład 3: Opisy parametrów w instrukcji Param</span><span class="sxs-lookup"><span data-stu-id="4f07d-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="4f07d-115">W tym przykładzie przedstawiono sposób wstawiania parameterdescriptions w `Param` instrukcji funkcji lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="4f07d-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="4f07d-116">Ten format jest najbardziej przydatne w przypadku krótkie opisy parametrów.</span><span class="sxs-lookup"><span data-stu-id="4f07d-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="4f07d-117">Wyniki są takie same wyniki, na przykład 1.</span><span class="sxs-lookup"><span data-stu-id="4f07d-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="4f07d-118">Get-Help interpretuje opisy parametrów, tak, jakby były towarzyszy `.Parameter` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4f07d-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="4f07d-119">Przykład 4:  Trwa przekierowywanie do pliku XML</span><span class="sxs-lookup"><span data-stu-id="4f07d-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="4f07d-120">Możesz tworzyć oparte na języku XML tematy pomocy dla funkcji i skryptów.</span><span class="sxs-lookup"><span data-stu-id="4f07d-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="4f07d-121">Pomoc oparta na komentarzach jest łatwiejsze do wdrożenia, oparty na składni XML pomocy jest wymagany, jeśli chcesz, aby bardziej precyzyjną kontrolę nad zawartością Pomocy lub jeśli tłumaczy tematów pomocy w wielu językach. Pierwszych kilka wierszy skryptu Month.ps1 aktualizacji można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4f07d-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="4f07d-122">Skrypt używa `.ExternalHelp` — słowo kluczowe, aby określić ścieżkę do tematu pomocy oparty na składni XML dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="4f07d-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="4f07d-123">Poniższy przykład pokazuje użycie `.ExternalHelp` — słowo kluczowe w funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f07d-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="4f07d-124">Przykład 5:  Trwa przekierowywanie do różnych tematów pomocy</span><span class="sxs-lookup"><span data-stu-id="4f07d-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="4f07d-125">Poniższy kod jest fragment początku wbudowane `Help` funkcji w programie Windows PowerShell, który wyświetla jeden ekran tekstu pomocy w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="4f07d-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="4f07d-126">Ponieważ tematu Pomocy dotyczącego polecenia cmdlet Get-Help zawiera opis funkcji pomocy, korzysta z funkcji pomocy `.ForwardHelpTargetName` i `.ForwardHelpCategory` słów kluczowych, aby przekierować użytkownika do tematu pomocy polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="4f07d-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="4f07d-127">Następujące polecenie używa tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f07d-127">The following command uses this feature.</span></span> <span data-ttu-id="4f07d-128">Gdy użytkownik wpisze funkcji pomocy polecenia Get-Help, Get-Help Wyświetla tematu Pomocy dotyczącego polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="4f07d-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

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