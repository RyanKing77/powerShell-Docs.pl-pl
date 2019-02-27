---
title: Tworzenie przepływu pracy przy użyciu skryptu programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844744"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="34370-102">Tworzenie przepływu pracy przy użyciu skryptu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34370-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="34370-103">Możesz utworzyć przepływ pracy, przez napisanie skryptu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34370-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="34370-104">Aby utworzyć przepływ pracy, użyj przepływu pracy — słowo kluczowe, następuje nazwa przepływu pracy przed treść skryptu.</span><span class="sxs-lookup"><span data-stu-id="34370-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="34370-105">Przykład:</span><span class="sxs-lookup"><span data-stu-id="34370-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="34370-106">Przepływ pracy można znaleźć w taki sam sposób jak w przypadku innych poleceń programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34370-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="34370-107">Implementowanie równoległe i sekwencyjne</span><span class="sxs-lookup"><span data-stu-id="34370-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="34370-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) obsługuje wykonanie czynności równolegle.</span><span class="sxs-lookup"><span data-stu-id="34370-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="34370-109">Aby zaimplementować tę funkcję w skrypcie programu Windows PowerShell, należy użyć `parallel` — słowo kluczowe przed blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="34370-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="34370-110">Można również użyć `foreach -parallel` konstrukcji do iterowania po kolekcji obiektów równolegle.</span><span class="sxs-lookup"><span data-stu-id="34370-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="34370-111">Do grupy działań są wykonywane w kolejności sekwencyjnej, w ramach bloku równoległego, należy ująć tej grupy działań w bloku skryptu i poprzedzać bloku ze słowem kluczowym sekwencji.</span><span class="sxs-lookup"><span data-stu-id="34370-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="34370-112">Przyłączanie komputerów do domeny</span><span class="sxs-lookup"><span data-stu-id="34370-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="34370-113">Poniższy skrypt tworzy przepływ pracy, który umożliwia sprawdzenie stanu domeny grupy komputerów określonych przez użytkownika, jeśli nie są już połączone, a następnie umożliwia sprawdzenie stanu dołączania ich do domeny.</span><span class="sxs-lookup"><span data-stu-id="34370-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="34370-114">To jest wersja skryptu przepływu pracy XAML, które wyjaśniono w [tworzenia przepływu pracy przy użyciu programu Windows PowerShell działania](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="34370-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```