---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxArchive zasobów
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC dla systemu Linux nxArchive zasobów

**NxArchive** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce na węźle Linux.

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
| SourcePath| Określa ścieżkę źródłową pliku archiwum. To pole powinno być tar zip, lub. plik tar.gz. |
| Ścieżka_docelowa| Określa lokalizację, w której chcesz upewnij się, że są wyodrębniane zawartość archiwum.|
| Suma kontrolna| Definiuje typ używany do określenia, czy archiwum źródła został zaktualizowany. Wartości to: "ctime —", "mtime" lub "md5". Wartość domyślna to "md5".|
| Force| Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd. Przy użyciu **życie** właściwość zastępuje takie błędy. Wartość domyślna to **$false**.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|
| Upewnij się| Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w **docelowego**. Ustaw tę właściwość na "Brak", aby upewnić się, że istnieje zawartość. Ustaw ją na "Brak", aby upewnić się, że nie istnieją. Wartość domyślna to "Brak".|

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie **nxArchive** zasobów, aby upewnić się, że zawartość pliku archiwum o nazwie `website.tar` istnieją i są wyodrębniane w danej lokalizacji docelowej.

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