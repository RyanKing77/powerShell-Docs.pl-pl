---
title: Przykładowe PowerShell02 Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082519"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="cafa6-102">Przykład Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="cafa6-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="cafa6-103">Niniejszy przykład pokazuje sposób uruchamiania poleceń asynchronicznie przy użyciu obszary działania puli obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="cafa6-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="cafa6-104">Przykład generuje listę poleceń, a następnie uruchomić tych poleceń, podczas gdy aparatu programu Windows PowerShell otwiera obszarem działania z puli, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="cafa6-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="cafa6-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cafa6-105">Requirements</span></span>

- <span data-ttu-id="cafa6-106">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="cafa6-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cafa6-107">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="cafa6-107">Demonstrates</span></span>

<span data-ttu-id="cafa6-108">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="cafa6-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cafa6-109">Tworzenie obiektu RunspacePool z minimalną i maksymalną liczbą obszary działania mogą zostać otwarte w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="cafa6-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="cafa6-110">Tworzenie listy poleceń.</span><span class="sxs-lookup"><span data-stu-id="cafa6-110">Creating a list of commands.</span></span>

- <span data-ttu-id="cafa6-111">Uruchamianie polecenia asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="cafa6-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="cafa6-112">Wywoływanie [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metodę, aby zobaczyć, ile obszary działania są bezpłatne.</span><span class="sxs-lookup"><span data-stu-id="cafa6-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="cafa6-113">Przechwytywanie danych wyjściowych polecenia za pomocą [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.</span><span class="sxs-lookup"><span data-stu-id="cafa6-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="cafa6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cafa6-114">Example</span></span>

<span data-ttu-id="cafa6-115">Niniejszy przykład pokazuje, jak otworzyć obszary działania puli obszarem działania i jak asynchronicznie uruchamiać polecenia w tych obszarach działania.</span><span class="sxs-lookup"><span data-stu-id="cafa6-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="cafa6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cafa6-116">See Also</span></span>

[<span data-ttu-id="cafa6-117">Pisanie aplikacji hosta programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="cafa6-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)