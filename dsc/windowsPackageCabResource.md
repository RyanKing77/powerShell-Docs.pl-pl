---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: DSC WindowsPackageCab Resource
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab Resource

> Dotyczy: Windows PowerShell 5.1 i nowszych

**WindowsPackageCab** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety cabinet (cab) systemu Windows w docelowym węźle.

Węzeł docelowy musi mieć zainstalowany moduł PowerShell narzędzie DISM. Aby uzyskać informacje, zobacz [DISM używany w programie Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14). 


## <a name="syntax"></a>Składnia

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   | 
|---|---| 
| Nazwa| Wskazuje nazwy pakietu dla chcesz zapewnić z określonym stanem.| 
| Upewnij się| Wskazuje, czy pakiet jest zainstalowany. Ustaw tę właściwość na "Brak", upewnij się, że pakiet nie jest zainstalowany (lub odinstalować pakiet, jeśli jest zainstalowana). Ustaw "Przedstawić" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.|
| Ścieżka| Określa ścieżkę, w której znajduje się pakiet.| 
| Ścieżka dziennika| Określa pełną ścieżkę, w którym ma dostawcy, aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".| 

## <a name="example"></a>Przykład

Poniższa przykładowa konfiguracja pobiera parametry wejściowe i zapewnia, że plik cab określony przez `$Name` parametru jest zainstalowany.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

