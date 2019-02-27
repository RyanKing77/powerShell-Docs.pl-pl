---
title: Deklarowanie właściwości jako parametry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850575"
---
# <a name="declaring-properties-as-parameters"></a>Deklarowanie właściwości jako parametrów

Ten temat zawiera podstawowe informacje, które należy zrozumieć przed możesz deklarować parametry polecenia cmdlet.

Aby zadeklarować parametry polecenia cmdlet w swojej klasie polecenia cmdlet, zdefiniuj właściwości publiczne, które reprezentują każdego parametru, a następnie dodaj jeden lub więcej atrybutów parametr do każdej właściwości. Środowisko wykonawcze programu Windows PowerShell używa atrybuty parametru do identyfikacji właściwość jako parametr polecenia cmdlet. Podstawowa składnia do deklarowania atrybutu parametru jest `[Parameter()]`.

Oto przykład właściwości zdefiniowane jako wymaganego parametru.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Poniżej przedstawiono niektóre kwestie, pamiętaj o parametrach.

- Parametr musi być jawnie oznaczone jako publiczne. Parametry, które nie są oznaczane jako publicznego domyślnego wewnętrznego i nie zostanie znaleziony w czasie wykonywania programu Windows PowerShell.

- Parametry powinna być zdefiniowana jako typy Microsoft .NET Framework w celu zapewnienia lepszej Walidacja parametru. Na przykład parametry, które są ograniczone do jednej wartości z zestawu wartości powinna być zdefiniowana jako typ wyliczenia. Parametry, które przyjmują wartość identyfikatora URI (Uniform Resource) powinny być typu [System.Uri](/dotnet/api/System.Uri).

- Unikaj parametrów ciągu podstawowe właściwości wszystkie elementy oprócz dowolnego tekstu.

- Możesz dodać parametr do dowolnej liczby zestawów parametrów. Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [zestawy parametrów polecenia Cmdlet](./cmdlet-parameter-sets.md).

Program Windows PowerShell udostępnia również zestaw wspólnych parametrów, które są automatycznie dostępne dla każdego polecenia cmdlet. Aby uzyskać więcej informacji na temat tych parametrów i ich aliasy, zobacz [wspólne parametry polecenia Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Zobacz też

[Polecenia cmdlet typowych parametrów](./common-parameter-names.md)

[Typy parametrów polecenia Cmdlet](./types-of-cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
