---
title: Jak pisać proste polecenie Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 2fc1a3947ca6076387ea85d7f8ba9018ed7385a0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849532"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="19d2a-102">Jak napisać polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-102">How to write a cmdlet</span></span>

<span data-ttu-id="19d2a-103">W tym artykule pokazano, jak napisać polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19d2a-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="19d2a-104">**Send-Greeting** polecenie cmdlet przyjmuje jako dane wejściowe nazwę pojedynczego użytkownika, a następnie zapisuje powitanie, dla tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19d2a-104">The **Send-Greeting** cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="19d2a-105">Polecenia cmdlet wykonać dużo pracy, w tym przykładzie przedstawiono główne sekcje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19d2a-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="19d2a-106">Kroki, aby zapisać polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="19d2a-107">Aby zadeklarować klasy jako polecenia cmdlet, należy użyć **polecenia Cmdlet** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="19d2a-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="19d2a-108">**Polecenia Cmdlet** atrybut określa czasownik i rzeczownik nazwy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19d2a-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="19d2a-109">Aby uzyskać więcej informacji na temat **polecenia Cmdlet** atrybutów, zobacz [deklaracji CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="19d2a-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="19d2a-110">Określ nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="19d2a-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="19d2a-111">Określ, że polecenia cmdlet wywodzi się z jednej z następujących klas:</span><span class="sxs-lookup"><span data-stu-id="19d2a-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="19d2a-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="19d2a-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="19d2a-114">Aby zdefiniować parametry dla polecenia cmdlet, należy użyć **parametru** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="19d2a-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="19d2a-115">W tym przypadku jedyną wymaganych określono parametr.</span><span class="sxs-lookup"><span data-stu-id="19d2a-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="19d2a-116">Aby uzyskać więcej informacji na temat **parametru** atrybutów, zobacz [deklaracji ParameterAttribute](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="19d2a-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="19d2a-117">Zastąpienie metody, która przetwarza dane wejściowe do przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="19d2a-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="19d2a-118">W tym przypadku [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda zostanie przesłonięta.</span><span class="sxs-lookup"><span data-stu-id="19d2a-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="19d2a-119">Aby zapisać powitanie, należy użyć metody [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="19d2a-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="19d2a-120">Pozdrowienie jest wyświetlane w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="19d2a-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="19d2a-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="19d2a-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify and
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="19d2a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19d2a-122">See also</span></span>

[<span data-ttu-id="19d2a-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="19d2a-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="19d2a-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="19d2a-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="19d2a-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="19d2a-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="19d2a-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="19d2a-127">Deklaracja CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="19d2a-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="19d2a-128">Deklaracja ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="19d2a-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="19d2a-129">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="19d2a-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
