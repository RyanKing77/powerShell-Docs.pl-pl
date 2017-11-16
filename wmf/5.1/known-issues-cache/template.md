---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: "Przykładowy szablon znany problem lub ograniczenie zapisywania"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="b3949-103">Uwaga: Podaj proponowanych opisowy tytuł i krótki opis</span><span class="sxs-lookup"><span data-stu-id="b3949-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="b3949-104">Przykład: Błędne ExecutionPolicy błędów</span><span class="sxs-lookup"><span data-stu-id="b3949-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="b3949-105">W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="b3949-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="b3949-106">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b3949-106">Resolution</span></span>

<span data-ttu-id="b3949-107">Aby rozwiązać, ustaw **ExecutionPolicy** do **RemoteSigned** , uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="b3949-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

