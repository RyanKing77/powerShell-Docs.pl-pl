---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="f93e2-102">Polecenia cmdlet archiwum</span><span class="sxs-lookup"><span data-stu-id="f93e2-102">Archive cmdlets</span></span>

<span data-ttu-id="f93e2-103">Dwa nowe polecenia cmdlet **Kompresuj archiwum** i **rozwiń archiwum**systemowi kompresji i rozwiń plików ZIP.</span><span class="sxs-lookup"><span data-stu-id="f93e2-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="f93e2-104">Kompresuj archiwum</span><span class="sxs-lookup"><span data-stu-id="f93e2-104">Compress-Archive</span></span>
<span data-ttu-id="f93e2-105">**Kompresuj archiwum** polecenie cmdlet tworzy nowy plik archiwum na podstawie określonych plików.</span><span class="sxs-lookup"><span data-stu-id="f93e2-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="f93e2-106">Plik archiwum umożliwia wielu plików może być spakowane i opcjonalnie skompresowane w jednym pliku łatwiejsza Obsługa i przechowywania.</span><span class="sxs-lookup"><span data-stu-id="f93e2-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="f93e2-107">Plik archiwum można skompresować za pomocą algorytmu kompresji określony w **- CompressionLevel** parametru.</span><span class="sxs-lookup"><span data-stu-id="f93e2-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="f93e2-108">Rozwiń węzeł archiwum</span><span class="sxs-lookup"><span data-stu-id="f93e2-108">Expand-Archive</span></span>
<span data-ttu-id="f93e2-109">**Rozwiń archiwum** polecenia cmdlet wyodrębnia pliki z archiwum określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="f93e2-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="f93e2-110">Plik archiwum umożliwia wielu plików może być spakowane i opcjonalnie skompresowane w jednym pliku łatwiejsza Obsługa i przechowywania.</span><span class="sxs-lookup"><span data-stu-id="f93e2-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

