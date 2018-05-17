---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Lista kontrolna tworzenia zasobu
ms.openlocfilehash: 76d9fecca8618fcc178975465f45cda0d0e04064
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="resource-authoring-checklist"></a>Lista kontrolna tworzenia zasobu
Ta lista kontrolna znajduje się lista najlepszych praktyk podczas tworzenia nowego zasobu usługi Konfiguracja DSC.
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Moduł zasobu zawiera plik psd1 i schema.mof dla każdego zasobu
Sprawdź, czy zasób ma poprawną strukturę i czy zawiera wszystkie wymagane pliki. Każdy moduł zasobów musi zawierać plik psd1 i każdy zasób złożone z systemem innym niż powinien mieć schema.mof pliku. Zasoby, które nie zawierają schematu nie są wyświetlane przez **Get-DscResource** i użytkownicy nie będą mogły używać funkcji intellisense podczas pisania kodu dla tych modułów w ISE.
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

## <a name="resource-and-schema-are-correct"></a>Zasób i schematu są prawidłowe ##
Sprawdź schemat zasobów (*. schema.mof) pliku. Można użyć [projektanta zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) ułatwiające opracowanie i przetestowanie schematu.
Upewnij się, że:
- Typy właściwości są prawidłowe (np. nie używaj ciąg dla właściwości, które akceptuje wartości liczbowe, należy użyć UInt32 lub inne typy liczbowe zamiast tego)
- Atrybuty właściwości są określone poprawnie jako: ([klucz], [wymagane], [zapisu], [read])
- Co najmniej jeden parametr w schemacie musi być oznaczony jako [klucz]
- [read] właściwości nie współistnieć wraz z dowolną z: [wymagane], [klucz], [zapisu]
- Jeśli określonych jest wiele kwalifikatory z wyjątkiem [odczytu], następnie [klucz] ma pierwszeństwo przed
- Jeśli [zapisu] i [wymagane] jest określona, a następnie pierwszeństwo będzie miała [wymagane]
- ValueMap jest określony w miarę potrzeb

Przykład:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- Przyjazna nazwa jest określona i potwierdza, DSC konwencje nazewnictwa

