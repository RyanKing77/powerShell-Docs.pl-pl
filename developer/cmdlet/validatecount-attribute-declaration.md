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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983902"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount, deklaracja atrybutu

Atrybut ValidateCount określa minimalną i maksymalną liczbę argumentów, które mogą uzyskać parametr polecenia cmdlet.

## <a name="syntax"></a>Składnia

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametry

`MinLength` ([System.Int32][]) wymagane. Określa minimalną liczbę argumentów.

`MaxLength`([System.Int32][]) wymagane. Określa maksymalną liczbę argumentów.

## <a name="remarks"></a>Uwagi

- Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [sposób sprawdzania poprawności liczby argumentów][].

- Jeśli ten atrybut nie zostanie wywołany, z odpowiadającym mu parametrem polecenia cmdlet może mieć dowolną liczbę argumentów.

- Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:

    - `MinLength` i `MaxLength` parametry atrybutów nie mają wartości typu [System.Int32][].

    - Wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.

- Atrybut ValidateCount jest definiowany przez [System.Management.Automation.ValidateCountAttribute][] klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.ValidateCountAttribute][]

[Sposób sprawdzania poprawności liczby argumentów][]

[Zapisywanie polecenia Cmdlet programu Windows PowerShell][]

[Sposób sprawdzania poprawności liczby argumentów]: how-to-validate-an-argument-count.md
[Zapisywanie polecenia Cmdlet programu Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
