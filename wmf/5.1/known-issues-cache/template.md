---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Przykładowy szablon znany problem lub ograniczenie zapisywania
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="8a76e-103">Uwaga: Podaj proponowanych opisowy tytuł i krótki opis</span><span class="sxs-lookup"><span data-stu-id="8a76e-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="8a76e-104">Przykład: Błędne ExecutionPolicy błędów</span><span class="sxs-lookup"><span data-stu-id="8a76e-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="8a76e-105">W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="8a76e-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="8a76e-106">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8a76e-106">Resolution</span></span>

<span data-ttu-id="8a76e-107">Aby rozwiązać, ustaw **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="8a76e-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```