---
title: Walidacja danych wejściowych parametr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067148"
---
# <a name="validating-parameter-input"></a>Weryfikowanie danych wejściowych parametrów

Program PowerShell można sprawdzić poprawność Argumenty przekazane do parametrów polecenia cmdlet na kilka sposobów.
PowerShell można sprawdzić poprawność, długość, zakresu i wzorzec znaków argumentu.
Może on zweryfikować liczbę dostępnych argumentów (liczba).
Te reguły sprawdzania poprawności są definiowane przez atrybutów sprawdzania poprawności, które są zadeklarowane za pomocą atrybutu parametru właściwości publicznej klasy polecenia cmdlet.

Do sprawdzania poprawności argumentu parametru, w czasie wykonywania programu PowerShell używa informacji dostarczonych przez atrybuty weryfikacji, aby potwierdzić wartość parametru, przed uruchomieniem polecenia cmdlet.
Jeśli parametr wejściowy nie jest prawidłowy, użytkownik otrzymuje komunikat o błędzie.
Każdy parametr weryfikacji definiuje reguły sprawdzania poprawności, który jest wymuszany przez program PowerShell.

Program PowerShell wymusza reguły sprawdzania poprawności na podstawie następujących atrybutów.

### <a name="validatecount"></a>ValidateCount

Określa minimalną i maksymalną liczbę argumentów, akceptujące parametr.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Określa minimalną i maksymalną liczbę znaków w argumencie parametru.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Określa wyrażenie regularne, która weryfikuje argument parametru.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Określa minimalne i maksymalne wartości argumentu parametru.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Określa prawidłowe wartości dla argumentu parametru.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Sposób sprawdzania poprawności wprowadzania parametrów](./how-to-validate-parameter-input.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
