---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057438"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="c68b2-102">Polecenia cmdlet archiwum</span><span class="sxs-lookup"><span data-stu-id="c68b2-102">Archive cmdlets</span></span>

<span data-ttu-id="c68b2-103">Dwa nowe polecenia cmdlet **archiwum Kompresuj** i **rozwiń archiwum**systemowi Kompresuj i rozwiń plików ZIP.</span><span class="sxs-lookup"><span data-stu-id="c68b2-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="c68b2-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="c68b2-104">Compress-Archive</span></span>
<span data-ttu-id="c68b2-105">**Archiwum Kompresuj** polecenie cmdlet tworzy nowy plik archiwum na podstawie określonych plików.</span><span class="sxs-lookup"><span data-stu-id="c68b2-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="c68b2-106">Plik archiwum zezwala na wiele plików w pakiecie i opcjonalnie kompresowane w jednym pliku ułatwiającej obsługi i pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="c68b2-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="c68b2-107">Plik archiwum, można kompresować przy użyciu algorytmu kompresji określony w **- CompressionLevel** parametru.</span><span class="sxs-lookup"><span data-stu-id="c68b2-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="c68b2-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="c68b2-108">Expand-Archive</span></span>
<span data-ttu-id="c68b2-109">**Rozwiń archiwum** polecenia cmdlet wyodrębnia pliki z archiwum określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="c68b2-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="c68b2-110">Plik archiwum zezwala na wiele plików w pakiecie i opcjonalnie kompresowane w jednym pliku ułatwiającej obsługi i pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="c68b2-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
