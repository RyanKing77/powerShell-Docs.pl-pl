---
title: Runspace01 przykładowy kod (VB.NET) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12ee5382-95ba-41c7-8291-7f69a6f63514
caps.latest.revision: 7
ms.openlocfilehash: fbc90a6736d841fe184b86ab143809ad23c7977a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846851"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="56b97-102">Przykładowy kod Runspace01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="56b97-102">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="56b97-103">Poniżej przedstawiono przykłady kodu dla obszaru działania opisane w [tworzenia działa konsola aplikacji czy określone polecenie](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="56b97-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="56b97-104">Aby to zrobić, aplikacja wywołuje obszarem działania, a następnie wywołuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="56b97-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="56b97-105">(Zwróć uwagę, że ta aplikacja nie określa informacje o konfiguracji obszaru działania ani go jawnie tworzy potok). Polecenie, które jest wywoływane jest `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56b97-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="56b97-106">Poniżej przedstawiono przykłady kodu dla obszaru działania opisane w [tworzenia działa konsola aplikacji czy określone polecenie](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="56b97-106">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="56b97-107">Aby to zrobić, aplikacja wywołuje obszarem działania, a następnie wywołuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="56b97-107">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="56b97-108">(Zwróć uwagę, że ta aplikacja nie określa informacje o konfiguracji obszaru działania ani go jawnie tworzy potok). Polecenie, które jest wywoływane jest `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56b97-108">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="56b97-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="56b97-109">Code Sample</span></span>

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a><span data-ttu-id="56b97-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56b97-110">See Also</span></span>

[<span data-ttu-id="56b97-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56b97-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)