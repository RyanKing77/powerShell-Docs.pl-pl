---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a>Polecenia cmdlet archiwum

Dwa nowe polecenia cmdlet **Kompresuj archiwum** i **rozwiń archiwum**systemowi kompresji i rozwiń plików ZIP.

## <a name="compress-archive"></a>Compress-Archive
**Kompresuj archiwum** polecenie cmdlet tworzy nowy plik archiwum na podstawie określonych plików. Plik archiwum umożliwia wielu plików może być spakowane i opcjonalnie skompresowane w jednym pliku łatwiejsza Obsługa i przechowywania. Plik archiwum można skompresować za pomocą algorytmu kompresji określony w **- CompressionLevel** parametru.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Rozwiń węzeł archiwum
**Rozwiń archiwum** polecenia cmdlet wyodrębnia pliki z archiwum określonego pliku. Plik archiwum umożliwia wielu plików może być spakowane i opcjonalnie skompresowane w jednym pliku łatwiejsza Obsługa i przechowywania.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```