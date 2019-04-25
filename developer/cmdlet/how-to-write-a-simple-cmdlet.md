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
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067743"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="f6b55-102">Jak napisać polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-102">How to write a cmdlet</span></span>

<span data-ttu-id="f6b55-103">W tym artykule pokazano, jak napisać polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6b55-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="f6b55-104">`Send-Greeting` Polecenie cmdlet przyjmuje jako dane wejściowe nazwę pojedynczego użytkownika, a następnie zapisuje powitanie, dla tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f6b55-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="f6b55-105">Polecenia cmdlet wykonać dużo pracy, w tym przykładzie przedstawiono główne sekcje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6b55-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="f6b55-106">Kroki, aby zapisać polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="f6b55-107">Aby zadeklarować klasy jako polecenia cmdlet, należy użyć **polecenia Cmdlet** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f6b55-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="f6b55-108">**Polecenia Cmdlet** atrybut określa czasownik i rzeczownik nazwy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6b55-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="f6b55-109">Aby uzyskać więcej informacji na temat **polecenia Cmdlet** atrybutów, zobacz [deklaracji CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f6b55-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="f6b55-110">Określ nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="f6b55-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="f6b55-111">Określ, że polecenia cmdlet wywodzi się z jednej z następujących klas:</span><span class="sxs-lookup"><span data-stu-id="f6b55-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="f6b55-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="f6b55-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="f6b55-114">Aby zdefiniować parametry dla polecenia cmdlet, należy użyć **parametru** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f6b55-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="f6b55-115">W tym przypadku jedyną wymaganych określono parametr.</span><span class="sxs-lookup"><span data-stu-id="f6b55-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="f6b55-116">Aby uzyskać więcej informacji na temat **parametru** atrybutów, zobacz [deklaracji ParameterAttribute](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f6b55-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="f6b55-117">Zastąpienie metody, która przetwarza dane wejściowe do przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f6b55-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="f6b55-118">W tym przypadku [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda zostanie przesłonięta.</span><span class="sxs-lookup"><span data-stu-id="f6b55-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="f6b55-119">Aby zapisać powitanie, należy użyć metody [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="f6b55-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="f6b55-120">Pozdrowienie jest wyświetlane w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="f6b55-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="f6b55-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6b55-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
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

## <a name="see-also"></a><span data-ttu-id="f6b55-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6b55-122">See also</span></span>

[<span data-ttu-id="f6b55-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="f6b55-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="f6b55-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="f6b55-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="f6b55-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="f6b55-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="f6b55-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="f6b55-127">Deklaracja CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="f6b55-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="f6b55-128">Deklaracja ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="f6b55-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="f6b55-129">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6b55-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)