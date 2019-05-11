---
title: Dane wejściowe polecenia cmdlet metody przetwarzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670308"
---
# <a name="cmdlet-input-processing-methods"></a>Metody przetwarzania danych wejściowych poleceń cmdlet

Polecenia cmdlet muszą przesłaniać co najmniej jedną z metod opisanych w tym temacie do wykonywania codziennej pracy przetwarzania danych wejściowych.
Te metody umożliwiają polecenia cmdlet do wykonywania operacji wstępne przetwarzanie, przetwarzanie danych wejściowych i przetwarzanie końcowe.
Te metody umożliwiają również zatrzymać przetwarzanie polecenia cmdlet.
Aby uzyskać bardziej szczegółowy przykład sposobu użycia tych metod, zobacz [samouczek SelectStr](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Operacje przetwarzania wstępnego

Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodę, aby dodać wszystkie operacje przetwarzania wstępnego są prawidłowe dla wszystkich rekordów, które będą później przetwarzane przy użyciu polecenia cmdlet.
Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.
Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).

Poniższy kod przedstawia implementację metody BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Dane wejściowe operacji przetwarzania

Polecenia cmdlet można zastąpić [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody do przetwarzania danych wejściowych, które są wysyłane do polecenia cmdlet.
Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę dla każdego rekordu wejściowego, który jest przetwarzany przez polecenie cmdlet.
Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).

Poniższy kod przedstawia implementację metody ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Operacje przetwarzania końcowego

Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodę, aby dodać dowolne operacje przetwarzania końcowego, które są prawidłowe dla wszystkich rekordów, które zostały przetworzone przez polecenie cmdlet.
Na przykład Twoje polecenie cmdlet może być konieczne wyczyścić zmienne obiektów po zakończeniu przetwarzania.

Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.
Jednak należy pamiętać, że w czasie wykonywania programu PowerShell nie wywoła metodę EndProcessing Jeśli polecenia cmdlet zostanie anulowane w środku za pośrednictwem jego przetwarzania danych wejściowych, lub jeśli wystąpi błąd powodujący przerwanie w jakichkolwiek pracach związanych z polecenia cmdlet.
Z tego powodu należy zaimplementować pełne polecenia cmdlet, które wymaga czyszczenia obiektu [System.IDisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać oba EndProcessing i [ Metodę System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) metody po zakończeniu przetwarzania.
Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).

Poniższy kod przedstawia implementację metody EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Samouczek SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
