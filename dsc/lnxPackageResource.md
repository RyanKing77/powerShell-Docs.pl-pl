---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxPackage zasobów"
ms.openlocfilehash: 41c627ebb39dad535f7acc8fe34739355f7a81b5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC dla systemu Linux nxPackage zasobów

**NxPackage** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania pakietami w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis | 
|---|---|
| Nazwa| Nazwa pakietu, dla którego chcesz zapewnić z określonym stanem.| 
| Upewnij się| Określa, czy sprawdzić, czy istnieje pakiet. Ustaw tę właściwość na "Brak", aby upewnić się, że pakiet istnieje. Ustaw ją na "Brak", aby upewnić się, że pakiet nie istnieje. Wartość domyślna to "Brak".|  
| PackageManager| Obsługiwane wartości to "yum", "stanie" i "zypper". Określa Menedżera pakietów do użycia podczas instalowania pakietów. Jeśli **FilePath** określono, że podana ścieżka będzie służyć do zainstalowania pakietu. W przeciwnym razie Menedżera pakietów będzie służyć do zainstalowania pakietu z wstępnie skonfigurowane repozytorium. Jeśli żadna **PackageManager** ani **FilePath** podano w nim domyślnego menedżera pakietów dla będzie używana przez system.| 
| FilePath| Ścieżka pliku, w którym znajduje się pakiet| 
| PackageGroup| Jeśli **$true**, **nazwa** powinien być nazwą grupy pakiet do użycia z **PackageManager**. **PacakgeGroup** jest nieprawidłowa, podczas dostarczania **FilePath**.| 
| Argumenty| Ciąg argumentów, które zostaną przekazane do pakietu, tak jak została podana.| 
| ReturnCode| Oczekiwany kod powrotu. Jeśli kod powrotu rzeczywiste nie odpowiada oczekiwanej wartości podane w tym miejscu konfiguracji spowoduje zwrócenie błędu.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Przykład

Poniższy przykład określa, że pakiet o nazwie "host z wieloma adresami" jest instalowany na komputer z systemem Linux, używając Menedżera pakietów "Yum".

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

