---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Przykładowy szablon znanych writeup problem lub ograniczenie
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055551"
---
 ><span data-ttu-id="00e6e-103">Uwaga: Podaj proponowaną opisowy tytuł i krótki opis</span><span class="sxs-lookup"><span data-stu-id="00e6e-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="00e6e-104">Przykład: Błędne błędy ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="00e6e-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="00e6e-105">Windows 7 korzystanie z modułów programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="00e6e-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="00e6e-106">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="00e6e-106">Resolution</span></span>

<span data-ttu-id="00e6e-107">Aby rozwiązać problem, należy ustawić **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="00e6e-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
