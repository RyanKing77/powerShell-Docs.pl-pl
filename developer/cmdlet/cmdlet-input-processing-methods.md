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
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="88dfc-102">Metody przetwarzania danych wejściowych poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="88dfc-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="88dfc-103">Polecenia cmdlet muszą przesłaniać co najmniej jedną z metod opisanych w tym temacie do wykonywania codziennej pracy przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="88dfc-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="88dfc-104">Te metody umożliwiają polecenia cmdlet do wykonywania przetwarzania wstępnego operacje, danych wejściowych operacji przetwarzania i operacji przetwarzania końcowego.</span><span class="sxs-lookup"><span data-stu-id="88dfc-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="88dfc-105">Te metody umożliwiają również zatrzymać przetwarzanie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="88dfc-106">Zadania przetwarzania wstępnego</span><span class="sxs-lookup"><span data-stu-id="88dfc-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="88dfc-107">Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodę, aby dodać wszystkie operacje przetwarzania wstępnego są prawidłowe dla wszystkich rekordów, które będą później przetwarzane przy użyciu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="88dfc-108">Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.</span><span class="sxs-lookup"><span data-stu-id="88dfc-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="88dfc-109">Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="88dfc-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="88dfc-110">Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metody.</span><span class="sxs-lookup"><span data-stu-id="88dfc-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="88dfc-111">Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="88dfc-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="88dfc-112">W tym samouczku **Str wybierz** polecenie cmdlet używa [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodę w celu wygenerowania wyrażenia regularnego, który jest używany do wyszukiwania danych wejściowych, przetwarzanie rekordów.</span><span class="sxs-lookup"><span data-stu-id="88dfc-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="88dfc-113">Dane wejściowe zadania przetwarzania</span><span class="sxs-lookup"><span data-stu-id="88dfc-113">Input Processing Tasks</span></span>

<span data-ttu-id="88dfc-114">Polecenia cmdlet można zastąpić [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody do przetwarzania danych wejściowych, które są wysyłane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="88dfc-115">Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę dla każdego rekordu wejściowego, który jest przetwarzany przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="88dfc-116">Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="88dfc-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="88dfc-117">Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody.</span><span class="sxs-lookup"><span data-stu-id="88dfc-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="88dfc-118">Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="88dfc-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="88dfc-119">Przetwarzania końcowego zadania</span><span class="sxs-lookup"><span data-stu-id="88dfc-119">Post-Processing Tasks</span></span>

<span data-ttu-id="88dfc-120">Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodę, aby dodać dowolne operacje przetwarzania końcowego, które są prawidłowe dla wszystkich rekordów, które zostały przetworzone przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="88dfc-121">Na przykład Twoje polecenie cmdlet może być konieczne wyczyścić zmienne obiektów po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="88dfc-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="88dfc-122">Kiedy program Windows PowerShell przetwarza potoku polecenia, programu Windows PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.</span><span class="sxs-lookup"><span data-stu-id="88dfc-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="88dfc-123">Będzie jednak pamiętać, że środowisko wykonawcze programu Windows PowerShell nie wywoła [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metody, jeśli polecenie cmdlet zostanie anulowana w środku za pośrednictwem jego przetwarzania danych wejściowych lub gdy kończącym błędu w jakichkolwiek pracach związanych z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88dfc-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="88dfc-124">Z tego powodu należy zaimplementować pełne polecenia cmdlet, które wymaga czyszczenia obiektu [System.Idisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać zarówno [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) i [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) metody po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="88dfc-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="88dfc-125">Aby uzyskać więcej informacji na temat sposobu programu Windows PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="88dfc-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="88dfc-126">Poniższy kod przedstawia implementację [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody.</span><span class="sxs-lookup"><span data-stu-id="88dfc-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="88dfc-127">Aby uzyskać bardziej szczegółowy przykład sposobu używania [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = imię i nazwisko](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metody, zobacz [samouczek SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="88dfc-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88dfc-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88dfc-128">See Also</span></span>

[<span data-ttu-id="88dfc-129">System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="88dfc-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="88dfc-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="88dfc-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="88dfc-131">System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="88dfc-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="88dfc-132">System.Idisposable</span><span class="sxs-lookup"><span data-stu-id="88dfc-132">System.Idisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="88dfc-133">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="88dfc-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
