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
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059562"
---
# <a name="users-requesting-confirmation"></a>Użytkownicy żądający potwierdzenia

Po określeniu wartości `true` dla `SupportsShouldProcess` parametru deklaracji atrybutu polecenia Cmdlet, użytkownicy mogą określić `Confirm` parametr w wierszu polecenia.

W środowisku domyślnym użytkownicy mogą określić `Confirm` parametru lub `"-Confirm:$true` tak, aby żądania potwierdzenia podczas [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoda jest wywoływana. To pomija [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) żądania potwierdzenia, nawet w przypadku operacji o dużym znaczeniu.

Jeśli `Confirm` nie zostanie określony, [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołanie zażąda potwierdzenia, jeśli `$ConfirmPreference` zmiennej preferencji jest równa lub większa niż `ConfirmImpact` ustawienie polecenia cmdlet lub dostawcy. Domyślne ustawienie `$ConfirmPreference` jest wysoki. W związku z tym w środowisku domyślnym tylko polecenia cmdlet i dostawców, które określają akcji o dużym znaczeniu żądania potwierdzenia.

Jeśli `Confirm` ma wartość false lub jeśli `"-Confirm:$false` jest określony, [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołanie zażąda potwierdzenia przez użytkownika i `$ConfirmPreference` zmiennej powłoki jest ignorowana.

## <a name="remarks"></a>Uwagi

- Dla poleceń cmdlet i dostawców, które określają `SupportsShouldProcess`, ale nie `ConfirmImpact`te akcje są obsługiwane jako akcje "średni wpływ" i nie będzie monitował domyślnie. Ich poziom wpływu jest niższy niż domyślne ustawienie `$ConfirmPreference` zmiennej preferencji.

- Jeśli użytkownik określi `Verbose` parametru, zostanie powiadomiony, operacji nawet jeśli nie są monitowani o potwierdzenie.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
