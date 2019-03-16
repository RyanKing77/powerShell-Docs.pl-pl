---
title: Pojęcia dotyczące raportów o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054411"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="518d9-102">Pojęcia dotyczące raportowania błędów</span><span class="sxs-lookup"><span data-stu-id="518d9-102">Error Reporting Concepts</span></span>

<span data-ttu-id="518d9-103">Windows PowerShell udostępnia dwa mechanizmy zgłaszania błędów: jeden mechanizm *przerywa błędy* i inny mechanizm *błędy niepowodujące*.</span><span class="sxs-lookup"><span data-stu-id="518d9-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="518d9-104">Ważne jest dla Twojego polecenia cmdlet, aby włączyć raportowanie błędów poprawnie tak, aby aplikacji hosta, która jest uruchomiona poleceń cmdlet pozwala reagować w odpowiedni sposób.</span><span class="sxs-lookup"><span data-stu-id="518d9-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="518d9-105">Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody, gdy wystąpi błąd, który nie jest lub nie powinien zezwalać na polecenia cmdlet kontynuować przetwarzanie jej danych wejściowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="518d9-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="518d9-106">Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, aby zgłaszać błędy niepowodujące w przypadku polecenia cmdlet można kontynuować przetwarzanie danych wejściowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="518d9-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="518d9-107">Obie metody zapewniają rekord błędu, używanego przez aplikację hosta można zbadać przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="518d9-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="518d9-108">Skorzystaj z poniższych wskazówek, aby określić, czy błąd jest kończącym lub błąd niepowodujący.</span><span class="sxs-lookup"><span data-stu-id="518d9-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="518d9-109">Błąd jest błąd, jeśli uniemożliwia Twojego polecenia cmdlet, z dalszego przetwarzania bieżącego obiektu lub pomyślnie przetwarzania wszelkich dalszych danych wejściowych obiektów, niezależnie od ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="518d9-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="518d9-110">Błąd jest błąd powodujący zakończenie, jeśli nie chcesz Twojego polecenia cmdlet kontynuować przetwarzanie bieżącego obiektu lub wszelkich dalszych danych wejściowych obiektów, niezależnie od ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="518d9-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="518d9-111">Błąd jest błąd powodujący zakończenie go w poleceniu cmdlet, które przyjmują ani nie zwraca obiektu lub jeśli nastąpi to w poleceniu cmdlet, który akceptuje lub zwraca tylko jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="518d9-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="518d9-112">Błąd jest błąd niepowodujący, jeśli chcesz Twojego polecenia cmdlet kontynuować przetwarzanie bieżący obiekt i wszystkie obiekty dalszych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="518d9-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="518d9-113">Błąd jest błąd niepowodujący, jeżeli jest powiązany do określonego obiektu wejściowego lub podzbiór obiektów danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="518d9-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="518d9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="518d9-114">See Also</span></span>

[<span data-ttu-id="518d9-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="518d9-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="518d9-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="518d9-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="518d9-117">Windows PowerShell błąd rekordów</span><span class="sxs-lookup"><span data-stu-id="518d9-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="518d9-118">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="518d9-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
