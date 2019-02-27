---
title: Deklaracji atrybutu polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 2bc03aaade1f18d48f65ecf5f9ee437ffaf07f92
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852010"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet, deklaracja atrybutu

Atrybut polecenia Cmdlet identyfikuje klasę jako polecenia cmdlet programu Microsoft .NET Framework i określa czasownik i rzeczownik używany do wywoływania polecenia cmdlet.

## <a name="syntax"></a>Składnia

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametry

`VerbName` ([System.String](/dotnet/api/System.String)) wymagane. Określa zlecenie polecenia cmdlet. To polecenie Określa akcję podejmowaną przez polecenie cmdlet. Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md) i [wymagane wskazówki dotyczące programowania](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) wymagane. Określa rzeczownik polecenia cmdlet. Ta rzeczownik Określa zasób, który polecenia cmdlet działają. Aby uzyskać więcej informacji na temat rzeczowniki poleceń cmdlet, zobacz [deklaracji polecenia Cmdlet](./cmdlet-class-declaration.md) i [zdecydowanie zalecane wskazówki dotyczące programowania](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` oznacza, że polecenie cmdlet obsługuje wywołania [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody, która udostępnia polecenia cmdlet monituje użytkownika przed wykonaniem akcji, która zmienia się system w sposób. `False`, wartość domyślna to wskazuje, polecenie cmdlet obsługuje wywołania [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody. Aby uzyskać więcej informacji na temat żądania potwierdzenia zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) o nazwie parametr opcjonalny. Określa, kiedy działania polecenia cmdlet powinny zostać potwierdzone przez wywołanie [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody. [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tylko zostanie wywołana, gdy wartość ConfirmImpact polecenia cmdlet (domyślnie średni) jest równa lub większa niż wartość `$ConfirmPreference` zmiennej. Ten parametr powinien być określony tylko wtedy, gdy `SupportsShouldProcess` określono parametr.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) o nazwie parametr opcjonalny. Określa domyślnego parametru zestawu, środowisko wykonawcze programu Windows PowerShell próbuje użyć, gdy nie można określić, które parametr skonfigurowany do używania. Należy zauważyć, że tej sytuacji można wyeliminować, wprowadzając unikatowy parametr każdego parametru, ustaw parametr obowiązkowy.

Istnieje jeden przypadek, w którym program Windows PowerShell nie można użyć domyślnego parametru, nawet jeśli jest określana nazwa domyślna parametru zestawu. Środowisko wykonawcze programu Windows PowerShell nie odróżnia zestawów parametrów, wyłącznie na typ obiektu. Na przykład, jeśli masz przyjmuje jeden zestaw parametrów, który przyjmuje ciąg jako ścieżkę pliku i inny zestaw **FileInfo** obiektu bezpośrednio, programu Windows PowerShell nie można określić, której parametr skonfigurowany do używania na podstawie wartości przekazane do polecenia cmdlet, ani nie używa domyślnego zestawu parametrów. W tym przypadku, nawet jeśli określisz nazwę zestawu domyślnego parametru, programu Windows PowerShell zgłasza komunikat o błędzie Ustaw parametr niejednoznaczne.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` Wskazuje, że polecenia cmdlet mogą być używane w obrębie transakcji. Gdy `True` określono środowiska uruchomieniowego programu Windows PowerShell dodaje `UseTransaction` parametru do listy parametrów polecenia cmdlet. `False`, wartość domyślna to wskazuje, że polecenie cmdlet nie można używać wewnątrz transakcji.

## <a name="remarks"></a>Uwagi

- Razem czasownik i rzeczownik służą do identyfikowania Twojego zarejestrowanego polecenia cmdlet i wywoływanie Twojego polecenia cmdlet w skrypcie.

- Gdy polecenie cmdlet jest wywoływany z konsoli programu Windows PowerShell, polecenie powinien wyglądać następujące polecenie:

**VerbName NounName**

- Wszystkie polecenia cmdlet, które zmieniają zasobów spoza środowiska Windows PowerShell powinna zawierać `SupportsShouldProcess` — słowo kluczowe gdy polecenia Cmdlet atrybut jest zadeklarowany, co pozwala polecenia cmdlet wywołać [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoda przed polecenia cmdlet wykonuje jej działaniem. Jeśli [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołania zwraca `false`, akcja nie powinny być pobierane. Aby uzyskać więcej informacji o potwierdzenie żądaniom wygenerowanym przez [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołań, zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

`Confirm` i `WhatIf` parametry polecenia cmdlet są dostępne tylko dla polecenia cmdlet, które obsługują [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołania.

## <a name="example"></a>Przykład

Poniższą definicję klasy używa atrybutu polecenia Cmdlet, aby zidentyfikować klasy .NET Framework dla **Get-Proc** polecenia cmdlet, które pobiera informacje dotyczące procesów uruchomionych na komputerze lokalnym.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Aby uzyskać więcej informacji na temat **Get-Proc** polecenia cmdlet, zobacz [samouczek GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
