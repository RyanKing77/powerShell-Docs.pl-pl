---
title: Błędy do niepowodujące | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067658"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="eef62-102">Błędy niepowodujące przerwania działania</span><span class="sxs-lookup"><span data-stu-id="eef62-102">Non-Terminating Errors</span></span>

<span data-ttu-id="eef62-103">W tym temacie omówiono metody używane do zgłaszania błędy niepowodujące.</span><span class="sxs-lookup"><span data-stu-id="eef62-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="eef62-104">Omawia także sposób wywoływania metody z w ramach polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eef62-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="eef62-105">Gdy wystąpi błąd niepowodujący, polecenia cmdlet należy zgłosić ten błąd przez wywołanie metody [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody.</span><span class="sxs-lookup"><span data-stu-id="eef62-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="eef62-106">Gdy polecenie cmdlet zgłasza błąd niepowodujący, polecenia cmdlet mogą w dalszym ciągu działać na ten obiekt danych wejściowych i dalsze przychodzące potoku obiektów.</span><span class="sxs-lookup"><span data-stu-id="eef62-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="eef62-107">Jeśli polecenie cmdlet nie wywoła [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody, polecenie cmdlet może zapisywać rekord błędu, który opisuje warunek, który spowodował błąd niepowodujący.</span><span class="sxs-lookup"><span data-stu-id="eef62-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="eef62-108">Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="eef62-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="eef62-109">Polecenia cmdlet można wywołać [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gdy jest to konieczne z ich dane wejściowe metody przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="eef62-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="eef62-110">Jednak można wywoływać polecenia cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) tylko z wątku, który wywołał [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), lub [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) przetwarzania metody wejściowej.</span><span class="sxs-lookup"><span data-stu-id="eef62-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="eef62-111">Nie wywołuj [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) z innego wątku.</span><span class="sxs-lookup"><span data-stu-id="eef62-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="eef62-112">Zamiast tego komunikują się błędy, wróć do głównego wątku.</span><span class="sxs-lookup"><span data-stu-id="eef62-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="eef62-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eef62-113">See Also</span></span>

[<span data-ttu-id="eef62-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="eef62-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="eef62-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="eef62-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="eef62-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="eef62-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="eef62-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="eef62-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="eef62-118">Windows PowerShell błąd rekordów</span><span class="sxs-lookup"><span data-stu-id="eef62-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="eef62-119">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eef62-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
