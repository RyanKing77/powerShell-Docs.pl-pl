---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxFile
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048570"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC dla systemu Linux zasób nxFile

**NxFile** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania pliki i katalogi w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| Ścieżka_docelowa| Określa lokalizację, w którym chcesz upewnić się, stan dla pliku lub katalogu.|
| SourcePath| Określa ścieżkę, z którego można skopiować zasobu pliku lub folderu. Ta ścieżka może być ścieżką lokalną lub `http/https/ftp` adresu URL. Zdalne `http/https/ftp` adresy URL są tylko obsługiwane w przypadku wartości **typu** właściwość jest plik.|
| Upewnij się| Określa, czy należy sprawdzić, czy plik istnieje. Ustaw tę właściwość "Present", aby upewnić się, że plik istnieje. Ustaw ją na "Brak", aby upewnić się, że plik nie istnieje. Wartość domyślna to "Istnieje".|
| Typ| Określa, czy zasób konfigurowany jest katalog lub plik. Ustaw tę właściwość na "directory", aby wskazać, czy zasób jest katalogiem. Ustaw ją na "plik", aby wskazać, czy zasób jest plik. Wartość domyślna to "file"|
| Zawartość| Określa zawartość pliku, na przykład określonego ciągu.|
| Suma kontrolna| Definiuje typ używany do określenia, czy dwa pliki są takie same. Jeśli **sumy kontrolnej** nie jest określona, tylko nazwa pliku lub katalogu jest używana do porównania. Wartości: "ctime", "mtime" lub "md5".|
| Recurse| Wskazuje, czy podkatalogi są uwzględniane. Ustaw tę właściwość na **$true** aby wskazać, że podkatalogi do uwzględnienia. Wartość domyślna to **$false**. **Uwaga:** Ta właściwość jest prawidłowa tylko kiedy **typu** ustawiono właściwość katalogu.|
| Force| Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu. Za pomocą **życie** właściwość zastępuje takie błędy. Wartość domyślna to **$false**.|
| Łącza| Określa zachowanie dla łącza symbolicznego. Ustaw tę właściwość na "follow" stosować linki symboliczne i działania w elemencie docelowym łącza (na przykład. Skopiuj plik zamiast łącza). Ustaw tę właściwość na "manage", które działają na link (np. Skopiuj link, sam). Ustaw tę właściwość na "ignorowania", aby zignorować łącza symbolicznego.|
| Grupa| Nazwa **grupy** być właścicielem pliku lub katalogu.|
| Tryb| Określa odpowiednich uprawnień dla zasobu, w notacji ósemkowej lub symboliczne. (na przykład 777 lub rwxrwxrwx). Przy użyciu notacji symbolicznych, nie są oferowane pierwszy znak, który wskazuje katalog lub plik.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Dodatkowe informacje


Z systemami Linux i Windows znaki podziału wiersza różnych w plikach tekstowych domyślnie używają i może to spowodować nieoczekiwane wyniki, podczas konfigurowania niektórych plików na komputerze z systemem Linux przy użyciu __nxFile__. Istnieje wiele sposobów, aby zarządzać zawartość pliku systemu Linux, unikając problemy spowodowane przez znaki podziału wiersza nieoczekiwany:

Krok 1. Skopiuj plik ze źródła zdalnego (http, https lub ftp): Utwórz plik w systemie Linux z żądaną zawartość i przygotowania na serwerze sieci web lub ftp dostępne węzły skonfigurujesz. Zdefiniuj __Ścieżka_źródłowa__ właściwość __nxFile__ zasobów za pomocą adresu URL sieci web lub ftp do pliku.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


Krok 2. Odczytać zawartość pliku w skrypcie programu PowerShell przy użyciu [pobrania zawartości](https://technet.microsoft.com/library/hh849787.aspx) po ustawieniu __$OFS__ właściwości, aby znak podziału wiersza systemu Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


Krok 3. Użyj funkcji programu PowerShell, aby zamienić Windows podziały wierszy przy użyciu systemu Linux, znaki podziału wiersza.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a>Przykład

Poniższy przykład zapewnia, że katalog `/opt/mydir` istnieje, i czy plik z określoną zawartość istnieje tego katalogu.

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```