---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068100"
---
# <a name="getproc-tutorial"></a>GetProc — samouczek

Ta sekcja zawiera samouczek tworzenia polecenia cmdlet Get-Proc, która jest bardzo podobne do [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) dostarczane przez środowisko Windows PowerShell polecenia cmdlet. Ten samouczek zawiera fragmenty kodu, które ilustrują implementacji poleceń cmdlet oraz objaśnienia dotyczące kodu.

## <a name="topics-in-this-tutorial"></a>Tematy w tym samouczku

Tematy w tym samouczku są przeznaczone do przeczytania po kolei, za pomocą każdego tematu, opierając się na co zostało omówione w poprzednim temacie.

[Tworzenie polecenia Cmdlet bez parametrów](./creating-a-cmdlet-without-parameters.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które pobiera informacje z komputera lokalnego bez użycia parametrów, a następnie zapisuje informacje do potoku.

[Dodawanie parametrów wejściowych tego procesu wiersza polecenia](./adding-parameters-that-process-command-line-input.md) tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc, tak aby polecenie cmdlet może przetwarzać dane wejściowe na podstawie jawnych obiektów przekazywane do polecenia cmdlet. Implementacja opisane tutaj pobiera procesów na podstawie ich nazwy, a następnie zapisuje informacje do potoku.

[Dodawanie parametrów tego procesu wejście potokowe](./adding-parameters-that-process-pipeline-input.md) tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc, tak aby polecenie cmdlet może przetwarzać obiektów przekazywane do niego za pośrednictwem potoku. Polecenia cmdlet wdrażania opisanych tutaj pobiera procesów na podstawie obiektów przekazywane do polecenia cmdlet, a następnie zapisuje informacje do potoku.

[Dodawanie niekończące raportowanie błędów do polecenia Cmdlet usługi](./adding-non-terminating-error-reporting-to-your-cmdlet.md) w tej sekcji opisano sposób dodawania niekończące raportów o błędach do polecenia cmdlet. Implementacja opisane w tym miejscu wykrywa błędy niekończące, które występują podczas przetwarzania danych wejściowych i zapisuje rekord błędu strumienia błędów.

## <a name="see-also"></a>Zobacz też

[Tworzenie polecenia Cmdlet bez parametrów](./creating-a-cmdlet-without-parameters.md)

[Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia](./adding-parameters-that-process-command-line-input.md)

[Dodając parametry, z których potok przetwarzania danych wejściowych](./adding-parameters-that-process-pipeline-input.md)

[Dodawanie niekończące raportów o błędach do Twojego polecenia Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
