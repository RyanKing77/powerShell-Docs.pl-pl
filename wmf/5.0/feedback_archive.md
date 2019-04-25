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
# <a name="archive-cmdlets"></a>Polecenia cmdlet archiwum

Dwa nowe polecenia cmdlet **archiwum Kompresuj** i **rozwiń archiwum**systemowi Kompresuj i rozwiń plików ZIP.

## <a name="compress-archive"></a>Compress-Archive
**Archiwum Kompresuj** polecenie cmdlet tworzy nowy plik archiwum na podstawie określonych plików. Plik archiwum zezwala na wiele plików w pakiecie i opcjonalnie kompresowane w jednym pliku ułatwiającej obsługi i pamięci masowej. Plik archiwum, można kompresować przy użyciu algorytmu kompresji określony w **- CompressionLevel** parametru.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
**Rozwiń archiwum** polecenia cmdlet wyodrębnia pliki z archiwum określonego pliku. Plik archiwum zezwala na wiele plików w pakiecie i opcjonalnie kompresowane w jednym pliku ułatwiającej obsługi i pamięci masowej.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
