---
title: Jak zweryfikować zakresu Argument | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067794"
---
# <a name="how-to-validate-an-argument-range"></a>Jak zweryfikować zakres argumentów

Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell można użyć do sprawdzenia minimalne i maksymalne wartości argumentu parametru przed uruchomieniem polecenia cmdlet. Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateRange.

> [!NOTE]
> Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Aby sprawdzić poprawność zakresu argumentu

- Dodaj atrybut ValidateRange, jak pokazano w poniższym kodzie. W tym przykładzie określa zakres od 0 do 5 dla `InputData` parametru.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
