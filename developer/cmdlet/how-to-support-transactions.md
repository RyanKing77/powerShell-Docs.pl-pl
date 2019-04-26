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
# <a name="how-to-support-transactions"></a>Jak obsługiwać transakcje

Ten przykład pokazuje elementy podstawowe kodu, które dodano obsługę dla transakcji do polecenia cmdlet.

> [!IMPORTANT]
> Aby uzyskać więcej informacji na temat obsługi transakcji w programie Windows PowerShell, zobacz [o transakcji][about_Transactions].

## <a name="to-support-transactions"></a>Do obsługi transakcji

1. Kiedy Deklarujesz atrybut polecenia Cmdlet, należy określić, to polecenie cmdlet obsługuje transakcji.
   Gdy polecenie cmdlet obsługuje transakcje, programu Windows PowerShell dodaje `UseTransaction` parametru do polecenia cmdlet, po jej uruchomieniu.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. W ramach jednej metody przetwarzania danych wejściowych, Dodaj `if` bloku, aby określić, czy transakcja jest dostępna.
   Jeśli `if` instrukcji jest rozpoznawana jako `true`, akcje w ramach niniejszych mogą być wykonywane w kontekście bieżącej transakcji.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
