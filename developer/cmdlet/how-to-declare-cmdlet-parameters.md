---
title: Sposób deklarowania parametry polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850589"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Jak zadeklarować parametry polecenia cmdlet

Te przykłady przedstawiają sposób deklaruje nazwanych pozycyjne, wymagane, opcjonalne i parametry przełączników. Te przykłady przedstawiają także sposób definiowania aliasów parametrów.

## <a name="how-to-declare-a-named-parameter"></a>Sposób deklarowania nazwany parametr

- Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie. Po dodaniu atrybut Parameter, Pomiń `Position` — słowo kluczowe z atrybutu.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Jak zadeklarować parametr pozycyjne

- Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie. Po dodaniu atrybut Parameter, ustaw `Position` słowa kluczowego pozycja argumentu. Wartość 0 wskazuje pierwszą pozycję.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Sposób deklarowania obowiązkowy parametr

- Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie. Po dodaniu atrybut Parameter, ustaw `Mandatory` słowa kluczowego `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Jak zadeklarować parametr opcjonalny

- Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie. Po dodaniu atrybut Parameter, Pomiń `Mandatory` — słowo kluczowe.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Jak zadeklarować parametr przełącznika

- Zdefiniuj właściwość publiczną typu [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), a następnie deklarować atrybutu parametru.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Sposób deklarowania parametrem aliasów

- Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie. Dodaj atrybut Alias, który zawiera listę aliasów dla parametru. W tym przykładzie trzy aliasy są zdefiniowane dla tego samego parametru. Pierwszy aliasu zawiera skrót. Drugi i trzeci aliasy zawierają nazwy, którego używasz dla różnych scenariuszy.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Aby uzyskać więcej informacji o atrybucie Alias, zobacz [deklaracji atrybutu Alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Deklaracji atrybutu parametru](./parameter-attribute-declaration.md)

[Deklaracji atrybutu aliasu](./alias-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
