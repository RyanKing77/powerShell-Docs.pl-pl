---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxArchive
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048475"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC dla systemu Linux zasób nxArchive

**NxArchive** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce na węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| SourcePath| Określa ścieżkę źródłową pliku archiwum. Powinno to być tar .zip, lub. plik tar.gz. |
| Ścieżka_docelowa| Określa lokalizację, w której chcesz upewnić się, że zawartość archiwum zostały wyodrębnione.|
| Suma kontrolna| Definiuje typ używany do określenia, czy archiwum źródła został zaktualizowany. Wartości: "ctime", "mtime" lub "md5". Wartość domyślna to "md5".|
| Force| Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu. Za pomocą **życie** właściwość zastępuje takie błędy. Wartość domyślna to **$false**.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|
| Upewnij się| Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w **docelowy**. Ustaw tę właściwość "Present", aby upewnić się, że zawartość istnieje. Ustaw ją na "Brak", aby upewnić się, że nie istnieją. Wartość domyślna to "Istnieje".|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać **nxArchive** zasobów, aby upewnić się, że zawartość pliku archiwum o nazwie `website.tar` istnieją i są wyodrębniane w danej lokalizacji docelowej.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```