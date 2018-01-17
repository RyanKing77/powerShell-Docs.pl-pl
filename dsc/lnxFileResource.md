---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxFile zasobów"
ms.openlocfilehash: e4916414e4de29ab15d9c82c492671ebc16d5412
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC dla systemu Linux nxFile zasobów

**NxFile** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania plików i katalogów w węźle systemu Linux.

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
| Ścieżka_docelowa| Określa lokalizację, w której chcesz zapewnić stan pliku lub katalogu.| 
| SourcePath| Określa ścieżkę, z którego można skopiować pliku lub folderu zasobów. Ta ścieżka może być ścieżką lokalną lub `http/https/ftp` adresu URL. Zdalne `http/https/ftp` adresy URL są tylko obsługiwane, gdy wartość **typu** właściwość jest plik.| 
| Upewnij się| Określa, czy należy sprawdzić, czy plik istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że plik istnieje. Ustaw ją na "Brak", aby upewnić się, że plik nie istnieje. Wartość domyślna to "Brak".| 
| Typ| Określa, czy zasób konfigurowany jest katalog lub plik. Ustaw tę właściwość na "directory", aby wskazać, czy zasób jest katalogiem. Ustaw go na "plik", aby wskazać, czy zasób jest plik. Wartość domyślna to "plik"| 
| Zawartość| Określa zawartość pliku, takie jak określony ciąg.| 
| Suma kontrolna| Definiuje typ używany do określenia, czy dwa pliki są takie same. Jeśli **sumy kontrolnej** nie zostanie określona, tylko nazwa pliku lub katalogu jest używana do porównania. Wartości to: "ctime —", "mtime" lub "md5".| 
| Recurse| Wskazuje, czy podkatalogi są dołączone. Ta właściwość jest ustawiana **$true** aby wskazać, że chcesz podkatalogów, które zostaną uwzględnione. Wartość domyślna to **$false**. **Uwaga:** ta właściwość jest prawidłowa tylko gdy **typu** właściwość jest ustawiona na katalogu.| 
| Force| Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd. Przy użyciu **życie** właściwość zastępuje takie błędy. Wartość domyślna to **$false**.| 
| Łącza| Określa zachowanie dla łącza symbolicznego. Ustaw tę właściwość na "podążać" wykonaj łącza symbolicznego i działa w systemie docelowym łącza (np. Skopiuj plik zamiast łącza). Ustaw tę właściwość na "manage", które działają na link (np. Skopiuj link, sam). Ustaw tę właściwość na "Ignoruj", aby zignorować łącza symbolicznego.| 
| Grupa| Nazwa **grupy** do pliku lub katalogu.| 
| Tryb| Określa odpowiednie uprawnienia do zasobów, w notacji ósemkowe lub symbolicznych. (na przykład 777 lub rwxrwxrwx). Jeśli przy użyciu notacji symbolicznych, nie zapewniają pierwszego znaku, który wskazuje katalog lub plik.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Dodatkowe informacje


Linux i Windows przy użyciu znaki końca wiersza różnych w plikach tekstowych domyślnie, a to może spowodować nieoczekiwane wyniki podczas konfigurowania niektóre pliki z komputera z systemem Linux __nxFile__. Istnieje wiele sposobów zarządzania zawartością pliku Linux, unikając problemów spowodowanych znaki końca wiersza nieoczekiwany:

Krok 1: Skopiuj plik ze źródła zdalnego (http, https lub ftp): Utwórz plik w systemie Linux z żądaną zawartość i przemieszczanie go na serwerze sieci web lub ftp dostępny węzłów skonfigurujesz. Zdefiniuj __Ścieżka_źródłowa__ właściwości w __nxFile__ zasobów z adresem URL sieci web lub ftp do pliku.

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


Krok 2: Odczytać zawartości pliku skryptu programu PowerShell z [pobrania zawartości](https://technet.microsoft.com/en-us/library/hh849787.aspx) po ustawieniu __$OFS__ właściwości można użyć znaku podział wiersza systemu Linux.


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


Krok 3: Użyj funkcji programu PowerShell należy zastąpić Windows podziałów Linux, znaki podziału wiersza.

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

Poniższy przykład zapewnia, że katalog `/opt/mydir` istnieje, i istnieje plik z określoną zawartość tego katalogu.

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

