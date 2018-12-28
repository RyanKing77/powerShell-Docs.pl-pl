---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Lista kontrolna tworzenia zasobu
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405083"
---
# <a name="resource-authoring-checklist"></a>Lista kontrolna tworzenia zasobu

Ta lista kontrolna jest lista najlepszych rozwiązań, podczas tworzenia nowego zasobu DSC.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Moduł zasobów zawiera plik psd1 i schema.mof dla każdego zasobu

Sprawdź, czy zasób ma poprawną strukturę i czy zawiera wszystkie wymagane pliki. Każdy moduł zasobów powinien zawierać plik psd1 i wszystkich zasobów innych niż złożone powinny mieć schema.mof pliku. Zasoby, które nie zawierają schematu, nie będą wyświetlane przez `Get-DscResource` i użytkownicy nie będą mogli korzystać z funkcji intellisense podczas pisania kodu dla tych modułów w środowisku ISE.
Struktura katalogów xRemoteFile zasobu, który jest częścią programu [moduł zasobów xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), wygląda następująco:

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Zasób i schematu są poprawne

Sprawdź schematu zasobów (*. schema.mof) pliku. Możesz użyć [projektancie zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) ułatwiające tworzenie i testowanie schematu.
Upewnij się, że:

- Typy właściwości są prawidłowe (np. nie należy używać ciągu dla właściwości, które akceptuje wartości liczbowych, należy użyć UInt32 lub inne typy liczbowe zamiast)
- Atrybuty właściwości są poprawnie określone jako: ([klucz], [wymagane], [napisać], [do odczytu])
- Co najmniej jeden parametr w schemacie musi zostać oznaczone jako [klucz]
- [do odczytu] właściwości nie współistnieć wraz z dowolnego z: [wymagane], [klucz], [zapisu]
- Jeśli nie określono wiele kwalifikatory z wyjątkiem [do odczytu], następnie [klucz] ma pierwszeństwo przed
- Jeśli [zapisu] i [wymagane] jest określony, a następnie pierwszeństwo [wymagane]
- Określono ValueMap przykład zgodnie z wymaganiami:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Przyjazna nazwa jest określona i potwierdza, konwencje nazewnictwa DSC

  Przykład: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Każde pole ma zrozumiały opis. Repozytorium GitHub dla programu PowerShell ma dobre przykłady, takie jak [. schema.mof dla xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Ponadto należy używać **xDscResource testu** i **xDscSchema testu** polecenia cmdlet z [projektancie zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) umożliwia automatyczne weryfikowanie zasobu i schematu:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Przykład:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Zasób ładuje się bez błędów

Sprawdź, czy moduł zasobów może być załadowany pomyślnie.
Można to osiągnąć ręcznie, uruchamiając `Import-Module <resource_module> -force` i potwierdzenie, że nie wystąpiły żadne błędy, lub przez zapisywanie Automatyzacja testów. W przypadku drugiego nagłówka tej struktury, można wykonać w przypadku testowym:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Zasób jest idempotentna, w tym przypadku dodatnią

Jednym z podstawowych charakterystyk zasobów DSC jest idempotentność. Oznacza to, że trwa operacja zastosowania konfiguracji DSC, zawierająca ten zasób wielokrotnie będzie zawsze ten sam efekt. Jeśli na przykład możemy utworzyć konfigurację, która zawiera następujące zasoby pliku:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Po zastosowaniu go po raz pierwszy, jako plik powinna zostać wyświetlona w `C:\test` folderu. Jednak kolejnych uruchomień taką samą konfigurację nie należy zmieniać stan maszyny (np. nie kopie `test.txt` można utworzyć pliku).
Aby upewnić się, zasób jest idempotentna, można wywoływać wielokrotnie `Set-TargetResource` podczas testowania zasobu bezpośrednio lub zadzwoń `Start-DscConfiguration` wiele razy podczas wykonywania pełnego testowania. Wynik powinien być taki sam, po każdym przebiegu.

## <a name="test-user-modification-scenario"></a>Scenariusz modyfikacji użytkownika testowego

Zmienianie stanu komputera, a następnie ponownemu uruchamianiu DSC, można sprawdzić, czy `Set-TargetResource` i `Test-TargetResource` działać prawidłowo. Poniżej przedstawiono kroki, które należy wykonać:

1. Zacznij od zasobu nie jest w żądanym stanie.
2. Uruchom konfigurację z zasobem usługi
3. Sprawdź `Test-DscConfiguration` zwraca wartość True
4. Modyfikowanie skonfigurowany element, aby brakować żądanego stanu
5. Sprawdź `Test-DscConfiguration` zwraca wartość false

Oto przykład bardziej konkretne, używając zasobu rejestru:

1. Uruchom za pomocą klucza rejestru nie jest w żądanym stanie
2. Uruchom `Start-DscConfiguration` przy użyciu konfiguracji, aby umieścić go w żądanym stanie i weryfikować ją przekazuje.
3. Uruchom `Test-DscConfiguration` i sprawdź, funkcja zwraca wartość true
4. Zmodyfikuj wartość klucza, tak, aby nie jest w żądanym stanie
5. Uruchom `Test-DscConfiguration` i sprawdź, zwraca wartość false
6. `Get-TargetResource` funkcja została zweryfikowana przy użyciu `Get-DscConfiguration`

`Get-TargetResource` powinno zwrócić szczegółowe informacje o bieżącym stanem zasobu. Pamiętaj ją przetestować, wywołując `Get-DscConfiguration` po zastosowaniu konfiguracji i weryfikowanie, że dane wyjściowe poprawnie odzwierciedla bieżący stan maszyny. Ważne jest, aby przetestować go oddzielnie, ponieważ wszelkie problemy, w tym obszarze nie będą wyświetlane podczas wywoływania `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Wywołaj **Get/Set/Test-TargetResource** funkcje bezpośrednio

Upewnij się, że testujesz **Get/Set/Test-TargetResource** funkcji realizowanych w swoim zasobie, bezpośrednie wywoływanie i weryfikowanie, czy działają one zgodnie z oczekiwaniami.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Sprawdź przy użyciu typu End to End **Start-DscConfiguration**

Testowanie **Get/Set/Test-TargetResource** funkcji przez bezpośrednie wywoływanie jest ważne, ale nie wszystkie problemy zostaną odnalezione w ten sposób. Należy skoncentrować się znaczna część testowania przy użyciu `Start-DscConfiguration` lub serwerze ściągania. W rzeczywistości jest to, jak użytkownicy będą używać zasobów, dzięki czemu nie uwzględniać znaczenie tego rodzaju testy.
Możliwe typy problemów:

- Poświadczenie/sesji może zachowywać się inaczej agenta DSC jest uruchamiana jako usługa.  Należy przetestować każdej funkcji, w tym miejscu typu end to end.
- Błędy generowane przez `Start-DscConfiguration` mogą być inne niż te wyświetlane podczas wywoływania `Set-TargetResource` funkcji bezpośrednio.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Platformy obsługiwane przez test zgodności na wszystkich DSC

Zasób powinny działać na wszystkich platformach DSC obsługiwane (Windows Server 2008 R2 i nowszych). Instalowanie najnowszej wersji platformy WMF (Windows Management Framework) dla Twojego systemu operacyjnego, aby pobrać najnowszą wersję DSC. Jeśli zasób nie działa na niektórych z tych platform zgodnie z projektem, powinny być zwrócone określony komunikat o błędzie. Ponadto upewnij się, że zasób sprawdza, czy polecenia cmdlet wywoływanego są obecne na określonym komputerze. Windows Server 2012 dodano dużą liczbą nowych poleceń cmdlet, które nie są dostępne w systemie Windows Server 2008 R2, nawet w przypadku programu WMF zainstalowane.

## <a name="verify-on-windows-client-if-applicable"></a>Sprawdź na kliencie Windows (jeśli dotyczy)

Jednym bardzo często przerwy testu jest sprawdzanie zasobów tylko w wersjach server systemu Windows. Wiele zasobów również zostały zaprojektowane do pracy na jednostki SKU klienta, więc jeśli jest to istotne w Twoim przypadku, nie zapomnij go przetestować na tych platformach, a także.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource zawiera listę zasobów

Po wdrożeniu modułu wywoływania `Get-DscResource` w wyniku pomysłem jest wystawienie zasobu m.in. Jeśli nie można odnaleźć zasób na liście, upewnij się, ten plik schema.mof dla tego zasobu istnieje.

## <a name="resource-module-contains-examples"></a>Moduł zasobów zawiera przykłady

Tworzenie przykładów jakości, które ułatwiają innym osobom dowiedzieć się, jak z niego korzystać. Jest to niezwykle istotne, szczególnie w przypadku, ponieważ wielu użytkowników traktować przykładowego kodu jako dokumentacji.

- Po pierwsze należy ustalić, przykłady, które zostaną dołączone za pomocą modułu — co najmniej, powinny obejmować najważniejszych przypadków użycia dla zasobu:
- Jeśli modułu zawiera kilka zasobów, które wymagają pracy zespołowej, scenariusz end-to-end, w idealnym przypadku będzie istnieć pierwszy przykład podstawowy end-to-end.
- Przykłady początkowe powinny być bardzo proste — jak rozpocząć pracę z zasobami w małych partiach łatwych do zarządzania (np. tworzenia nowego wirtualnego dysku twardego)
- Przykłady kolejnych powinien rozwijać tych przykładów (np. Tworzenie maszyny Wirtualnej z dysku VHD, usunięcie maszyny Wirtualnej, modyfikując maszyn wirtualnych) i wyświetlania informacji dotyczących zaawansowanych funkcji (np. Tworzenie maszyny Wirtualnej z pamięcią dynamiczną)
- Przykładowe konfiguracje należy ustawiać parametry (wszystkie wartości mają być przekazywane do konfiguracji jako parametry i powinno być żadnych wartości zapisane na stałe):

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- Jest dobrym rozwiązaniem, aby uwzględnić (out) komentarzami przykładem wywołania konfiguracji przy użyciu rzeczywistych wartości na końcu przykładowy skrypt.
  Na przykład w powyższej konfiguracji nie jest koniecznie oczywiste, że najlepszym sposobem, aby określić UserAgent jest:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` W tym przypadku komentarz może wyjaśnić zamierzony wykonanie konfiguracji:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- W każdym przykładzie krótki opis, który wyjaśnia, co robi i zapisywać znaczenie parametrów.
- Upewnij się, przykłady obejmują większość ważnych scenariuszy zasobu bazy danych i jeśli nic nie brakuje, sprawdź, czy wszystkie wykonania i przełączyć maszynę w żądanym stanie.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Komunikaty o błędach są łatwe do zrozumienia i pomaganie użytkownikom w rozwiązywaniu problemów

Komunikaty o błędach dobre powinny być następujące:

- Brak: Największy problem z komunikatami o błędach jest często nie istnieje, dlatego upewnij się, że są one dostępne.
- Łatwe do zrozumienia: Kody błędów ludzkich możliwy do odczytu, nie zasłoniętej
- Dokładny: Opisano, jakie dokładnie problem
- Konstruktywnych informacji: Porady dotyczące sposobu rozwiązania problemu
- Proces łagodnego: Nie blame użytkownika lub stały się, że nieprawidłowe

Upewnij się, sprawdź błędy w scenariuszach typu End to End (przy użyciu `Start-DscConfiguration`), ponieważ one mogą się różnić od tych zwracane po uruchomieniu funkcji zasobów bezpośrednio.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Komunikaty dziennika są łatwe do zrozumienia i informacyjnej (w tym — pełne, — debugowania, jak i dzienniki zdarzeń systemu Windows)

Upewnij się, że dzienniki zwrócone przez zasób są łatwe do zrozumienia i podać wartość dla użytkownika. Zasoby ma produkt wyjściowy wszystkie informacje, które mogą być pomocne dla użytkowników, ale nie więcej dzienników zawsze jest lepiej. Należy unikać nadmiarowości i wyprowadzanie danych, które nie zapewniają dodatkową wartość — nie należy ktoś przechodzą przez setki wpisy dziennika, aby można było znaleźć, czego szukają. Oczywiście żadne dzienniki nie jest to dopuszczalne rozwiązanie tego problemu albo.

Podczas testowania, należy również analizować pełne i debugowania dzienniki (uruchamiając `Start-DscConfiguration` z `–Verbose` i `–Debug` zmienia odpowiednio), jak również jako dzienniki zdarzeń systemu Windows. Aby wyświetlić dzienniki DSC ETW, przejdź do podglądu zdarzeń, a następnie otwórz następujący folder: Aplikacje i usługi firmy Microsoft - Windows - Desired State Configuration.  Domyślnie zostanie kanał operacyjny, ale upewnij się, możesz włączyć analityczne i debugowania kanały przed uruchomieniem konfiguracji.
Aby włączyć kanały analityczne/Debug, można wykonać poniższy skrypt:

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Implementacja zasób nie zawiera ścieżki zapisane na stałe

Upewnij się w implementacji zasobów istnieje nie ścieżek zapisane na stałe, zwłaszcza w przypadku, gdy zakładają też języka (en-us), lub gdy występują zmiennych systemowych, które mogą być używane.
Jeśli dostęp do określonej ścieżki, użyj zmiennych środowiskowych zamiast hardcoding zasobu ścieżki, ponieważ mogą się różnić na innych komputerach.

Przykład:

Zamiast:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Można napisać:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Implementacja zasobów nie zawiera informacji o użytkowniku

Upewnij się, że nie ma żadnych wiadomości e-mail, informacje o koncie, nazwiska lub nazwy osoby w kodzie.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Zasób został przetestowany z prawidłową nieprawidłowe poświadczenia

Jeśli zasób przyjmuje poświadczenia, jako parametr:

- Sprawdź, czy zasób działa, gdy System lokalny (lub konto komputera dla zasobów zdalnych) nie ma dostępu.
- Sprawdź działa zasobów przy użyciu poświadczeń, określony dla pobierania ustawiania i testowanie
- Jeśli zasób uzyskuje dostęp do udziałów, przetestuj wszystkich wariantów, czego potrzebujesz do obsługi, takie jak:
  - Standardowy system windows udziałów.
  - Udziały systemu plików DFS.
  - Udziały SAMBA (jeśli mają być obsługiwane systemu Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Zasób nie wymaga wprowadzania interaktywne

**Get/Set/Test-TargetResource** funkcje mają zostać wykonane automatycznie i nie należy czekać do wejściowych użytkownika na każdym etapie cyklu wykonywania (np. nie należy używać `Get-Credential` wewnątrz tych funkcji). Jeśli musisz podać dane wejściowe użytkownika, należy przekazać go do konfiguracji jako parametr w fazie kompilacji.

## <a name="resource-functionality-was-thoroughly-tested"></a>Funkcje zasobów została dokładnie przetestowana.

Ta lista kontrolna zawiera elementy, które są ważne do zbadania i/lub często zostaną pominięte. Będzie istnieć wiele testów, głównie funkcjonalności te, które są specyficzne dla zasobu, testowania i nie są tutaj wymienione. Nie zapomnij o ujemna przypadków testowych.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Najlepszym rozwiązaniem jest: Moduł zasobów zawiera folder testy za pomocą skryptu ResourceDesignerTests.ps1

Jest dobrą praktyką jest tworzenie folderu "testy" wewnątrz modułu zasobów, tworzenie `ResourceDesignerTests.ps1` pliku i Dodaj testy przy użyciu **xDscResource testu** i **xDscSchema testu** dla wszystkich zasobów w danych modułu.
Dzięki temu można szybko sprawdzić poprawność schematów wszystkie zasoby z danym modułów i nie wykonuje sprawdzanie przed opublikowaniem.
Aby uzyskać xRemoteFile `ResourceTests.ps1` mogłoby wyglądać tak proste, jak:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Najlepszym rozwiązaniem jest: Folder zasobów zawiera zasób skryptu projektanta do generowania schematu

Każdy zasób może zawierać zasobu skryptu projektanta, które generuje schemat mof zasobu. Ten plik należy umieścić w `<ResourceName>\ResourceDesignerScripts` i będzie nosić nazwę Generuj `<ResourceName>Schema.ps1` dla zasobu xRemoteFile ten plik będzie nazywany `GenerateXRemoteFileSchema.ps1` i zawierać:

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>Najlepszym rozwiązaniem jest: Zasób obsługuje - WhatIf

Jeśli zasób jest wykonywanie operacji "niebezpiecznych", jest dobrym rozwiązaniem, aby zaimplementować `-WhatIf` funkcji. Po zakończeniu upewnij się, że `-WhatIf` dane wyjściowe poprawnie opisuje operacje, co się stanie, jeśli polecenie zostało wykonane bez `-WhatIf` przełącznika.
Sprawdź także, czy nie jest wykonywane operacje (nie do stanu węzła zmian) podczas `–WhatIf` przełącznik jest obecny.
Załóżmy na przykład, że testujemy pliku zasobów. Poniżej znajduje się prostej konfiguracji, co powoduje utworzenie pliku `test.txt` z zawartością "test":

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

Jeśli firma Microsoft kompilacji, a następnie wykonanie konfiguracji z `-WhatIf` przełącznika, dane wyjściowe informuje NAS, dokładnie co się stanie, gdy Uruchamiamy konfiguracji. Konfiguracja samego jednak nie zostało wykonane (`test.txt` nie utworzono pliku).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Ta lista nie jest wyczerpująca, ale obejmuje wiele ważnych kwestii, które można napotkać podczas projektowania, opracowywania i testowania zasoby DSC.
