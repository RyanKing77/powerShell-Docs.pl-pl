---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218097"
---
# <a name="archive-cmdlets"></a>Polecenia cmdlet archiwum

Dwa nowe polecenia cmdlet **Kompresuj archiwum** i **rozwiń archiwum**systemowi kompresji i rozwiń plików ZIP.

## <a name="compress-archive"></a>Kompresuj archiwum
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
