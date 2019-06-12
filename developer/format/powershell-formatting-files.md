---
title: Windows PowerShell, formatowanie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830258"
---
# <a name="windows-powershell-formatting-files"></a>Pliki formatujące programu Windows PowerShell

Windows PowerShell udostępnia kilka plików formatowania (. format.ps1xml), znajdują się w katalogu instalacyjnym (`$pshome`). Każdy z tych plików definiuje domyślnym wyświetlaniem dla określonego zestawu obiektów platformy .NET. Pliki te nigdy nie powinny być zmieniane. Jednak można je jako odwołanie do tworzenia własnych niestandardowych plików formatowania.

`Certificate.Format.ps1xml` Określa wyświetlanie obiektów w magazynie certyfikatów, takich jak certyfikaty x.509 i magazynów certyfikatów.

`DotNetTypes.Format.ps1xml` Określa wyświetlanie różnych obiektów platformy .NET, takich jak obiekty CultureInfo, FileVersionInfo i EventLogEntry.

`FileSystem.Format.ps1xml` Określa wyświetlanie obiektów systemu plików, takich jak obiekty plików i katalogów.

`Help.Format.ps1xml` Definiuje różne widoki, które są używane przez [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, takich jak szczegółowe widoki pełnej, parametry oraz przykład.

`PowerShellCore.Format.ps1xml` Określa wyświetlanie obiektów wygenerowanych przez polecenia cmdlet z podstawowych programu Windows PowerShell, takie jak obiekty zwrócone przez [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) i [historii Get](/powershell/module/Microsoft.PowerShell.Core/Get-History) polecenia cmdlet.

`PowerShellTrace.Format.ps1xml` Określa wyświetlanie obiektów śledzenia, np. tych generowanych przez [polecenia Trace](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) polecenia cmdlet.

`Registry.Format.ps1xml` Określa wyświetlanie rejestru obiekty, takie jak obiekty klucza i wpisu.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
