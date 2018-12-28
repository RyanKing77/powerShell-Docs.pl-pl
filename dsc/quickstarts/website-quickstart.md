---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Przewodnik Szybki Start — tworzenie witryny sieci Web za pomocą DSC
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404676"
---
> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Przewodnik Szybki Start — tworzenie witryny sieci Web za pomocą DSC

To ćwiczenie zawiera opis sposobu tworzenia i stosowania konfiguracji Desired State Configuration (DSC), od początku do końca.
Przykład użyjemy gwarantuje, że serwer ma `Web-Server` aktywna (IIS), a zawartość prostą witrynę sieci Web "Hello World" znajduje się w `intepub\wwwroot` katalogu tego serwera.

Aby uzyskać omówienie DSC i jak to działa, zobacz [Przegląd Desired State Configuration dla osób podejmujących](../overview/decisionMaker.md).

## <a name="requirements"></a>Wymagania

Aby uruchomić ten przykład, należy komputer z systemem Windows Server 2012 lub nowszego oraz programu PowerShell 4.0 lub nowszy.

## <a name="write-and-place-the-indexhtm-file"></a>Pisanie i umieścić ten plik index.htm

Najpierw utworzymy plik HTML, który będzie używany jako zawartość witryny sieci Web.

W folderze głównym, Utwórz folder o nazwie `test`.

W edytorze tekstów wpisz następujący tekst:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Zapisz jako `index.htm` w `test` folderu utworzonego wcześniej.

## <a name="write-the-configuration"></a>Zapisz konfigurację

A [konfiguracji DSC](../configurations/configurations.md) jest specjalną funkcję programu PowerShell, który definiuje, jak chcesz skonfigurować jeden lub więcej komputerów docelowych (węzły).

Wpisz następujące polecenie w środowisku PowerShell ISE:

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

Zostanie wyświetlony, wygląda na funkcję programu PowerShell dodając słowa kluczowego **konfiguracji** używane przed nazwą funkcji.

**Węzła** bloku określa węzeł docelowy należy skonfigurować w tym przypadku `localhost`.

Konfiguracja wymaga dwóch [zasobów](../resources/resources.md), **WindowsFeature** i **pliku**.
Zasoby wykonują pracę zapewnienia, że węzeł docelowy jest w stanie zdefiniowane przez tą konfigurację.

## <a name="compile-the-configuration"></a>Kompilowanie konfiguracji w

Dla konfiguracji DSC do zastosowania do węzła jej muszą najpierw być skompilowane w pliku MOF.
Aby to zrobić, należy uruchomić konfiguracji, takich jak funkcja.
W konsoli programu PowerShell przejdź do tego samego folderu, w której zapisano konfigurację i uruchom następujące polecenia, aby skompilować konfigurację do pliku MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Spowoduje to wygenerowanie następujące dane wyjściowe:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

Pierwszy wiersz sprawia, że funkcja konfiguracji jest dostępny w konsoli.
Drugi wiersz uruchamia konfigurację.
Wynik jest, że nowy folder o nazwie `WebsiteTest` jest tworzony jako podfolder bieżącego folderu.
`WebsiteTest` Folder zawiera plik o nazwie `localhost.mof`.
Jest to plik, który można następnie zastosować do węzła docelowego.

## <a name="apply-the-configuration"></a>Zastosuj konfigurację

Teraz, gdy masz skompilowany plik MOF, konfigurację można zastosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.

`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md), czyli aparatu DSC, aby zastosować konfigurację.
LCM działa wywoływania zasoby DSC, aby zastosować konfigurację.

W konsoli programu PowerShell przejdź do folderu, w której zapisano konfigurację, a następnie uruchom następujące polecenie:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testowanie konfiguracji

Możesz wywołać [Get DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) polecenia cmdlet, aby zobaczyć, czy konfiguracja zakończyła się pomyślnie.

Możesz również przetestować wyniki bezpośrednio, w tym przypadku, przechodząc do `http://localhost/` w przeglądarce sieci web.
Powinna zostać wyświetlona strona "Hello World" HTML, który został utworzony, w pierwszym kroku w tym przykładzie.

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej na temat konfiguracji DSC w [konfiguracje DSC](../configurations/configurations.md).
- Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasoby DSC](../resources/resources.md).
- Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).
