---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Żądany stan konfiguracji Szybki Start"
ms.openlocfilehash: e21017f24db8c90229063895c1a7e4c6f0546d0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Żądany stan konfiguracji Szybki Start

Tego ćwiczenia przeprowadzi Cię przez tworzenia i stosowania konfiguracji konfiguracji żądanego stanu (DSC) od początku do końca.
Przykład użyjemy gwarantuje, że serwer ma `Web-Server` włączona funkcja (IIS), a zawartość witryny sieci Web "Hello World" proste znajduje się w `intepub\wwwroot` katalogu tego serwera.

Omówienie usługi Konfiguracja DSC jest i jak działa, zobacz [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md).

## <a name="requirements"></a>Wymagania

Aby uruchomić ten przykład, należy komputer z systemem Windows Server 2012 lub nowszym i programu PowerShell 4.0 lub nowszy.

## <a name="write-and-place-the-indexhtm-file"></a>Zapis i umieścić go index.htm

Najpierw utworzymy plik HTML, który będzie używany jako zawartości witryny sieci Web.

W folderze głównym, Utwórz folder o nazwie `test`.

W edytorze tekstów należy wpisać następujący tekst:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Zapisz jako `index.htm` w `test` folderu utworzonego wcześniej. 

## <a name="write-the-configuration"></a>Zapisać konfiguracji

A [konfiguracji DSC](configurations.md) jest specjalnych funkcji programu PowerShell, która definiuje sposób skonfigurowania jednego lub więcej komputerów docelowych (węzłów).

W programie PowerShell ISE wpisz następujące polecenie:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Zapisz plik jako `WebsiteTest.ps1`.

Widać wygląda funkcji programu PowerShell, dodając słowa kluczowego **konfiguracji** używany przed nazwę funkcji.

**Węzła** bloku określa węzeł docelowy jest skonfigurowany w tym przypadku `localhost`.

Konfiguracja wymaga dwóch [zasobów](resources.md), [WindowsFeature](windowsFeatureResource.md) i [pliku](fileResource.md).
Zasoby czy pracy zapewnienie węzeł docelowy jest w stanie określonym w konfiguracji.

## <a name="compile-the-configuration"></a>Konfiguracja kompilacji

Dla konfiguracji DSC ma zostać zastosowany do węzła go musi najpierw zostać skompilowany w pliku MOF.
Aby to zrobić, należy uruchomić konfiguracji, takich jak funkcja.
W konsoli programu PowerShell przejdź do folderu, w którym zapisano konfigurację i uruchom następujące polecenia, aby skompilować konfigurację do pliku MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Spowoduje to wygenerowanie następujących danych wyjściowych:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

Pierwszy wiersz sprawia, że funkcja konfiguracji jest dostępne w konsoli.
Drugi wiersz uruchamia konfigurację.
Wynik jest, że nowy folder o nazwie `WebsiteTest` zostanie utworzona jako podfolder bieżącego folderu.
`WebsiteTest` Folder zawiera plik o nazwie `localhost.mof`.
Jest to plik, który można zastosować do węzła docelowego.

## <a name="apply-the-configuration"></a>Zastosuj konfigurację

Teraz, gdy masz skompilowanych MOF konfiguracji można stosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) polecenia cmdlet.

`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](metaConfig.md), która jest aparat DSC, aby zastosować konfigurację.
LCM działa wywoływania zasobów DSC, aby zastosować konfigurację.

W konsoli programu PowerShell przejdź do folderu, w którym zapisano konfigurację i uruchom następujące polecenie:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Przetestuj konfigurację

Możesz wywołać [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) polecenia cmdlet, aby zobaczyć, czy konfiguracja zakończyła się pomyślnie. 

Można również sprawdzić wyniki bezpośrednio, w tym przypadku przechodząc do `http://localhost/` w przeglądarce sieci web.
Powinna zostać wyświetlona strona "Hello World" HTML, który został utworzony jako pierwszy krok w tym przykładzie.

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej o konfiguracji DSC w [konfiguracji DSC](configurations.md).
- Zobacz, jakie zasoby DSC są dostępne oraz sposobu tworzenia niestandardowych zasobów DSC w [zasobów DSC](resources.md).
- Znajdź konfiguracji DSC i zasobów w [galerii programu PowerShell](https://www.powershellgallery.com/).



