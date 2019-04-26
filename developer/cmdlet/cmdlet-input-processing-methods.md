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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068491"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="b3de7-102">Metody przetwarzania danych wejściowych poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3de7-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="b3de7-103">Polecenia cmdlet muszą przesłaniać co najmniej jedną z metod opisanych w tym temacie do wykonywania codziennej pracy przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b3de7-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="b3de7-104">Te metody umożliwiają polecenia cmdlet do wykonywania operacji wstępne przetwarzanie, przetwarzanie danych wejściowych i przetwarzanie końcowe.</span><span class="sxs-lookup"><span data-stu-id="b3de7-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="b3de7-105">Te metody umożliwiają również zatrzymać przetwarzanie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="b3de7-106">Aby uzyskać bardziej szczegółowy przykład sposobu użycia tych metod, zobacz [samouczek SelectStr](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b3de7-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="b3de7-107">Operacje przetwarzania wstępnego</span><span class="sxs-lookup"><span data-stu-id="b3de7-107">Pre-Processing Operations</span></span>

<span data-ttu-id="b3de7-108">Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodę, aby dodać wszystkie operacje przetwarzania wstępnego są prawidłowe dla wszystkich rekordów, które będą później przetwarzane przy użyciu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="b3de7-109">Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.</span><span class="sxs-lookup"><span data-stu-id="b3de7-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="b3de7-110">Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3de7-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="b3de7-111">Poniższy kod przedstawia implementację metody BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="b3de7-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="b3de7-112">Dane wejściowe operacji przetwarzania</span><span class="sxs-lookup"><span data-stu-id="b3de7-112">Input Processing Operations</span></span>

<span data-ttu-id="b3de7-113">Polecenia cmdlet można zastąpić [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody do przetwarzania danych wejściowych, które są wysyłane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="b3de7-114">Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę dla każdego rekordu wejściowego, który jest przetwarzany przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="b3de7-115">Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3de7-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="b3de7-116">Poniższy kod przedstawia implementację metody ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="b3de7-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="b3de7-117">Operacje przetwarzania końcowego</span><span class="sxs-lookup"><span data-stu-id="b3de7-117">Post-Processing Operations</span></span>

<span data-ttu-id="b3de7-118">Polecenia cmdlet powinny przesłaniać [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodę, aby dodać dowolne operacje przetwarzania końcowego, które są prawidłowe dla wszystkich rekordów, które zostały przetworzone przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="b3de7-119">Na przykład Twoje polecenie cmdlet może być konieczne wyczyścić zmienne obiektów po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b3de7-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="b3de7-120">Kiedy PowerShell przetwarza potoku polecenia, programu PowerShell wywołuje tę metodę raz dla poszczególnych wystąpień tego polecenia cmdlet w potoku.</span><span class="sxs-lookup"><span data-stu-id="b3de7-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="b3de7-121">Jednak należy pamiętać, że w czasie wykonywania programu PowerShell nie wywoła metodę EndProcessing Jeśli polecenia cmdlet zostanie anulowane w środku za pośrednictwem jego przetwarzania danych wejściowych, lub jeśli wystąpi błąd powodujący przerwanie w jakichkolwiek pracach związanych z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3de7-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="b3de7-122">Z tego powodu należy zaimplementować pełne polecenia cmdlet, które wymaga czyszczenia obiektu [System.IDisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać oba EndProcessing i [ Metodę System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) metody po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b3de7-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="b3de7-123">Aby uzyskać więcej informacji na temat sposobu PowerShell wywołuje potok polecenia, zobacz [cyklu przetwarzania polecenia Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3de7-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="b3de7-124">Poniższy kod przedstawia implementację metody EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="b3de7-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="b3de7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3de7-125">See Also</span></span>

[<span data-ttu-id="b3de7-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="b3de7-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="b3de7-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="b3de7-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="b3de7-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="b3de7-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="b3de7-129">Samouczek SelectStr</span><span class="sxs-lookup"><span data-stu-id="b3de7-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="b3de7-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="b3de7-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="b3de7-131">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="b3de7-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
