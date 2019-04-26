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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067719"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="008fc-102">Jak zweryfikować długość argumentu</span><span class="sxs-lookup"><span data-stu-id="008fc-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="008fc-103">Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź liczbę znaków (długość) argument parametru przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="008fc-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="008fc-104">Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="008fc-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="008fc-105">Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="008fc-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="008fc-106">Aby sprawdzić długość argumentu</span><span class="sxs-lookup"><span data-stu-id="008fc-106">To validate the argument length</span></span>

- <span data-ttu-id="008fc-107">Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="008fc-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="008fc-108">W tym przykładzie określa, że długość argumentu powinien mieć długość 0 do 10 znaków.</span><span class="sxs-lookup"><span data-stu-id="008fc-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="008fc-109">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="008fc-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="008fc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="008fc-110">See Also</span></span>

[<span data-ttu-id="008fc-111">Deklaracji atrybutu ValidateLength</span><span class="sxs-lookup"><span data-stu-id="008fc-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="008fc-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="008fc-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
