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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794947"
---
# <a name="cmdlet-input-processing-methods"></a>Metody przetwarzania danych wejściowych poleceń cmdlet

Polecenia cmdlet muszą przesłaniać co najmniej jedną z metod opisanych w tym temacie do wykonywania codziennej pracy przetwarzania danych wejściowych. Te metody umożliwiają polecenia cmdlet do wykonywania przetwarzania wstępnego operacje, danych wejściowych operacji przetwarzania i operacji przetwarzania końcowego. Te metody umożliwiają również zatrzymać przetwarzanie polecenia cmdlet.

## <a name="pre-processing-tasks"></a>Zadania przetwarzania wstępnego

Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodę, aby dodać wszystkie operacje przetwarzania wstępnego są prawidłowe dla wszystkich rekordów, które będą później przetwarzane przy użyciu polecenia cmdlet. Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku. Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metody.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md). W tym samouczku **Str wybierz** polecenie cmdlet używa [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodę w celu wygenerowania wyrażenia regularnego, który jest używany do wyszukiwania danych wejściowych, przetwarzanie rekordów.

## <a name="input-processing-tasks"></a>Dane wejściowe zadania przetwarzania

Polecenia cmdlet można zastąpić [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody do przetwarzania danych wejściowych, które są wysyłane do polecenia cmdlet. Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę dla każdego rekordu wejściowego, który jest przetwarzany przez polecenie cmdlet. Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Przetwarzania końcowego zadania

Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodę, aby dodać dowolne operacje przetwarzania końcowego, które są prawidłowe dla wszystkich rekordów, które zostały przetworzone przez polecenie cmdlet. Na przykład Twoje polecenie cmdlet może być konieczne wyczyścić zmienne obiektów po zakończeniu przetwarzania.

Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku. Będzie jednak pamiętać, że środowisko wykonawcze programu Windows PowerShell nie wywoła [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metody, jeśli polecenie cmdlet zostanie anulowana w środku za pośrednictwem jego przetwarzania danych wejściowych lub gdy kończącym błędu w jakichkolwiek pracach związanych z polecenia cmdlet. Z tego powodu należy zaimplementować pełne polecenia cmdlet, które wymaga czyszczenia obiektu [System.Idisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać zarówno [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) i [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) metody po zakończeniu przetwarzania. Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md).

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
