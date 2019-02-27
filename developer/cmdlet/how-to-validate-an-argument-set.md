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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850568"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="fcc3e-102">Jak zweryfikować zestaw argumentów</span><span class="sxs-lookup"><span data-stu-id="fcc3e-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="fcc3e-103">Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź argument parametru przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcc3e-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="fcc3e-104">Ta reguła walidacji zawiera zestaw prawidłowych wartości dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="fcc3e-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc3e-105">Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="fcc3e-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="fcc3e-106">Aby sprawdzić poprawność zestawu argumentów</span><span class="sxs-lookup"><span data-stu-id="fcc3e-106">To validate an argument set</span></span>

- <span data-ttu-id="fcc3e-107">Dodaj atrybut ValidateSet, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fcc3e-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="fcc3e-108">W tym przykładzie określa zestaw trzech możliwych wartości dla `UserName` parametru.</span><span class="sxs-lookup"><span data-stu-id="fcc3e-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="fcc3e-109">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="fcc3e-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc3e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcc3e-110">See Also</span></span>

[<span data-ttu-id="fcc3e-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="fcc3e-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="fcc3e-112">Deklaracji atrybutu ValidateSet</span><span class="sxs-lookup"><span data-stu-id="fcc3e-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="fcc3e-113">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcc3e-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
