---
title: Jak obsługiwać transakcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067862"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="898d8-102">Jak obsługiwać transakcje</span><span class="sxs-lookup"><span data-stu-id="898d8-102">How to Support Transactions</span></span>

<span data-ttu-id="898d8-103">Ten przykład pokazuje elementy podstawowe kodu, które dodano obsługę dla transakcji do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="898d8-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="898d8-104">Aby uzyskać więcej informacji na temat obsługi transakcji w programie Windows PowerShell, zobacz [o transakcji][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="898d8-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="898d8-105">Do obsługi transakcji</span><span class="sxs-lookup"><span data-stu-id="898d8-105">To support transactions</span></span>

1. <span data-ttu-id="898d8-106">Kiedy Deklarujesz atrybut polecenia Cmdlet, należy określić, to polecenie cmdlet obsługuje transakcji.</span><span class="sxs-lookup"><span data-stu-id="898d8-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="898d8-107">Gdy polecenie cmdlet obsługuje transakcje, programu Windows PowerShell dodaje `UseTransaction` parametru do polecenia cmdlet, po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="898d8-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="898d8-108">W ramach jednej metody przetwarzania danych wejściowych, Dodaj `if` bloku, aby określić, czy transakcja jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="898d8-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="898d8-109">Jeśli `if` instrukcji jest rozpoznawana jako `true`, akcje w ramach niniejszych mogą być wykonywane w kontekście bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="898d8-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="898d8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="898d8-110">See Also</span></span>

[<span data-ttu-id="898d8-111">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="898d8-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
