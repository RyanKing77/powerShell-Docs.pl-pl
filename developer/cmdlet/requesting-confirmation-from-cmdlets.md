---
title: Żądanie potwierdzenia z polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844989"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Żądanie potwierdzenia z poziomu poleceń cmdlet

Polecenia cmdlet powinny żądania potwierdzenia, gdy chcesz wprowadzić zmiany w systemie, który znajduje się poza środowisko Windows PowerShell. Na przykład jeśli polecenie cmdlet jest dodać konto użytkownika lub zatrzymywanie procesu, polecenia cmdlet powinny wymagać potwierdzenia przez użytkownika, przed przechodzi. Z kolei jeśli polecenie cmdlet ma zostać zmieniona zmienną środowiska Windows PowerShell, polecenie cmdlet nie trzeba wymaga potwierdzenia.

W celu żądania potwierdzenia, polecenia cmdlet musi wskazywać, że obsługuje ona żądania potwierdzenia i musi on wywołać metodę [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody (opcjonalnie) aby wyświetlić komunikat z żądaniem potwierdzenia.

## <a name="supporting-confirmation-requests"></a>Obsługa żądania potwierdzenia

Obsługuje żądania potwierdzenia, polecenia cmdlet należy ustawić `SupportsShouldProcess` parametru atrybutu polecenia Cmdlet `true`. Dzięki temu `Confirm` i `WhatIf` parametry polecenia cmdlet, które są dostarczane przez środowisko Windows PowerShell. `Confirm` Parametr umożliwia użytkownikowi kontrolowanie, czy jest wyświetlany żądania potwierdzenia. `WhatIf` Parametr umożliwia użytkownikowi ustalić, czy polecenia cmdlet powinny wyświetlać komunikat lub wykonać jej działaniem. Nie należy ręcznie dodawać `Confirm` i `WhatIf` parametry do polecenia cmdlet.

Poniższy przykład pokazuje deklaracji atrybutu polecenia Cmdlet, który obsługuje żądania potwierdzenia.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Wywoływanie metod żądania potwierdzenia

W kodzie polecenia cmdlet, należy wywołać [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoda przed wykonaniem operacji, która zmienia się system. Projektowanie polecenia cmdlet, tak że jeśli to wywołanie zwraca wartość `false`, operacja nie jest wykonywane, i polecenia cmdlet przetwarza następnej operacji.

## <a name="calling-the-shouldcontinue-method"></a>Wywołanie metody ShouldContinue

Większość poleceń cmdlet żądania potwierdzenia przy użyciu tylko [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody. Jednak w niektórych przypadkach mogą wymagać dodatkowe potwierdzenie. W takich przypadkach należy uzupełnić [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołanie wywołaniem [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody. Pozwala to polecenie cmdlet lub dostawcę, aby bardziej precyzyjne kontrolowanie zakresu **tak na wszystko** odpowiedzi na monit o potwierdzenie.

Jeśli wywołuje polecenie cmdlet [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody, polecenia cmdlet należy również podać `Force` parametr przełącznika. Jeśli użytkownik określi `Force` po użytkownik wywołuje polecenie cmdlet, polecenie cmdlet nadal powinny wywoływać [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), należy pominąć, wywołanie metody, ale [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) spowoduje zgłoszenie wyjątku, gdy jest wywoływana przy użyciu środowiska nieinterakcyjnych których użytkownik nie można wyświetlić monitu. Dodawanie `Force` parametru gwarantuje, że można nadal można wykonać polecenia wywołana w środowisku nieinterakcyjnych.

Poniższy przykład pokazuje sposób wywoływania [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Zachowanie [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołania mogą się różnić w zależności od środowiska, w którym jest wywoływana polecenia cmdlet. Za pomocą wytycznych poprzedniego pomoże zapewnić spójne działania polecenia cmdlet z innymi poleceniami cmdlet, niezależnie od tego, w środowisku hosta.

Na przykład wywołanie [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody, zobacz [jak żądania potwierdzenia](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Określ poziom wpływu

Podczas tworzenia polecenia cmdlet, należy określić poziom wpływu (ważność) zmiany. Aby to zrobić, ustaw wartość `ConfirmImpact` parametru atrybutu polecenia Cmdlet na wysoki, średni lub niski. Można określić wartość dla `ConfirmImpact` tylko gdy określasz również `SupportsShouldProcess` parametr polecenia cmdlet.

Dla większości poleceń cmdlet, nie trzeba jawnie określić `ConfirmImpact`.  Zamiast tego użyj ustawienia domyślnego parametru, która jest. Jeśli ustawisz `ConfirmImpact` na wysoki, operacja zostanie potwierdzone domyślnie. Zarezerwuj to ustawienie dla bardzo uciążliwe akcje, takie jak ponowne formatowanie woluminu dysku twardego.

## <a name="calling-non-confirmation-methods"></a>Wywoływanie metod bez potwierdzenia

Jeśli polecenia cmdlet lub dostawca musi wysłać wiadomość, ale nie żądania potwierdzenia, wywołując następujących trzech metod. Unikaj używania [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metodę, aby wysyłać komunikaty z tych typów, ponieważ [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to są dane wyjściowe zwykłe dane wyjściowe polecenia cmdlet lub dostawcy, który sprawia, że pisanie skryptów trudne.

- Uwaga użytkownika i kontynuować wykonywanie operacji, można wywołać polecenia cmdlet lub dostawca [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody.

- Dodatkowe informacje, które użytkownik może pobrać za pomocą `Verbose` parametru polecenia cmdlet i dostawcy może wywołać [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody.

- Aby podać szczegóły na poziomie debugowania innym deweloperom lub pomocy technicznej, można wywołać polecenia cmdlet lub dostawca [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody. Użytkownik może pobrać te informacje przy użyciu `Debug` parametru.

Polecenia cmdlet i dostawców należy najpierw wywołać następujące metody umożliwiające żądania potwierdzenia przed ich podjął próbę wykonania operacji, która zmienia systemu poza programu Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Mogą to zrobić, wywołując [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody, która wyświetli monit o potwierdzenie operacji, w oparciu o sposób użytkownik wywołał polecenie.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
