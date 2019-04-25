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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067777"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="f4a6c-102">Jak zweryfikować wzorzec argumentu</span><span class="sxs-lookup"><span data-stu-id="f4a6c-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="f4a6c-103">Ten przykład pokazuje, jak określić regułę walidacji, środowisko wykonawcze programu Windows PowerShell można użyć do sprawdzenia wzorzec znak argumentu parametru przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4a6c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f4a6c-104">Ta reguła walidacji możesz ustawić od zadeklarowania atrybutu ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="f4a6c-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a6c-105">Aby uzyskać więcej informacji na temat klasę, która definiuje ten atrybut zobacz [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="f4a6c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="f4a6c-106">Aby sprawdzić poprawność wzorzec argumentu</span><span class="sxs-lookup"><span data-stu-id="f4a6c-106">To validate an argument pattern</span></span>

- <span data-ttu-id="f4a6c-107">Dodaj atrybut weryfikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f4a6c-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="f4a6c-108">W tym przykładzie określa wzorzec cztery cyfry, w którym każda cyfrę ma wartość od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="f4a6c-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="f4a6c-109">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4a6c-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4a6c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4a6c-110">See Also</span></span>

[<span data-ttu-id="f4a6c-111">Deklaracji atrybutu ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f4a6c-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="f4a6c-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4a6c-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
