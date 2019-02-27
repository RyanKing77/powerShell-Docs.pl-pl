---
title: RunSpace03 przykładowy kod (VB.NET) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3611d66b-19da-4477-ac05-2e5e68312f51
caps.latest.revision: 6
ms.openlocfilehash: 77d0871953950374d2eece65bead0f2075b1138b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847712"
---
# <a name="runspace03-vbnet-code-sample"></a><span data-ttu-id="eaa33-102">Przykładowy kod RunSpace03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="eaa33-102">RunSpace03 (VB.NET) Code Sample</span></span>

<span data-ttu-id="eaa33-103">Oto VB.NET kodu źródłowego dla aplikacji konsoli opisanego w [tworzenia działa konsola aplikacji czy określony skrypt](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="eaa33-103">Here is the VB.NET source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="eaa33-104">W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który pobiera przetwarzania informacji dla listy nazw procesu przekazywane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="eaa33-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information for the list of process names passed into the script.</span></span> <span data-ttu-id="eaa33-105">Pokazuje, jak przekazać obiekty wejściowe do skryptu oraz jak pobierać obiektów błędu, a także obiekty danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="eaa33-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>
<span data-ttu-id="eaa33-106">Oto VB.NET kodu źródłowego dla aplikacji konsoli opisanego w [tworzenia działa konsola aplikacji czy określony skrypt](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="eaa33-106">Here is the VB.NET source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="eaa33-107">W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który pobiera przetwarzania informacji dla listy nazw procesu przekazywane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="eaa33-107">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information for the list of process names passed into the script.</span></span> <span data-ttu-id="eaa33-108">Pokazuje, jak przekazać obiekty wejściowe do skryptu oraz jak pobierać obiektów błędu, a także obiekty danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="eaa33-108">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="eaa33-109">Możesz pobrać plik źródłowy VB.NET (runspace03.vb) omawiany w tym przykładzie przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="eaa33-109">You can download the VB.NET source file (runspace03.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eaa33-110">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="eaa33-110">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="eaa33-111">Możesz pobrać plik źródłowy VB.NET (runspace03.vb) omawiany w tym przykładzie przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="eaa33-111">You can download the VB.NET source file (runspace03.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="eaa33-112">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="eaa33-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="eaa33-113">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="eaa33-113">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="eaa33-114">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="eaa33-114">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace03

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script that retrieves process information for the
        ''' list of process names passed into the script.
        ''' It shows how to pass input objects to a script and
        ''' how to retrieve error objects as well as the output objects.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that were generated
        '''    during the execution of that script.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of processes to look for
            Dim processNames() As String = {"lsass", "nosuchprocess", _
                "services", "nosuchprocess2"}

            ' The script to run to get these processes. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | get-process -name {$_}"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            Dim errors As System.Collections.IList = Nothing
            Dim result As PSObject
            For Each result In invoker.Invoke(script, processNames, errors)
                Console.WriteLine("{0,-20} {1}", _
                result.Members("ProcessName").Value, _
                result.Members("HandleCount").Value)
            Next result

            ' Now process any error records that were generated while
            ' running the script.
            Console.WriteLine(vbCrLf & _
                "The following non-terminating errors occurred:" & vbCrLf)
            If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                Dim err As PSObject
                For Each err In errors
                    System.Console.WriteLine("    error: {0}", err.ToString())
                Next err
            End If
            System.Console.WriteLine(vbCRLF & "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main

    End Class 'Runspace03

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace03.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace03.vb#L09-L83 "Runspace03.vb")] -->

## <a name="see-also"></a><span data-ttu-id="eaa33-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eaa33-115">See Also</span></span>

[<span data-ttu-id="eaa33-116">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="eaa33-116">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="eaa33-117">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eaa33-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)