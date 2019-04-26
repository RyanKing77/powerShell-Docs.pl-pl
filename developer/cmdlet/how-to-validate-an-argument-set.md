---
title: Sposób sprawdzania poprawności do zestawu argumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067723"
---
# <a name="how-to-validate-an-argument-set"></a>Jak zweryfikować zestaw argumentów

Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź argument parametru przed uruchomieniem polecenia cmdlet. Ta reguła walidacji zawiera zestaw prawidłowych wartości dla argumentu parametru.

> [!NOTE]
> Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Aby sprawdzić poprawność zestawu argumentów

- Dodaj atrybut ValidateSet, jak pokazano w poniższym kodzie. W tym przykładzie określa zestaw trzech możliwych wartości dla `UserName` parametru.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
