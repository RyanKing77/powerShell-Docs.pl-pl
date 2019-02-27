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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848804"
---
# <a name="validating-parameter-input"></a>Weryfikowanie danych wejściowych parametrów

Program Windows PowerShell można sprawdzić poprawność Argumenty przekazane do parametrów polecenia cmdlet na kilka sposobów. Programu Windows PowerShell można sprawdzić poprawność, długość, zakresu i wzorzec znaków argumentu. Może on zweryfikować liczbę dostępnych argumentów (liczba). Te reguły sprawdzania poprawności są definiowane przez atrybutów sprawdzania poprawności, które są zadeklarowane za pomocą atrybutu parametru właściwości publicznej klasy polecenia cmdlet.

Do sprawdzania poprawności argumentu parametru, środowisko wykonawcze programu Windows PowerShell korzysta z informacji dostarczonych przez atrybuty weryfikacji Aby potwierdzić wartość parametru, przed uruchomieniem polecenia cmdlet. Jeśli parametr wejściowy nie jest prawidłowy, użytkownik otrzymuje komunikat o błędzie. Każdy parametr weryfikacji definiuje reguły sprawdzania poprawności, który jest wymuszany przez środowisko Windows PowerShell.

Program Windows PowerShell wymusza reguły sprawdzania poprawności na podstawie następujących atrybutów.

ValidateCount określa minimalną i maksymalną liczbę argumentów, akceptujące parametr. Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).

ValidateLength określa minimalną i maksymalną liczbę znaków w argumencie parametru. Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern określa wyrażenia regularnego weryfikującego argument parametru. Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).

ValidateRange określa minimalne i maksymalne wartości argumentu parametru. Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).

ValidateSet określa prawidłowe wartości dla argumentu parametru. Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Sposób sprawdzania poprawności wprowadzania parametrów](./how-to-validate-parameter-input.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
