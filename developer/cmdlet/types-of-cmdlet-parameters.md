---
title: Typy parametrów polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059579"
---
# <a name="types-of-cmdlet-parameters"></a>Typy parametrów poleceń cmdlet

W tym temacie opisano różne typy parametrów, które można zadeklarować w poleceniach cmdlet. Parametry polecenia cmdlet można być pozycyjne, nazwanych, wymagane, opcjonalne lub parametry przełączników.

## <a name="positional-and-named-parameters"></a>Parametry pozycyjne i nazwane

Wszystkie parametry polecenia cmdlet są parametrów nazwanych i pozycyjnych. Parametr o nazwie wymaga, wpisz nazwę parametru i argumentów podczas wywoływania polecenia cmdlet. Parametr pozycyjne wymaga jedynie, wpisz argumenty w kolejności względnej. System następnie mapuje pierwszy parametr pozycyjne pierwszy argument bez nazwy. System mapuje drugi nienazwany argument do drugiego parametru nienazwanego i tak dalej. Domyślnie wszystkie parametry polecenia cmdlet są nazwanych parametrów.

Aby zdefiniować nazwany parametr, Pomiń `Position` — słowo kluczowe w **parametru** atrybutu deklaracji, jak pokazano w poniższej deklaracji parametru.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Aby zdefiniować parametr pozycyjne, Dodaj `Position` — słowo kluczowe w parametrze deklaracji atrybutu, a następnie określić położenie. W poniższym przykładzie `UserName` parametru jest zadeklarowany jako parametr pozycyjne od pozycji 0. Oznacza to, że pierwszy argument wywołania będą automatycznie powiązane tego parametru.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Polecenia cmdlet dobrej projekcie są zalecane, parametry używane przez większość może być zadeklarowana jako parametry pozycyjne, tak, aby użytkownik nie musiał po uruchomieniu polecenia cmdlet, wprowadź nazwę parametru.

Parametry pozycyjne i nazwane akceptuje żadnych argumentów jednego lub wielu argumentów rozdzielonych przecinkami. Wiele argumentów są dozwolone tylko wtedy, gdy parametr akceptuje kolekcja przykład tablicy ciągów. Może mieszać parametry pozycyjne i nazwane, w tym samym poleceniu cmdlet. W takim przypadku system pobiera argumenty nazwane najpierw, a następnie próbuje zamapować pozostałe nienazwane argumenty pozycyjne parametrów.

W następujących poleceniach pokazano różne sposoby, w którym można określić pojedynczych i wielu argumenty dla parametrów `Get-Command` polecenia cmdlet. Należy zauważyć, że w ostatnich dwóch próbek **— nazwa** nie musi być określona, ponieważ `Name` parametr jest zdefiniowany jako parametr pozycyjne.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obowiązkowych i opcjonalnych parametrów

Parametry polecenia cmdlet można także zdefiniować jako wymagane lub opcjonalne parametry. (To parametr obowiązkowy przed należy określić w czasie wykonywania programu Windows PowerShell wywołuje polecenie cmdlet.)  Domyślnie parametry są definiowane jako opcjonalną.

Aby zdefiniować to parametr obowiązkowy, należy dodać `Mandatory` — słowo kluczowe w parametrze atrybutu deklaracji i ustaw ją na `true`, jak pokazano w poniższej deklaracji parametru.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Aby zdefiniować parametr opcjonalny, Pomiń `Mandatory` — słowo kluczowe w **parametru** atrybutu deklaracji, jak pokazano w poniższej deklaracji parametru.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parametry przełączników

Program Windows PowerShell udostępnia [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ, który pozwala na zdefiniowanie parametru którego wartość jest automatycznie ustawiana na `false` Jeśli parametr nie zostanie określony, gdy polecenie cmdlet jest wywoływana. Zawsze, gdy jest to możliwe, należy użyć parametrów przełącznika zamiast logiczna parametrów.

Należy wziąć pod uwagę poniższego przykładu. Domyślnie kilka poleceń cmdlet programu Windows PowerShell nie przekazuj obiekt danych wyjściowych w dół do potoku. Jednak te polecenia cmdlet mają `PassThru` Przełącz parametr, który zastępuje domyślne zachowanie. Jeśli `PassThru` parametr jest określony, wywołanego tych poleceń cmdlet, polecenie cmdlet zwraca obiekt danych wyjściowych do potoku.

Jeśli potrzebujesz parametr ma wartość domyślną `true` gdy parametr nie jest określony w wywołaniu, należy wziąć pod uwagę wycofywanie sense parametru. Dla przykładu, zamiast ustawiać atrybutu parametru na wartość logiczną `true`, zadeklarować właściwości jako [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typu, a następnie ustaw wartość domyślna parametru `false`.

Aby zdefiniować parametr przełącznika, należy zadeklarować właściwości jako [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ, jak pokazano w następującym przykładzie.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Aby polecenie cmdlet działa w parametrze, jeśli nie zostanie określony, użyj następującej struktury w ramach jednej metody przetwarzania danych wejściowych.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
