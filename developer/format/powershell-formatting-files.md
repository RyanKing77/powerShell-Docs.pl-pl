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
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065382"
---
# <a name="windows-powershell-formatting-files"></a>Pliki formatujące programu Windows PowerShell

Windows PowerShell udostępnia kilka plików formatowania (. format.ps1xml), znajdują się w katalogu instalacyjnym (`$pshome`). Każdy z tych plików definiuje domyślnym wyświetlaniem dla określonego zestawu obiektów platformy .NET. Pliki te nigdy nie powinny być zmieniane. Jednak można je jako odwołanie do tworzenia własnych niestandardowych plików formatowania.

Certificate.Format.ps1xml Określa wyświetlanie obiektów w magazynie certyfikatów, takich jak certyfikaty x.509 i magazynów certyfikatów.

DotNetTypes.Format.ps1xml Określa wyświetlanie różnych obiektów platformy .NET, takich jak obiekty CultureInfo, FileVersionInfo i EventLogEntry.

FileSystem.Format.ps1xml definiuje wyświetlanie obiektów systemu plików, takich jak obiekty plików i katalogów.

Definiuje Help.Format.ps1xml posługują się różne widoki [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, takich jak szczegółowe widoki pełnej, parametry oraz przykład.

PowerShellCore.Format.ps1xml Określa wyświetlanie obiektów wygenerowanych przez polecenia cmdlet z podstawowych programu Windows PowerShell, takie jak obiekty zwrócone przez [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) i [historii Get](/powershell/module/Microsoft.PowerShell.Core/Get-History) polecenia cmdlet.

PowerShellTrace.Format.ps1xml Określa wyświetlanie obiektów śledzenia, np. tych generowanych przez [polecenia Trace](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) polecenia cmdlet.

Registry.Format.ps1xml definiuje wyświetlanie rejestru obiekty, takie jak obiekty klucza i wpisu.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
