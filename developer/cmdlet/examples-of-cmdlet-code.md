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
# <a name="examples-of-cmdlet-code"></a>Przykłady kodu poleceń cmdlet

Ta sekcja zawiera przykłady kodu polecenie cmdlet, których można użyć do rozpoczęcia pisania własnych poleceń cmdlet.

> [!IMPORTANT]
> Aby uzyskać instrukcje krok po kroku dotyczące pisania poleceń cmdlet, zobacz [samouczki dotyczące pisania poleceń cmdlet](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>W tej sekcji

[Jak pisać proste polecenie Cmdlet](./how-to-write-a-simple-cmdlet.md) ten przykład pokazuje podstawową strukturę kodu polecenie cmdlet.

[Jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md) ten przykład pokazuje sposób deklarowania typów parametrów.

[Jak zadeklarować parametr ustawia](./how-to-declare-parameter-sets.md) ten przykład pokazuje sposób deklarowania zestawów parametrów, które można zmienić akcję wykonuje polecenie cmdlet.

[Jak sprawdzić poprawność danych wejściowych z parametru](./how-to-validate-parameter-input.md) te przykłady pokazują, jak sprawdzanie poprawności danych wejściowych parametrów.

[Jak deklarować parametrów dynamicznych](./how-to-declare-dynamic-parameters.md) ten przykład pokazuje sposób deklarowania parametr, który zostanie dodany w czasie wykonywania.

[Jak wywołać skrypty w ramach polecenia Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) w tym przykładzie pokazano, jak wywołać skrypt, który jest dostarczany do polecenia cmdlet.

[Sposób przesłonięcia metody przetwarzania danych wejściowych](./how-to-override-input-processing-methods.md) podstawowa struktura służy do zastępowania metod BeginProcessing, ProcessRecord i EndProcessing w tych przykładach.

[Jak ShouldProcess telefonów](./how-to-request-confirmations.md) ten przykład przedstawia sposób, w jaki [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)metody powinien zostać wywołany z poziomu polecenia cmdlet.

[Sposób obsługi transakcji](./how-to-support-transactions.md) ten przykład przedstawia sposób wskazać, że polecenie cmdlet obsługuje transakcje i jak implementować akcję, która zostanie podjęta, gdy polecenie cmdlet jest używane w obrębie transakcji.

[Jak obsługiwać zadania](./how-to-support-jobs.md) w tym przykładzie pokazano, jak obsługiwać zadania podczas pisania poleceń cmdlet.

[Opis wywoływania polecenia Cmdlet z w ramach polecenia Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) w tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet, dzięki czemu można dodawać funkcje wywoływane polecenia cmdlet do polecenia cmdlet, tworzysz.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
