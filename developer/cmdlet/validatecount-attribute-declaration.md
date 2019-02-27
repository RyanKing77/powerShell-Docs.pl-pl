---
title: Deklaracji atrybutu ValidateCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849021"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount, deklaracja atrybutu

Atrybut ValidateCount określa minimalną i maksymalną liczbę argumentów, które mogą uzyskać parametr polecenia cmdlet.

## <a name="syntax"></a>Składnia

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametry

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) wymagane. Określa minimalną liczbę argumentów.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) wymagane. Określa maksymalną liczbę argumentów.

## <a name="remarks"></a>Uwagi

- Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Jeśli ten atrybut nie zostanie wywołany, z odpowiadającym mu parametrem polecenia cmdlet może mieć dowolną liczbę argumentów.

- Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:

    - `MinLength` i `MaxLength` parametry atrybutów nie mają wartości typu [System.Int32](/dotnet/api/System.Int32).

    - Wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.

- Atrybut ValidateCount jest definiowany przez [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Sposób deklarowania reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Sposób deklarowania reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
