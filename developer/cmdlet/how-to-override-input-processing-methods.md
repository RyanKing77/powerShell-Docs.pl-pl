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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056400"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="a12b4-102">Jak przesłaniać metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="a12b4-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="a12b4-103">Te przykłady przedstawiają sposób zastąpienia metody w ramach polecenia cmdlet przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a12b4-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="a12b4-104">Te metody są używane do wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a12b4-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="a12b4-105">[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoda jest używana do wykonywania operacji jednorazowego uruchomienia, które są prawidłowe dla wszystkich obiektów, które są przetwarzane przy użyciu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a12b4-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="a12b4-106">Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę tylko raz.</span><span class="sxs-lookup"><span data-stu-id="a12b4-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="a12b4-107">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda jest używana do przetwarzania obiektów przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a12b4-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="a12b4-108">Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę dla każdego obiektu, przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a12b4-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="a12b4-109">[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metoda jest używana do wykonywania operacji przetwarzania jednorazowe post.</span><span class="sxs-lookup"><span data-stu-id="a12b4-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="a12b4-110">Środowisko wykonawcze programu Windows PowerShell wywołuje tę metodę tylko raz.</span><span class="sxs-lookup"><span data-stu-id="a12b4-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="a12b4-111">Aby przesłonić metodę BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="a12b4-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="a12b4-112">Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="a12b4-113">Następujące klasy drukuje przykładowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="a12b4-113">The following class prints a sample message.</span></span> <span data-ttu-id="a12b4-114">Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="a12b4-115">Aby przesłonić metodę ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a12b4-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="a12b4-116">Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="a12b4-117">Następujące klasy drukuje przykładowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="a12b4-117">The following class prints a sample message.</span></span> <span data-ttu-id="a12b4-118">Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="a12b4-119">Aby przesłonić metodę EndProcessing</span><span class="sxs-lookup"><span data-stu-id="a12b4-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="a12b4-120">Zadeklaruj chronionych zastępowania metody [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="a12b4-121">Następujące klasy drukuje próbkę.</span><span class="sxs-lookup"><span data-stu-id="a12b4-121">The following class prints a sample.</span></span> <span data-ttu-id="a12b4-122">Aby użyć tej klasy, należy zmienić czasownik i rzeczownik w atrybucie polecenia Cmdlet, zmienić nazwę klasy, aby odzwierciedlić nowe czasownik i rzeczownik, a następnie dodaj funkcji wymaganych do zastępowania metody [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.</span><span class="sxs-lookup"><span data-stu-id="a12b4-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a12b4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a12b4-123">See Also</span></span>

[<span data-ttu-id="a12b4-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="a12b4-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="a12b4-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="a12b4-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="a12b4-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a12b4-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a12b4-127">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a12b4-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
