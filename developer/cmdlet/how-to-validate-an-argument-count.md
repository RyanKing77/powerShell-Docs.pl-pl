---
title: Sposób sprawdzania poprawności liczby argumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067811"
---
# <a name="how-to-validate-an-argument-count"></a>Jak zweryfikować liczbę argumentów

W tym przykładzie pokazano, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź liczbę argumentów (liczba), które akceptuje parametr przed uruchomieniem polecenia cmdlet. Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateCount.

> [!NOTE]
> Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Aby sprawdzić poprawność liczba argumentów

- Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie. W tym przykładzie określa, że parametr przyjmuje jeden argument lub maksymalnie trzy argumenty.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