Przykład: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- Każde pole ma zrozumiały opis. Repozytorium PowerShell GitHub ma dobre przykłady, takich jak [. schema.mof dla xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Ponadto należy używać **xDscResource testu** i **xDscSchema testu** poleceń cmdlet z [projektanta zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) automatycznie sprawdzić zasobów i schematu:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Przykład:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Obciążenia zasobów bez błędów ##
Sprawdź, czy moduł zasobów można pomyślnie załadować.
Można to osiągnąć ręcznie, uruchamiając `Import-Module <resource_module> -force ` i potwierdzenie, że nie wystąpiły żadne błędy, lub przez zapisywanie automatyzacji testów. W przypadku drugiego nagłówka tej struktury można wykonać w przypadku testowego:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a>Zasób jest idempotentności w przypadku dodatnią
Jeden z podstawowych właściwości zasobów DSC jest projektu. Oznacza to, że stosowania konfiguracji DSC, zawierający wiele razy ten zasób będzie zawsze osiągnąć ten sam rezultat. Jeśli na przykład utworzymy konfigurację, która zawiera zasób następujących plików:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
Po zastosowaniu go po raz pierwszy, test.txt pliku powinna pojawić się w folderze C:\test. Jednak kolejnych uruchomieniach taką samą konfigurację, nie należy zmieniać stan maszyny (np. Brak kopii pliku test.txt należy utworzyć).
Zapewnienie zasób jest idempotentności można wywoływać wielokrotnie **TargetResource zestaw** podczas testowania zasobu bezpośrednio, lub zadzwoń **Start DscConfiguration** wiele razy w przypadku przeprowadzania pełnego testowania. Wynik powinien być taki sam po każdym Uruchom.


## <a name="test-user-modification-scenario"></a>Scenariusz modyfikacji użytkownika testowego ##
Zmienianie stanu urządzenia i ponowne uruchomienie usługi Konfiguracja DSC, można sprawdzić, czy **TargetResource zestaw** i **TargetResource testu** działać prawidłowo. Poniżej przedstawiono kroki, które należy wykonać:
1.  Rozpocznij od zasobu nie jest w stanie żądany.
2.  Konfiguracja uruchomieniowa o zasobie
3.  Sprawdź **DscConfiguration testu** zwraca wartość True
4.  Zmodyfikuj element skonfigurowanych poza żądanego stanu
5.  Sprawdź **DscConfiguration testu** zwraca wartość false, w tym miejscu jest bardziej konkretny przykład przy użyciu zasobów rejestru:
1.  Uruchom z kluczem rejestru nie jest w stanie żądaną
2.  Uruchom **Start DscConfiguration** konfiguracji umieszcza je w żądanym stanie i sprawdź jej przekazuje.
3.  Uruchom **DscConfiguration testu** i sprawdź, zwraca wartość true
4.  Zmodyfikuj wartość klucza, dzięki czemu nie jest żądanego stanu
5.  Uruchom **DscConfiguration testu** i sprawdź, zwraca wartość false
6.  Get-TargetResource funkcji została zweryfikowana przy użyciu Get DscConfiguration

Get-TargetResource powinien zwrócić szczegółowe informacje o bieżącym stanem zasobu. Upewnij się przetestować go przez wywołanie Get-DscConfiguration, po zastosowaniu konfiguracji i sprawdzanie, czy dane wyjściowe poprawnie odzwierciedla bieżący stan maszyny. Należy przetestować go oddzielnie, ponieważ wszelkie problemy w tym zakresie nie będzie dłużej wyświetlane podczas wywoływania metody Start DscConfiguration.

## <a name="call-getsettest-targetresource-functions-directly"></a>Wywołanie **Get/Set/Test-TargetResource** funkcje bezpośrednio ##

Upewnij się, że należy przetestować **Get/Set/Test-TargetResource** funkcje implementowana w zasobie przez bezpośrednie wywoływanie i sprawdzanie, czy działają zgodnie z oczekiwaniami.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Sprawdź przy użyciu pełnego **Start DscConfiguration** ##

Testowanie **Get/Set/Test-TargetResource** funkcje przez bezpośrednie wywoływanie jest ważne, ale nie wszystkie problemy nie zostaną odnalezione w ten sposób. Należy skoncentrować znaczną część testowania przy użyciu **Start DscConfiguration** lub z serwerem ściągania. W rzeczywistości jest to, jak użytkownicy będą używać zasobów, dlatego nie przypadku licznik nie uwzględniać znaczenia tego typu testy.
Możliwe typy problemy:
- Poświadczenie/sesji może zachowywać się inaczej, ponieważ DSC agent działa jako usługa.  Należy sprawdzić wszystkie funkcje tutaj pełnego.
- Błędy danych wyjściowych przez **Start DscConfiguration** mogą być inne niż wyświetlone podczas wywoływania metody **TargetResource zestaw** funkcji bezpośrednio.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Test zgodności DSC wszystkie obsługiwane platformy ##
Zasobu powinny działać na wszystkich platformach DSC obsługiwane (z systemem Windows Server 2008 R2 lub nowszym). Zainstaluj najnowsze WMF (Windows Management Framework) w systemie operacyjnym, aby pobrać najnowszą wersję usługi Konfiguracja DSC. Jeśli zasób nie działa na niektórych z tych platform zgodnie z projektem, ma zostać zwrócony komunikat o błędzie. Ponadto upewnij się, że zasobu sprawdza, czy polecenia cmdlet, wywoływana znajdują się na określonym komputerze. Windows Server 2012 dodano dużą liczbą nowych poleceń cmdlet, które nie są dostępne w systemie Windows Server 2008 R2, nawet w przypadku WMF zainstalowane.

## <a name="verify-on-windows-client-if-applicable"></a>Sprawdź w kliencie systemu Windows (jeśli dotyczy) ##
Jeden często przerwę testu jest sprawdzanie zasobów tylko w wersjach systemu Windows server. Wiele zasobów są również przeznaczona do pracy w SKU klienta, jeśli jest to istotne w przypadku sieci, nie zapomnij przetestować go także tych platform.
## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource zawiera listę zasobów ##
Po wdrożeniu modułu, wywołanie Get-DscResource powinny zawierać zasobu między innymi w wyniku. Jeśli na liście, nie można odnaleźć zasobu, upewnij się, czy plik schema.mof dla tego zasobu istnieje.
## <a name="resource-module-contains-examples"></a>Moduł zasobu zawiera przykłady ##
Tworzenie przykłady jakości, które będzie ułatwiała innym zrozumieć, jak z niego korzystać. Jest to ważne, szczególnie, ponieważ w przypadku wielu użytkowników zaliczenie dokumentacji przykładowy kod.
- Najpierw należy określić przykłady, które zostanie uwzględniony w module — co najmniej, powinno obejmować najważniejszych przypadków użycia dla zasobu:
- Modułu zawiera kilka zasobów, które wymagają współdziałają ze sobą scenariusz end-to-end, prosty przykład end-to-end w idealnym przypadku będzie pierwszy.
- Przykłady początkowej powinny być bardzo prosty — jak rozpocząć pracę z zasobami w małych partiach łatwych do (np. utworzenie nowego wirtualnego dysku twardego)
- Przykłady kolejnych powinien kompilacji na tych przykładów (np. utworzenie maszyny Wirtualnej z dysku VHD, usuwanie maszyny Wirtualnej, modyfikując maszyny Wirtualnej), a Pokaż zaawansowane funkcje (np. utworzenie maszyny Wirtualnej z pamięcią dynamiczną)
- Przykładowe konfiguracje należy ustawiać parametry (wszystkie wartości powinny zostać przekazane do konfiguracji jako parametry i nie powinna istnieć bez wartości zapisane na stałe):
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
- Dobrym rozwiązaniem, aby uwzględnić (komentarze out) przykładem wywołań konfiguracji o wartości rzeczywistych na końcu przykładowy skrypt jest.
Na przykład w powyższej konfiguracji nie jest zawsze widoczne, to najlepszy sposób, aby określić agenta użytkownika:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` W takim przypadku komentarz można wyjaśnić zamierzone wykonywania konfiguracji:
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- Przykładowo każdego zapisu krótki opis, który opisano, jakie operacje oraz na znaczenie właściwości parametrów.
- Upewnij się, przykłady obejmują większość ważne scenariusze dla zasobu i jeśli nic nie Brak, sprawdź, czy wszystkie wykonania i umieść maszyny w żądanym stanie.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Komunikaty o błędach są łatwe do zrozumienia i pomaganie użytkownikom w rozwiązywaniu problemów ##
Powinny być dobrym komunikaty:
- : Największych problem z komunikatami o błędach jest często nie istnieje, dlatego upewnij się, że są one dostępne.
- Łatwe do zrozumienia: kody błędów ludzkich do odczytu, nie zasłoniętej
- Dokładne: Co to jest dokładnie problem opisano
- Zwyczajowo: Porady jak rozwiązać ten problem
- Proces łagodnego: Nie winy użytkownika lub upewnij, możesz je zły upewnij się, sprawdź błędy w scenariuszach kompleksowego (przy użyciu **Start DscConfiguration**), ponieważ elementy różnią od tych zwrócony podczas uruchamiania funkcji zasobów bezpośrednio.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Komunikaty dziennika są łatwe do zrozumienia i informacyjnej (łącznie-verbose, — debugowania i dzienniki zdarzeń systemu Windows) ##
Upewnij się, że dzienniki wyjściowych przez zasób są łatwe do zrozumienia i podaj wartość dla użytkownika. Zasoby powinny output wszystkie informacje, które mogą być przydatne do użytkownika, ale nie więcej dzienników zawsze jest lepsze. Należy unikać nadmiarowości i wyprowadzania danych, która nie zapewniają dodatkowe wartość — nie są przenoszone ktoś przejść przez setki wpisów dziennika, aby znaleźć ich wyszukiwanie. Oczywiście nie dzienniki nie jest dopuszczalne rozwiązanie tego problemu albo.

Podczas testowania, należy również analizować pełne i dzienników debugowania (uruchamiając **Start DscConfiguration** z — pełne i — przełączników debugowania odpowiednio), jak również jako dzienniki zdarzeń systemu Windows. Aby wyświetlić dzienniki DSC ETW, przejdź do podglądu zdarzeń i otwórz następujący folder: aplikacji i usług firmy Microsoft - Windows - konfiguracji żądanego stanu.  Domyślnie zostanie operacyjne kanału, ale upewnij się, że możesz włączyć analityczne i debugowania kanały przed uruchomieniem konfiguracji.
Aby włączyć kanały analityczne/Debug, można wykonać skryptu poniżej:
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
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Implementacja zasobu nie zawiera ścieżki zapisane na stałe ##
Upewnić nie ścieżek zapisane na stałe w implementacji zasobów, zwłaszcza w wypadku zakładają języka (en-us), lub gdy występują zmienne systemowe, które mogą być używane.
Jeśli potrzebujesz zasobu dostęp do określonej ścieżki, używać zmiennych środowiskowych zamiast hardcoding ścieżki, ponieważ mogą się różnić na innych komputerach.

Przykład:

Zamiast:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
Można napisać:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a>Implementacja zasobu nie zawiera informacji o użytkowniku ##
Upewnij się, że nie ma żadnych nazw poczty e-mail, informacje o koncie lub nazwy osób w kodzie.
## <a name="resource-was-tested-with-validinvalid-credentials"></a>Zasób była testowana przy prawidłowy lub jest ono nieprawidłowe poświadczenia ##
Jeśli zasób przyjmuje poświadczenia jako parametr:
- Weryfikowanie działania zasobów, gdy System lokalny (lub konto komputera dla zasobów zdalnych) nie ma dostępu.
- Sprawdź działa zasobów z poświadczenia określone dla Get Set i testowanie
- Jeśli zasób uzyskuje dostęp do udziałów, przetestuj wszystkich wariantów potrzebnych do obsługi, takie jak:
  - Udziały standardowego systemu windows.
  - Udziały systemu plików DFS.
  - Udziały SAMBA (jeśli mają być obsługiwane systemu Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Zasób nie wymaga interaktywnego dane wejściowe ##
**Get/Set/Test-TargetResource** funkcje mają zostać wykonane automatycznie i nie musi czekać dla danych wejściowych użytkownika na każdym etapie wykonywania (np. nie należy używać **Get-Credential** wewnątrz tych funkcji). Jeśli potrzebujesz podawanie danych wejściowych użytkownika, należy przekazujesz ją do konfiguracji jako parametr podczas fazy kompilacji.
## <a name="resource-functionality-was-thoroughly-tested"></a>Funkcje zasobów została dokładnie przetestowana. ##
Ta lista kontrolna zawiera elementy, które są ważne do sprawdzenia i/lub często zostaną pominięte. Będzie bunch testów, głównie funkcjonalności te, które są specyficzne dla zasobu, testowania i nie są wymienione w tym miejscu. Nie zapomnij o ujemna przypadków testowych.
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Najlepsze praktyki: moduł zasobów zawiera folder testy przy użyciu skryptu ResourceDesignerTests.ps1 ##
Dobrym rozwiązaniem, aby utworzyć folder "testy" wewnątrz moduł zasobów, Utwórz plik ResourceDesignerTests.ps1 i dodać testów za pomocą jest **xDscResource testu** i **xDscSchema testu** dla wszystkich zasobów w danych Moduł.
Dzięki temu można szybko Zweryfikuj schematy wszystkich zasobów z modułów danego i nie wykonuje sprawdzanie przed opublikowaniem.
Dla xRemoteFile ResourceTests.ps1 może wyglądać tak proste, jak:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Najlepsze praktyki: folder zasobów zawiera zasób skryptu projektanta podczas generowania schematu ##
Każdy zasób powinien zawierać projektanta skryptu zasobu, który generuje schematu mof zasobu. Ten plik powinien być umieszczony w <ResourceName>\ResourceDesignerScripts i będzie nosić nazwę Generuj<ResourceName>Schema.ps1 dla zasobu xRemoteFile ten plik może być wywoływana GenerateXRemoteFileSchema.ps1 i zawierają:
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
## <a name="best-practice-resource-supports--whatif"></a>Najlepsze praktyki: zasób obsługuje - whatif ##
Jeśli zasób jest wykonywanie operacji "niebezpieczne", jest dobrym rozwiązaniem do implementowania - whatif. Po zakończeniu upewnij się, czy dane wyjściowe whatif poprawnie opisano operacje, co się stanie, jeśli polecenie zostało wykonane bez przełącznika whatif.
Sprawdź także, czy operacje nie wykonuj (nie do stanu węzła jest zmieniana) po ma przełącznika-whatif.
Załóżmy na przykład, że testujemy pliku zasobu. Poniżej znajdują się prostą konfigurację, która tworzy plik "test.txt" zawartość "test":
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
Jeśli firma Microsoft kompilacji, a następnie wykonaj konfiguracji z przełącznikiem-whatif, dane wyjściowe informuje NAS dokładnie co się stanie, gdy przeprowadzana konfiguracji. Konfiguracja się jednak nie zostało wykonane (test.txt Plik nie został utworzony).
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

Ta lista nie jest wyczerpująca, ale obejmuje wiele ważnych kwestii, które można napotkał podczas projektowania, tworzenia i testowania DSC zasobów.