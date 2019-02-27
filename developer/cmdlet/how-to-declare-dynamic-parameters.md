---
title: Jak deklarować parametrów dynamicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847971"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="5334d-102">Jak zadeklarować parametry dynamiczne</span><span class="sxs-lookup"><span data-stu-id="5334d-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="5334d-103">Ten przykład pokazuje jak zdefiniować parametry dynamiczne, które są dodawane do polecenia cmdlet w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="5334d-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="5334d-104">W tym przykładzie `Department` parametr jest dodawany do polecenia cmdlet, zawsze wtedy, gdy użytkownik określi `Employee` parametr przełącznika.</span><span class="sxs-lookup"><span data-stu-id="5334d-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="5334d-105">Aby uzyskać więcej informacji na temat parametrów dynamicznych, zobacz [parametrów dynamicznych do polecenia Cmdlet](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5334d-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="5334d-106">Aby zdefiniować parametry dynamiczne</span><span class="sxs-lookup"><span data-stu-id="5334d-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="5334d-107">W deklaracji klasy polecenia cmdlet, Dodaj [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interfejsu, jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="5334d-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="5334d-108">Wywołaj [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) metody, która zwraca obiekt, w której są zdefiniowane parametry dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="5334d-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="5334d-109">W tym przykładzie metoda jest wywoływana, gdy `Employee` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="5334d-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="5334d-110">Zadeklaruj klasę, która definiuje parametry dynamiczne, które mają zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="5334d-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="5334d-111">Możesz użyć atrybutów, które są używane do deklarowania parametry statyczne polecenia cmdlet, aby zadeklarować parametrów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5334d-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="5334d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5334d-112">Example</span></span>

<span data-ttu-id="5334d-113">W tym przykładzie `Department` zawsze wtedy, gdy użytkownik określi zostanie dodany parametr `Employee` parametru.</span><span class="sxs-lookup"><span data-stu-id="5334d-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="5334d-114">`Department` Parametr jest opcjonalny parametr, a atrybut ValidateSet służy do określania dozwolonych argumentów.</span><span class="sxs-lookup"><span data-stu-id="5334d-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="5334d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5334d-115">See Also</span></span>

[<span data-ttu-id="5334d-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="5334d-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="5334d-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="5334d-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="5334d-118">Parametry polecenia cmdlet dynamiczny</span><span class="sxs-lookup"><span data-stu-id="5334d-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="5334d-119">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5334d-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)