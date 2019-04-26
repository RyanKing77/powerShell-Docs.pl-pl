---
title: Jak utworzyć żądanie potwierdzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067845"
---
# <a name="how-to-request-confirmations"></a>Jak tworzyć żądania potwierdzenia

W tym przykładzie przedstawiono sposób wywoływania [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody żądania potwierdzenia z Użytkownik, przed wykonaniem akcji.

> [!IMPORTANT]
> Aby uzyskać więcej informacji na temat tych żądań obsługi środowiska Windows PowerShell, zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Aby zażądać potwierdzenia

1. Upewnij się, że `SupportsShouldProcess` parametru polecenia Cmdlet atrybutu jest równa `true`. (Dla funkcji jest to parametr atrybut CmdletBinding).

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Dodaj `Force` parametru do Twojego polecenia cmdlet, aby użytkownik może zastąpić żądania potwierdzenia.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Dodaj `if` instrukcję, która używa wartość zwracaną przez [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodę, aby określić, czy [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoda jest wywoływana.

4. Dodaj drugą `if` instrukcję, która używa wartość zwracaną przez [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody i wartości `Force` parametru, aby określić, czy operacja powinna być wykonywane.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody są wywoływane z w ramach zastępowania z [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody. Jednak te metody można również wywołać z innych danych wejściowych metody przetwarzania.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
