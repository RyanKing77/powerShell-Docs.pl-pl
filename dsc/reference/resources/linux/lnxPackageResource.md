---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxPackage
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077878"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC dla systemu Linux zasób nxPackage

**NxPackage** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania pakietami w węźle systemu Linux.

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
| Nazwa| Nazwa pakietu, dla którego chcesz zapewnić określonego stanu.|
| Upewnij się| Określa, czy należy sprawdzić, czy istnieje pakiet. Ustaw tę właściwość "Present", aby upewnić się, że pakiet istnieje. Ustaw ją na "Brak", aby upewnić się, że pakiet nie istnieje. Wartość domyślna to "Istnieje".|
| PackageManager| Obsługiwane wartości to "yum", "apt" i "zypper". Określa Menedżera pakietów do użycia podczas instalowania pakietów. Jeśli **FilePath** jest określony, podana ścieżka będzie służyć do zainstalowania pakietu. W przeciwnym razie Menedżera pakietów będzie służyć do zainstalowania pakietu ze wstępnie skonfigurowanym repozytorium. Jeśli żadna **PackageManager** ani **FilePath** są dostarczane, domyślnego menedżera pakietów dla systemu, który będzie używany.|
| FilePath| Ścieżka pliku, w którym znajduje się pakiet|
| PackageGroup| Jeśli **$true**, **nazwa** powinna być nazwa grupy pakietu do użytku z programem **PackageManager**. **PacakgeGroup** jest nieprawidłowa, podczas dostarczania **FilePath**.|
| Argumenty| Ciąg argumenty, które zostaną przekazane do pakietu dokładnie zgodnie z postanowieniami.|
| Kod zwrotny| Oczekiwany kod powrotny. Jeśli rzeczywiste zwróci kod nie odpowiada oczekiwanej wartości zostanie podany tutaj, konfiguracja zwróci błąd.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

Poniższy przykład gwarantuje, że na komputerze z systemem Linux, przy użyciu Menedżera pakietów "Yum" zainstalowano pakiet o nazwie "host z wieloma adresami".

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