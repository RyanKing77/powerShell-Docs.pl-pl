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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067927"
---
# <a name="how-to-declare-dynamic-parameters"></a>Jak zadeklarować parametry dynamiczne

Ten przykład pokazuje jak zdefiniować parametry dynamiczne, które są dodawane do polecenia cmdlet w środowisku uruchomieniowym. W tym przykładzie `Department` parametr jest dodawany do polecenia cmdlet, zawsze wtedy, gdy użytkownik określi `Employee` parametr przełącznika. Aby uzyskać więcej informacji na temat parametrów dynamicznych, zobacz [parametrów dynamicznych do polecenia Cmdlet](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Aby zdefiniować parametry dynamiczne

1. W deklaracji klasy polecenia cmdlet, Dodaj [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interfejsu, jak pokazano.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Wywołaj [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) metody, która zwraca obiekt, w której są zdefiniowane parametry dynamiczne. W tym przykładzie metoda jest wywoływana, gdy `Employee` określono parametr.

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

3. Zadeklaruj klasę, która definiuje parametry dynamiczne, które mają zostać dodane. Możesz użyć atrybutów, które są używane do deklarowania parametry statyczne polecenia cmdlet, aby zadeklarować parametrów dynamicznych.

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

## <a name="example"></a>Przykład

W tym przykładzie `Department` zawsze wtedy, gdy użytkownik określi zostanie dodany parametr `Employee` parametru. `Department` Parametr jest opcjonalny parametr, a atrybut ValidateSet służy do określania dozwolonych argumentów.

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

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Parametry polecenia cmdlet dynamiczny](./cmdlet-dynamic-parameters.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)