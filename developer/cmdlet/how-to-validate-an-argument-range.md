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
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="f8030-102">Jak zweryfikować zakres argumentów</span><span class="sxs-lookup"><span data-stu-id="f8030-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="f8030-103">Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell można użyć do sprawdzenia minimalne i maksymalne wartości argumentu parametru przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8030-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f8030-104">Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="f8030-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f8030-105">Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="f8030-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="f8030-106">Aby sprawdzić poprawność zakresu argumentu</span><span class="sxs-lookup"><span data-stu-id="f8030-106">To validate an argument range</span></span>

- <span data-ttu-id="f8030-107">Dodaj atrybut ValidateRange, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f8030-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="f8030-108">W tym przykładzie określa zakres od 0 do 5 dla `InputData` parametru.</span><span class="sxs-lookup"><span data-stu-id="f8030-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="f8030-109">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f8030-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8030-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8030-110">See Also</span></span>

[<span data-ttu-id="f8030-111">Deklaracji atrybutu ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f8030-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="f8030-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8030-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
