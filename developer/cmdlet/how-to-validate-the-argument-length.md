---
title: Jak zweryfikować długość argumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847600"
---
# <a name="how-to-validate-the-argument-length"></a>Jak zweryfikować długość argumentu

Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź liczbę znaków (długość) argument parametru przed uruchomieniem polecenia cmdlet. Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateLength.

> [!NOTE]
> Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Aby sprawdzić długość argumentu

- Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie. W tym przykładzie określa, że długość argumentu powinien mieć długość 0 do 10 znaków.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
