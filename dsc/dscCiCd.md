---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Tworzenie potoku ciągłej integracji i ciągłe wdrażanie w usłudze Konfiguracja DSC
ms.openlocfilehash: faeef5022cbd984cab0620b69db19de8b84cca0e
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940348"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Tworzenie potoku ciągłej integracji i ciągłe wdrażanie w usłudze Konfiguracja DSC

W tym przykładzie pokazano, jak utworzyć potok ciągłe wdrażanie ciągłe/integracji (CI/CD) przy użyciu programu PowerShell, DSC Pester i Visual Studio Team Foundation Server (TFS).

Po potoku jest utworzony i skonfigurowany, można użyć pełni wdrożenia, skonfigurowania i przetestowania serwera DNS i skojarzonych rekordów hosta.
Ten proces symuluje pierwsza część potok, który będzie używany w środowisku projektowym.

Automatyczne potoku CI/CD pomaga w aktualizacji oprogramowania szybciej i bardziej niezawodnie zapewnienie, że cały kod jest przetestowany i czy bieżąca kompilacja kodu jest dostępna przez cały czas.

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przykładu, należy zapoznać się z następujących czynności:

- Pojęcia dotyczące elementu konfiguracji CD. Dobrym odwołanie znajduje się w temacie [Model potoku wersji](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) kontroli źródła
- [Pester](https://github.com/pester/Pester) testowania framework
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Dane będą potrzebne

Aby skompilować i uruchomić ten przykład, należy w środowisku zawierającym wiele komputerów i/lub maszyn wirtualnych.

### <a name="client"></a>Client

Jest to komputer, na którym będzie wykonywać wszystkie pracy konfigurowania i uruchamiania przykładzie.

Komputer kliencki musi być komputerem z systemem Windows z zainstalowane następujące elementy:

- [Git](https://git-scm.com/)
- sklonowany z repozytorium git lokalnego https://github.com/PowerShell/Demo_CI
- Edytor tekstu, takich jak [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Komputer obsługujący serwer TFS, w którym zostaną zdefiniowane kompilacji i wydania.
Ten komputer musi mieć [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) zainstalowane.

### <a name="buildagent"></a>BuildAgent

Komputer z systemem Windows kompilacji agenta, która tworzy projekt.
Ten komputer musi mieć i uruchom agenta kompilacji systemu Windows.
Zobacz [wdrażania agenta w systemie Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) dla agenta kompilacji instrukcje dotyczące sposobu instalowania i uruchamiania systemu Windows.

Należy również zainstalować zarówno `xDnsServer` i `xNetworking` DSC modułów na tym komputerze.

### <a name="testagent1"></a>TestAgent1

Jest to komputer, który jest skonfigurowany jako serwer DNS za pomocą konfiguracji DSC w tym przykładzie.
Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Jest to komputer, który obsługuje ten przykład konfiguruje witryny sieci Web.
Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Dodaj kod do TFS

Zaczniemy Tworzenie repozytorium Git w programie TFS, a następnie importowanie kod z lokalnym repozytorium na komputerze klienckim.
Jeśli nie ma już sklonować repozytorium Demo_CI na komputerze klienckim, zrób tak teraz za pomocą następującego polecenia git:

`git clone https://github.com/PowerShell/Demo_CI`

1. Na komputerze klienckim przejdź do serwera TFS w przeglądarce sieci web.
1. W programie TFS [Tworzenie nowego projektu zespołowego](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) o nazwie Demo_CI.

   Upewnij się, że **kontroli wersji** ustawiono **Git**.
1. Na komputerze klienckim należy dodać zdalnej do repozytorium, utworzony w programie TFS przy użyciu następującego polecenia:

   `git remote add tfs <YourTFSRepoURL>`

   Gdzie `<YourTFSRepoURL>` jest adres URL klonowania służący do repozytorium TFS utworzony w poprzednim kroku.

   Jeśli nie wiadomo, gdzie można znaleźć ten adres URL, zobacz [istniejące repozytorium Git Clone](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Wypchnij kod z lokalnym repozytorium do repozytorium TFS przy użyciu następującego polecenia:

   `git push tfs --all`
1. Repozytorium TFS zostaną wypełnione z kodem Demo_CI.

> [!NOTE]
> W tym przykładzie użyto kod w `ci-cd-example` gałęzi repozytorium Git.
> Należy określić gałęzi jako gałąź domyślną projektu TFS i wyzwalaczy CI/CD tworzenia.

## <a name="understanding-the-code"></a>Opis kodu

Przed utworzymy potoki kompilowanie i wdrażanie przyjrzymy kodu, aby zrozumieć, co się dzieje.
Na komputerze klienckim otwórz w ulubionym edytorze tekstów i przejdź do katalogu głównego repozytorium Demo_CI Git.

### <a name="the-dsc-configuration"></a>Konfiguracja DSC

Otwórz plik `DNSServer.ps1` (od głównego lokalnego repozytorium Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).

Ten plik zawiera konfiguracji DSC, który konfiguruje serwer DNS. Poniżej przedstawiono w całości:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Powiadomienie `Node` instrukcji:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Znajduje to węzły, które zostały zdefiniowane jako mający rolę `DNSServer` w [dane konfiguracji](configData.md), który jest tworzony przez `DevEnv.ps1` skryptu.

Możesz przeczytać dodatkowe informacje `Where` metoda [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Ważne jest określenie węzłów przy użyciu danych konfiguracji, podczas wykonywania elementu konfiguracji, ponieważ węzeł informacji prawdopodobnie spowoduje zmianę między środowiskami i przy użyciu danych konfiguracji umożliwia łatwe wprowadzić zmiany w informacjach węzła bez konieczności zmieniania kodu konfiguracji.

W pierwszym bloku zasobów, wywołuje konfiguracji [WindowsFeature](windowsFeatureResource.md) aby upewnić się, że jest włączona funkcja DNS.
Bloki zasobów, które należy wykonać wywołanie zasobów z [xDnsServer](https://github.com/PowerShell/xDnsServer) modułu, aby skonfigurować strefa podstawowa i rekordów DNS.

Zwróć uwagę, że dwa `xDnsRecord` bloki są ujęte w `foreach` pętli, które iterację tablic w danych konfiguracji.
Ponownie, dane konfiguracji są tworzone przez `DevEnv.ps1` skryptu, który przyjrzymy dalej.

### <a name="configuration-data"></a>Dane konfiguracji

`DevEnv.ps1` Pliku (z katalogu lokalnego repozytorium Demo_CI `./InfraDNS/DevEnv.ps1`) określa dane konfiguracyjne specyficzne dla środowiska w tablicy skrótów, a następnie przekazuje tego obiektu hashtable do wywołania `New-DscConfigurationDataDocument` funkcja, która jest zdefiniowana w `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

`DevEnv.ps1` Pliku:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

`New-DscConfigurationDataDocument` — Funkcja (zdefiniowany w `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programowo tworzy dokument danych konfiguracji z hashtable (dane węzła) i tablicy (z systemem innym niż węzeł danych), które są przekazywane jako `RawEnvData` i `OtherEnvData` parametrów.

W tym przypadku tylko `RawEnvData` parametr jest używany.

### <a name="the-psake-build-script"></a>Psake skryptu kompilacji

[Psake](https://github.com/psake/psake) kompilacji skryptu zdefiniowane w `Build.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Build.ps1`) definiuje zadania, które są częścią kompilacji.
Definiuje również inne zadania zależy od każdego zadania.
Po wywołaniu, skrypt psake upewnia się, że określonego zadania (lub zadania o nazwie `Default` Jeśli nie zostanie określona) działa i że wszystkie zależności również uruchomić (tak, aby uruchomić zależności zależności, jest rekursywny, i tak dalej).

W tym przykładzie `Default` zadań jest zdefiniowany jako:

```powershell
Task Default -depends UnitTests
```

`Default` Zadanie ma się implementacji, ale zależy `CompileConfigs` zadań.
Wynikowa łańcuch zależności zadań zapewnia, że wszystkie zadania w skrypcie kompilacji są uruchamiane.

W tym przykładzie skrypt psake jest wywoływany przez wywołanie do `Invoke-PSake` w `Initiate.ps1` (znajdującym się w folderze głównym repozytorium Demo_CI):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Gdy utworzymy definicję kompilacji w naszym przykładzie w programie TFS, firma Microsoft będzie dostarczać naszych pliku skryptu psake jako `fileName` parametru w ramach tego skryptu.

Skrypt kompilacji definiuje następujące zadania:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Uruchamia `DevEnv.ps1`, który generuje plik danych konfiguracji.

#### <a name="installmodules"></a>InstallModules

Instaluje moduły wymagane przez konfigurację `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Wywołania [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Uruchamia [Pester](https://github.com/pester/Pester/wiki) testów jednostkowych.

#### <a name="compileconfigs"></a>CompileConfigs

Kompiluje konfigurację (`DNSServer.ps1`) do pliku MOF przy użyciu danych konfiguracji wygenerowane przez `GenerateEnvironmentFiles` zadań.

#### <a name="clean"></a>Czyszczenie

Tworzy foldery używane dla przykładu i usuwa wszystkie wyniki testów, pliki danych konfiguracji i moduły poprzedniej działa.

### <a name="the-psake-deploy-script"></a>Psake wdrożenia skryptu

[Psake](https://github.com/psake/psake) skrypt wdrożenia zdefiniowane w `Deploy.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Deploy.ps1`) definiuje zadań, które wdrażanie i uruchamianie konfiguracji.

`Deploy.ps1` definiuje następujące zadania:

#### <a name="deploymodules"></a>DeployModules

Uruchamia sesję programu PowerShell na `TestAgent1` i instaluje modułów zawierających DSC zasoby wymagane do konfiguracji.

#### <a name="deployconfigs"></a>DeployConfigs

Wywołania [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) polecenia cmdlet, aby uruchomić konfigurację na `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Uruchamia [Pester](https://github.com/pester/Pester/wiki) testów integracji.

#### <a name="acceptancetests"></a>AcceptanceTests

Uruchamia [Pester](https://github.com/pester/Pester/wiki) testy akceptacji.

#### <a name="clean"></a>Czyszczenie

Usunięcie wszelkich modułów zainstalowanych w poprzedniej uruchamia i zapewnia, że istnieje folder wyników testu.

### <a name="test-scripts"></a>Testowanie skryptów

Testy akceptacji, integracja i jednostki są zdefiniowane w skryptach w `Tests` folder (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Tests`), każdy w plikach o nazwie `DNSServer.tests.ps1` w ich odpowiednich folderów.

Użyj skryptów testu [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

#### <a name="unit-tests"></a>Testy jednostkowe

Konfiguracje testów DSC, aby upewnić się, czy konfiguracje wykona, czego oczekuje się po uruchomieniu testów jednostkowych.
Skrypt używa testu jednostkowego [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Testy integracji

Testy integracji jest przetestowanie konfiguracji systemu, aby upewnić się, że gdy zintegrowana z innymi składnikami, system jest skonfigurowany zgodnie z oczekiwaniami. Te testy wykonywane w docelowym węźle po skonfigurowaniu usłudze Konfiguracja DSC.
Skrypt testu integracji używa kombinację [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

#### <a name="acceptance-tests"></a>Testy akceptacji

Testy akceptacji testu systemu, aby upewnić się, że działa zgodnie z oczekiwaniami.
Na przykład testy, aby upewnić się, że właściwe informacje, gdy kwerenda zwraca stronę sieci web.
Te testy uruchomić zdalnie w węźle docelowym w celu przetestowania rzeczywistych scenariuszach.
Skrypt testu integracji używa kombinację [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

## <a name="define-the-build"></a>Zdefiniuj kompilacji

Firma Microsoft przekazanego naszego kodu do TFS i przeglądał tak jest, zdefiniujmy naszych kompilacji.

W tym miejscu omówione zostaną następujące czynności kroków kompilacji, które dodasz do kompilacji. Aby uzyskać instrukcje dotyczące sposobu tworzenia definicji kompilacji w programie TFS, zobacz [tworzenie i kolejki definicję kompilacji](https://www.visualstudio.com/en-us/docs/build/define/create).

Utwórz nową definicję kompilacji (wybierz **pusty** szablonu) o nazwie "InfraDNS".
Dodaj następujące kroki, aby użytkownik definicji kompilacji:

- Skrypt programu PowerShell
- Publikowanie wyników testu
- Skopiuj pliki
- Publikowanie artefaktów

Po dodaniu te kroki procesu kompilacji, Edytuj właściwości każdego kroku w następujący sposób:

### <a name="powershell-script"></a>Skrypt programu PowerShell

1. Ustaw **typu** właściwości `File Path`.
1. Ustaw **ścieżka skryptu** właściwości `initiate.ps1`.
1. Dodaj `-fileName build` do **argumenty** właściwości.

Ten krok kompilacji działa `initiate.ps1` pliku, który wywołuje psake skryptu kompilacji.

### <a name="publish-test-results"></a>Publikowanie wyników testu

1. Ustaw **Format wyniku testu** do `NUnit`
1. Ustaw **plików z wynikami testów** do `InfraDNS/Tests/Results/*.xml`
1. Ustaw **tytułu uruchomienia testu** do `Unit`.
1. Upewnij się, że **opcje sterowania** **włączone** i **są zawsze uruchamiane** są wybrane.

Ten krok kompilacji uruchamia testy jednostkowe w skrypcie Pester analizujemy wcześniej i przechowuje wyniki w `InfraDNS/Tests/Results/*.xml` folderu.

### <a name="copy-files"></a>Skopiuj pliki

1. Każdy z poniższych wierszy, aby dodać **zawartość**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Ustaw **TargetFolder** do `$(Build.ArtifactStagingDirectory)\`

Ten krok umożliwia skopiowanie kompilacji i test skryptów w katalogu przemieszczania więc zostać opublikowane zgodnie z kompilacji artefakty przez następnego kroku.

### <a name="publish-artifact"></a>Publikowanie artefaktów

1. Ustaw **ścieżka do publikowania** do `$(Build.ArtifactStagingDirectory)\`
1. Ustaw **nazwa artefaktu** do `Deploy`
1. Ustaw **typu artefaktu** do `Server`
1. Wybierz `Enabled` w **opcje sterowania**

## <a name="enable-continuous-integration"></a>Włącz ciągłej integracji

Teraz wyzwalacz, który powoduje, że projekt do kompilacji w dowolnej chwili zaplanujemy zmiany jest zaewidencjonowany do `ci-cd-example` gałęzi repozytorium git.

1. W programie TFS, kliknij przycisk **kompilacji i wydania** kartę
1. Wybierz `DNS Infra` definicji kompilacji, a następnie kliknij przycisk **edycji**
1. Kliknij przycisk **wyzwalaczy** kartę
1. Wybierz **ciągłej integracji (CI)** i wybierz `refs/heads/ci-cd-example` na liście rozwijanej gałęzi
1. Kliknij przycisk **zapisać** , a następnie **OK**

Teraz wszelkie zmiany wyzwalaczy repozytorium git TFS automatyczne kompilacji.

## <a name="create-the-release-definition"></a>Utwórz definicję zlecenia

Teraz należy utworzyć definicji wersji, tak aby projektu została wdrożona do środowiska projektowego z każdym ewidencjonowania kodu.

Aby to zrobić, Dodaj nową definicję wersji skojarzony z `InfraDNS` wcześniej utworzonego definicji kompilacji.
Należy wybrać **ciągłe wdrażanie** tak, aby nowej wersji zostanie wywołane dowolnej chwili ukończenia nowej kompilacji.
([Porady: Praca z definicji wersji](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) i skonfigurować w następujący sposób:

Do definicji wersji, należy dodać następujące kroki:

- Skrypt programu PowerShell
- Publikowanie wyników testu
- Publikowanie wyników testu

Edytuj kroki w następujący sposób:

### <a name="powershell-script"></a>Skrypt programu PowerShell

1. Ustaw **ścieżka skryptu** do `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ustaw **argumenty** do `-fileName Deploy`

### <a name="first-publish-test-results"></a>Najpierw opublikować wyniki testu

1. Wybierz `NUnit` dla **Format wyniku testu** pola
1. Ustaw **plików wyników testu** do `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ustaw **tytułu uruchomienia testu** do `Integration`
1. W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**

### <a name="second-publish-test-results"></a>Drugi opublikować wyniki testu

1. Wybierz `NUnit` dla **Format wyniku testu** pola
1. Ustaw **plików wyników testu** do `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ustaw **tytułu uruchomienia testu** do `Acceptance`
1. W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**

## <a name="verify-your-results"></a>Sprawdź wyniki

Teraz, dowolnej chwili możesz wypchnąć zmiany `ci-cd-example` rozpocznie gałęzi do programu TFS, nowej kompilacji.
Jeśli kompilacja zakończy się pomyślnie, zostanie wywołany nowego wdrożenia.

Wynik wdrożenia można sprawdzić, otwierając przeglądarki na komputerze klienckim i przechodząc do `www.contoso.com`.

## <a name="next-steps"></a>Następne kroki

Ten przykład konfiguruje serwer DNS `TestAgent1` , aby adres URL `www.contoso.com` jest rozpoznawana jako `TestAgent2`, ale nie faktycznie wdrażać witryny sieci Web.
Szkielet dokonaniem znajduje się w repozytorium w obszarze `WebApp` folderu.
Zastępcze dostarczony do tworzenia skryptów psake, Pester testów i konfiguracji DSC umożliwia wdrażanie własnych witryny sieci Web.