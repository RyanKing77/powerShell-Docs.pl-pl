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
# <a name="how-to-write-a-cmdlet"></a>Jak napisać polecenia cmdlet

W tym artykule pokazano, jak napisać polecenia cmdlet. **Send-Greeting** polecenie cmdlet przyjmuje jako dane wejściowe nazwę pojedynczego użytkownika, a następnie zapisuje powitanie, dla tego użytkownika. Polecenia cmdlet wykonać dużo pracy, w tym przykładzie przedstawiono główne sekcje polecenia cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Kroki, aby zapisać polecenia cmdlet

1. Aby zadeklarować klasy jako polecenia cmdlet, należy użyć **polecenia Cmdlet** atrybutu. **Polecenia Cmdlet** atrybut określa czasownik i rzeczownik nazwy polecenia cmdlet.

   Aby uzyskać więcej informacji na temat **polecenia Cmdlet** atrybutów, zobacz [deklaracji CmdletAttribute](cmdlet-attribute-declaration.md).

2. Określ nazwę klasy.

3. Określ, że polecenia cmdlet wywodzi się z jednej z następujących klas:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Aby zdefiniować parametry dla polecenia cmdlet, należy użyć **parametru** atrybutu. W tym przypadku jedyną wymaganych określono parametr.

   Aby uzyskać więcej informacji na temat **parametru** atrybutów, zobacz [deklaracji ParameterAttribute](parameter-attribute-declaration.md).

5. Zastąpienie metody, która przetwarza dane wejściowe do przetwarzania danych wejściowych. W tym przypadku [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda zostanie przesłonięta.

6. Aby zapisać powitanie, należy użyć metody [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Pozdrowienie jest wyświetlane w następującym formacie:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Deklaracja CmdletAttribute](cmdlet-attribute-declaration.md)

[Deklaracja ParameterAttribute](parameter-attribute-declaration.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](writing-a-windows-powershell-cmdlet.md)
