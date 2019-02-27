---
title: Przykłady kodu, polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 39c0814faf72cdb4b24730acb2ae429a2f465b32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851800"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="ae9c8-102">Przykłady kodu poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae9c8-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="ae9c8-103">Ta sekcja zawiera przykłady kodu polecenie cmdlet, których można użyć do rozpoczęcia pisania własnych poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae9c8-104">Aby uzyskać instrukcje krok po kroku dotyczące pisania poleceń cmdlet, zobacz [samouczki dotyczące pisania poleceń cmdlet](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="ae9c8-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ae9c8-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ae9c8-105">In This Section</span></span>

<span data-ttu-id="ae9c8-106">[Jak pisać proste polecenie Cmdlet](./how-to-write-a-simple-cmdlet.md) ten przykład pokazuje podstawową strukturę kodu polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="ae9c8-107">[Jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md) ten przykład pokazuje sposób deklarowania typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="ae9c8-108">[Jak zadeklarować parametr ustawia](./how-to-declare-parameter-sets.md) ten przykład pokazuje sposób deklarowania zestawów parametrów, które można zmienić akcję wykonuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="ae9c8-109">[Jak sprawdzić poprawność danych wejściowych z parametru](./how-to-validate-parameter-input.md) te przykłady pokazują, jak sprawdzanie poprawności danych wejściowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="ae9c8-110">[Jak deklarować parametrów dynamicznych](./how-to-declare-dynamic-parameters.md) ten przykład pokazuje sposób deklarowania parametr, który zostanie dodany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="ae9c8-111">[Jak wywołać skrypty w ramach polecenia Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) w tym przykładzie pokazano, jak wywołać skrypt, który jest dostarczany do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="ae9c8-112">[Sposób przesłonięcia metody przetwarzania danych wejściowych](./how-to-override-input-processing-methods.md) podstawowa struktura służy do zastępowania metod BeginProcessing, ProcessRecord i EndProcessing w tych przykładach.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="ae9c8-113">[Jak ShouldProcess telefonów](./how-to-request-confirmations.md) ten przykład przedstawia sposób, w jaki [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)metody powinien zostać wywołany z poziomu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="ae9c8-114">[Sposób obsługi transakcji](./how-to-support-transactions.md) ten przykład przedstawia sposób wskazać, że polecenie cmdlet obsługuje transakcje i jak implementować akcję, która zostanie podjęta, gdy polecenie cmdlet jest używane w obrębie transakcji.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="ae9c8-115">[Jak obsługiwać zadania](./how-to-support-jobs.md) w tym przykładzie pokazano, jak obsługiwać zadania podczas pisania poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="ae9c8-116">[Opis wywoływania polecenia Cmdlet z w ramach polecenia Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) w tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet, dzięki czemu można dodawać funkcje wywoływane polecenia cmdlet do polecenia cmdlet, tworzysz.</span><span class="sxs-lookup"><span data-stu-id="ae9c8-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9c8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae9c8-117">See Also</span></span>

[<span data-ttu-id="ae9c8-118">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae9c8-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
