---
title: Użytkownicy z żądaniem potwierdzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846977"
---
# <a name="users-requesting-confirmation"></a>Użytkownicy żądający potwierdzenia

Po określeniu wartości `true` dla `SupportsShouldProcess` parametru deklaracji atrybutu polecenia Cmdlet, użytkownicy mogą określić `Confirm` parametr w wierszu polecenia.

W środowisku domyślnym użytkownicy mogą określić `Confirm` parametru lub `"-Confirm:$true` tak, aby żądania potwierdzenia podczas [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoda jest wywoływana. To pomija [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) żądania potwierdzenia, nawet w przypadku operacji o dużym znaczeniu.

Jeśli `Confirm` nie zostanie określony, [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołanie zażąda potwierdzenia, jeśli `$ConfirmPreference` zmiennej preferencji jest równa lub większa niż `ConfirmImpact` ustawienie polecenia cmdlet lub dostawcy. Domyślne ustawienie `$ConfirmPreference` jest wysoki. W związku z tym w środowisku domyślnym tylko polecenia cmdlet i dostawców, które określają akcji o dużym znaczeniu żądania potwierdzenia.

Jeśli `Confirm` ma wartość false lub jeśli `"-Confirm:$false` jest określony, [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołanie zażąda potwierdzenia przez użytkownika i `$ConfirmPreference` zmiennej powłoki jest ignorowana.

## <a name="remarks"></a>Uwagi

- Dla poleceń cmdlet i dostawców, które określają `SupportsShouldProcess`, ale nie `ConfirmImpact`te akcje są obsługiwane jako akcje "średni wpływ" i nie będzie monitował domyślnie. Ich poziom wpływu jest niższy niż domyślne ustawienie `$ConfirmPreference` zmiennej preferencji.

- Jeśli użytkownik określi `Verbose` parametru, zostanie powiadomiony, operacji nawet jeśli nie są monitowani o potwierdzenie.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
