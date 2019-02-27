---
title: Deklaracji atrybutu ValidatePattern | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848825"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern, deklaracja atrybutu

Atrybut ValidatePattern Określa wzorzec wyrażenia regularnego weryfikującego argument parametru polecenia cmdlet. Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.

Wywołana ValidatePattern w ramach polecenia cmdlet środowiska uruchomieniowego programu Windows PowerShell argument parametru polecenia cmdlet jest konwertowany na ciąg, a następnie porównuje ciąg do wzorca, dostarczone przez atrybut ValidatePattern. Polecenie cmdlet jest uruchamiane tylko wtedy, gdy jest to reprezentacja ciągu przekonwertowanego argument i podanego wzorca dopasowania. Jeśli nie są zgodne, zostanie zgłoszony błąd w czasie wykonywania programu Windows PowerShell.

## <a name="syntax"></a>Składnia

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametry

`RegexString` ([System.String](/dotnet/api/System.String)) wymagane. Określa wyrażenie regularne, która weryfikuje argument parametru.

Opcje ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) o nazwie parametr opcjonalny. Bitowa kombinacja Określa [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flagi, które określają opcje wyrażeń regularnych.

## <a name="remarks"></a>Uwagi

- Ten atrybut może służyć tylko raz dla parametru.

- Możesz użyć `Option` parametru atrybutu do dalszego określenia wzorzec. Na przykład umożliwia wzorca z uwzględnieniem wielkości liter.

- Jeśli ten atrybut jest stosowany do kolekcji, każdy element w kolekcji musi być zgodna z wzorcem.

- Atrybut ValidatePattern jest definiowany przez [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
