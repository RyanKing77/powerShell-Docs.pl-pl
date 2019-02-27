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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849007"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="31682-102">Jak zweryfikować liczbę argumentów</span><span class="sxs-lookup"><span data-stu-id="31682-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="31682-103">W tym przykładzie pokazano, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell służy do Sprawdź liczbę argumentów (liczba), które akceptuje parametr przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31682-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="31682-104">Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="31682-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="31682-105">Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="31682-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="31682-106">Aby sprawdzić poprawność liczba argumentów</span><span class="sxs-lookup"><span data-stu-id="31682-106">To validate an argument count</span></span>

- <span data-ttu-id="31682-107">Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="31682-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="31682-108">W tym przykładzie określa, że parametr przyjmuje jeden argument lub maksymalnie trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="31682-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="31682-109">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="31682-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31682-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31682-110">See Also</span></span>

[<span data-ttu-id="31682-111">Deklaracji atrybutu ValidateCount</span><span class="sxs-lookup"><span data-stu-id="31682-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="31682-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="31682-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
