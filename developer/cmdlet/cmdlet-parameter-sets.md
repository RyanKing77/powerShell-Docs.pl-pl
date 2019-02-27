---
title: Zestawy parametrów polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847698"
---
# <a name="cmdlet-parameter-sets"></a>Zestawy parametrów poleceń cmdlet

Programu Windows PowerShell używa zestawów parametrów, aby umożliwić pisanie jednego polecenia cmdlet, które może wykonywać różne akcje dla różnych scenariuszy. Zestawy parametrów pozwalają do udostępnienia różne parametry dla użytkownika i zwracać różne informacje, w oparciu o parametry określone przez użytkownika.

## <a name="examples-of-parameter-sets"></a>Przykłady zestawy parametrów

Na przykład `Get-EventLog` (udostępnione przez środowisko Windows PowerShell) polecenie cmdlet zwraca różne informacje w zależności od tego, czy użytkownik określi `List` lub `LogName` parametru. Jeśli `List` parametr jest określony, polecenie cmdlet zwraca informacje o plikach dzienników samodzielnie, ale nie dane zdarzenia zawierają. Jeśli `LogName` parametr jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w określonym dzienniku zdarzeń. `List` i `LogName` parametry zidentyfikować dwa zestawy oddzielny parametr.

## <a name="unique-parameter"></a>Unikatowy parametr

Każdy zestaw parametrów musi mieć unikatowy parametr, który w czasie wykonywania programu Windows PowerShell można użyć do udostępnienia zestaw odpowiednich parametrów. Jeśli to możliwe unikatowy parametr powinien być to parametr obowiązkowy. Jeśli parametr jest obowiązkowy, użytkownik jest zmuszony do określenia parametru, a środowisko wykonawcze programu Windows PowerShell można używać tego parametru do identyfikacji parametr, który został skonfigurowany do używania. Unikatowy parametr nie może być wymagane, jeśli Twojego polecenia cmdlet jest przeznaczony do uruchamiania bez określenia wszystkich parametrów.

## <a name="multiple-parameter-sets"></a>Wiele zestawów parametrów

Na poniższej ilustracji w kolumnie po lewej stronie jest wyświetlana trzech zestawów prawidłowego parametru. Parametr A jest unikatowy dla pierwszego zestawu parametrów, parametr B jest unikatowy dla drugiego zestawu parametrów i parametr C jest unikatowy dla trzeciego zestaw parametrów. Jednak w prawej kolumnie zestawów parametrów ma unikatowy parametr.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Wymagania dotyczące zestawu parametrów

Poniższe wymagania dotyczą wszystkich zestawów parametrów.

- Każdy zestaw parametrów musi mieć co najmniej jeden parametr unikatowy. Jeśli to możliwe należy ten parametr to parametr obowiązkowy.

- Zestaw parametrów, który zawiera wiele parametry pozycyjne, należy zdefiniować pozycji unikatowy dla każdego parametru. Nie dwa parametry pozycyjne, można określić taką samą pozycję.

- Można zadeklarować tylko jeden parametr w zestawie `ValueFromPipeline` — słowo kluczowe z wartością `true`. Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName` — słowo kluczowe z wartością `true`.

- Jeśli nie ustawiono parametru jest określona dla parametru, parametr należy do wszystkich zestawów parametrów.

## <a name="default-parameter-sets"></a>Domyślne zestawy parametrów

Jeśli zdefiniowano wiele zestawów parametrów, możesz użyć `DefaultParameterSetName` słowa kluczowego atrybutu polecenia Cmdlet, aby określić domyślny zestaw parametrów. Korzysta z domyślnego parametru, jeśli nie można określić, parametr, który został skonfigurowany do używania na podstawie informacji dostępnych za pomocą polecenia programu Windows PowerShell. Aby uzyskać więcej informacji o atrybucie polecenia Cmdlet, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarowanie zestawy parametrów

Aby utworzyć zestaw parametrów, należy określić `ParameterSetName` — słowo kluczowe, kiedy Deklarujesz atrybut Parameter dla każdego parametru w zestaw parametrów. Dla parametrów, które należą do wiele zestawów parametrów należy dodać atrybut parametru dla każdego zestawu parametrów. Dzięki temu można zdefiniować parametr w różny sposób dla każdego zestawu parametrów. Na przykład można zdefiniować parametr jako obowiązkowe w jednym zestawie i opcjonalnych w innym. Jednak każdy zestaw parametrów musi zawierać jeden parametr unikatowy.

W poniższym przykładzie `UserName` parametr jest unikatowy parametr Test01 zestaw parametrów, a `ComputerName` parametr jest unikatowy parametr Test02 zestaw parametrów. `SharedParam` Parametr należy do obu zestawów i jest wymagane dla parametru Test01 ustawić, ale opcjonalny w przypadku Test02 zestaw parametrów.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```