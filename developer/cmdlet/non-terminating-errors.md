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
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845255"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="8e4e0-102">Błędy niepowodujące przerwania działania</span><span class="sxs-lookup"><span data-stu-id="8e4e0-102">Non-Terminating Errors</span></span>

<span data-ttu-id="8e4e0-103">W tym temacie omówiono metody używane do zgłaszania błędy niepowodujące.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="8e4e0-104">Omawia także sposób wywoływania metody z w ramach polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="8e4e0-105">Gdy wystąpi błąd niepowodujący, polecenia cmdlet należy zgłosić ten błąd przez wywołanie metody [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="8e4e0-106">Gdy polecenie cmdlet zgłasza błąd niepowodujący, polecenia cmdlet mogą w dalszym ciągu działać na ten obiekt danych wejściowych i dalsze przychodzące potoku obiektów.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="8e4e0-107">Jeśli polecenie cmdlet nie wywoła [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody, polecenie cmdlet może zapisywać rekord błędu, który opisuje warunek, który spowodował błąd niepowodujący.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="8e4e0-108">Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="8e4e0-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="8e4e0-109">Polecenia cmdlet można wywołać [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gdy jest to konieczne z ich dane wejściowe metody przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="8e4e0-110">Jednak można wywoływać polecenia cmdlet [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) tylko z wątku, który wywołał [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), lub [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) przetwarzania metody wejściowej.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="8e4e0-111">Nie wywołuj [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) z innego wątku.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="8e4e0-112">Zamiast tego komunikują się błędy, wróć do głównego wątku.</span><span class="sxs-lookup"><span data-stu-id="8e4e0-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e4e0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e4e0-113">See Also</span></span>

[<span data-ttu-id="8e4e0-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="8e4e0-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="8e4e0-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="8e4e0-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="8e4e0-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="8e4e0-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="8e4e0-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="8e4e0-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="8e4e0-118">Windows PowerShell błąd rekordów</span><span class="sxs-lookup"><span data-stu-id="8e4e0-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="8e4e0-119">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e4e0-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
