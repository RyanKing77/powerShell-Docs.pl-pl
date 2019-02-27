---
title: Jak zweryfikować wzorzec Argument | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846158"
---
# <a name="how-to-validate-an-argument-pattern"></a>Jak zweryfikować wzorzec argumentu

Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell można użyć do sprawdzenia wzorzec znak argumentu parametru przed uruchomieniem polecenia cmdlet. Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidatePattern.

> [!NOTE]
> Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Aby sprawdzić poprawność wzorzec argumentu

- Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie. W tym przykładzie określa wzorzec cztery cyfry, w którym każda cyfrę ma wartość od 0 do 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
