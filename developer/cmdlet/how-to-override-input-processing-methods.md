---
title: Sposób przesłonięcia metody przetwarzania danych wejściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067947"
---
# <a name="how-to-override-input-processing-methods"></a>Jak przesłaniać metody przetwarzania danych wejściowych

Te przykłady przedstawiają sposób zastąpienia metody w ramach polecenia cmdlet przetwarzania danych wejściowych. Te metody są używane do wykonywania następujących czynności:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoda jest używana do wykonywania operacji jednorazowego uruchomienia, które są prawidłowe dla wszystkich obiektów, które są przetwarzane przy użyciu polecenia cmdlet. Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę tylko raz.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda jest używana do przetwarzania obiektów przekazywane do polecenia cmdlet. Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę dla każdego obiektu, przekazywane do polecenia cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoda jest używana do wykonywania operacji przetwarzania jednorazowe post. Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę tylko raz.

## <a name="to-override-the-beginprocessing-method"></a>Aby przesłonić metodę BeginProcessing

- Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody.

Następujące klasy drukuje przykładowy komunikat. Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Aby przesłonić metodę ProcessRecord

- Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.

Następujące klasy drukuje przykładowy komunikat. Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Aby przesłonić metodę EndProcessing

- Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.

Następujące klasy drukuje próbkę. Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
