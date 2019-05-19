---
title: Deklaracji atrybutu ValidateLength | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855157"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength, deklaracja atrybutu

Atrybut ValidateLength określa minimalną i maksymalną liczbę znaków dla parametru w argumencie polecenia cmdlet. Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.

## <a name="syntax"></a>Składnia

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametry

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane. Określa minimalną liczbę znaków.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane. Określa maksymalną liczbę znaków.

## <a name="remarks"></a>Uwagi

- Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](./how-to-validate-parameter-input.md).

- Jeśli ten atrybut nie jest używana, odpowiedni argument parametru może być o dowolnej długości.

- Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:

    - Gdy wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.

    - Gdy `MaxLength` parametru atrybutu jest równa 0.

    - Jeśli argument nie jest ciągiem.

- Atrybut ValidateLength jest definiowany przez [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
