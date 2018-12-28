---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Tworzenie potoku ciągłej integracji i ciągłego wdrażania za pomocą DSC
ms.openlocfilehash: c305d9bc7e0f8c659129b5a20d0b7e8b34d09ba8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405246"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Tworzenie potoku ciągłej integracji i ciągłego wdrażania za pomocą DSC

W tym przykładzie pokazano, jak utworzyć potok ciągłej integracji i ciągłego wdrażania (CI/CD) przy użyciu programu PowerShell, DSC, usług Pester i Visual Studio Team Foundation Server (TFS).

Po potoku jest utworzony i skonfigurowany, można użyć w pełni wdrażania, konfigurowania i testowania serwera DNS i skojarzonych rekordów hosta.
Ten proces symuluje pierwszą część z potoku, która będzie używana w środowisku programistycznym.

Swój zautomatyzowany potok CI/CD pomaga zaktualizować oprogramowanie szybciej i bardziej niezawodnie zagwarantowanie, że cały kod jest przetestowany i czy bieżąca kompilacja kodu jest dostępny przez cały czas.

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przykładu, należy zapoznać się z następujących czynności:

- Pojęcia dotyczące ciągłej integracji ciągłego wdrażania. Wartościowa dokumentacja ułatwiająca znajduje się w temacie [Model potoku wydania](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) kontroli źródła
- [Usług Pester](https://github.com/pester/Pester) struktury testowania
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Będą potrzebne

Aby skompilować i uruchomić ten przykład, konieczne będzie środowisko z kilku komputerów i/lub maszyn wirtualnych.

### <a name="client"></a>Client

Jest to komputer, na którym odbywa się na wszystkie zadania konfigurowania i uruchamiania przykładu.

Komputer kliencki musi być komputerem Windows za pomocą zainstalowane następujące oprogramowanie:

- [usługi git](https://git-scm.com/)
- sklonowany z repozytorium lokalnego narzędzia git https://github.com/PowerShell/Demo_CI
- Edytor tekstu, takie jak [programu Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Komputer, który jest hostem serwera TFS, w którym będzie definicji kompilacji i wydania.
Ten komputer musi mieć [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) zainstalowane.

### <a name="buildagent"></a>BuildAgent

Komputer z systemem Windows agenta kompilacji, który tworzy projekt.
Ten komputer musi mieć Windows, zainstaluj i uruchom agenta kompilacji.
Zobacz [wdrażanie agenta w Windows](/azure/devops/pipelines/agents/v2-windows) dla agenta kompilacji, instrukcje dotyczące sposobu instalowania i uruchamiania Windows.

Należy również zainstalować zarówno `xDnsServer` i `xNetworking` modułów DSC na tym komputerze.

### <a name="testagent1"></a>TestAgent1

Jest to komputer, który jest skonfigurowany jako serwer DNS za pomocą konfiguracji DSC, w tym przykładzie.
Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Jest to komputer, który jest hostem witryny sieci Web, który określa, w tym przykładzie.
Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Dodaj kod programem TFS

Rozpoczniemy tworzenia repozytorium Git w programie TFS, a następnie importując kod ze swojego lokalnego repozytorium na komputerze klienckim.
Jeśli nie zostały jeszcze sklonowane repozytorium Demo_CI na swoim komputerze klienckim, wykonaj teraz przez uruchomienie następującego polecenia git:

`git clone https://github.com/PowerShell/Demo_CI`

1. Na komputerze klienckim przejdź do serwera TFS w przeglądarce sieci web.
1. W programie TFS [Tworzenie nowego projektu zespołowego](/azure/devops/organizations/projects/create-project) o nazwie Demo_CI.

   Upewnij się, że **kontroli wersji** ustawiono **Git**.
1. Na komputerze klienckim należy dodać element zdalny do repozytorium, który został utworzony w programie TFS za pomocą następującego polecenia:

   `git remote add tfs <YourTFSRepoURL>`

   Gdzie `<YourTFSRepoURL>` jest adres URL klonowania repozytorium TFS został utworzony w poprzednim kroku.

   Jeśli nie wiesz, gdzie można znaleźć ten adres URL, zobacz [sklonować istniejące repozytorium Git](/azure/devops/repos/git/clone).
1. Polecenia push Przenieś kod ze swojego lokalnego repozytorium do repozytorium programu TFS za pomocą następującego polecenia:

   `git push tfs --all`
1. Repozytorium TFS zostanie wypełniona przy użyciu kodu Demo_CI.

> [!NOTE]
> W tym przykładzie użyto kod w `ci-cd-example` gałęzi repozytorium Git.
> Pamiętaj określić tę gałąź jako domyślną gałąź w projekcie programu TFS, a dla wyzwalaczy CI/CD można utworzyć.

## <a name="understanding-the-code"></a>Znajomość kodu

Przed utworzeniem potoki kompilacji i wdrażania, Przyjrzyjmy się część kodu, aby zrozumieć, co się dzieje.
Na komputerze klienckim otwórz swoim ulubionym edytorze tekstów, a następnie przejdź do katalogu głównego repozytorium Demo_CI Git.

### <a name="the-dsc-configuration"></a>Konfiguracja DSC

Otwórz plik `DNSServer.ps1` (z katalogu głównego lokalnego repozytorium Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).

Ten plik zawiera konfigurację DSC, który konfiguruje serwer DNS. W tym miejscu jest w całości:

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

Zwróć uwagę `Node` instrukcji:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

To znajdzie wszystkie węzły, które zostały zdefiniowane jako mające rolę `DNSServer` w [dane konfiguracyjne](../configurations/configData.md), który jest tworzony przez `DevEnv.ps1` skryptu.

Przeczytaj więcej o `Where` method in Class metoda [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Ważne jest korzystanie z danych konfiguracji do definiowania węzły, podczas wykonywania ciągłej integracji, ponieważ informacje o węźle najprawdopodobniej ulegną zmianom między środowiskami i korzystanie z danych konfiguracji pozwala łatwo dokonać zmian bez konieczności zmieniania kodu konfiguracji informacje o węźle.

W pierwszym bloku zasobów, konfiguracji wywołuje **WindowsFeature** aby upewnić się, że włączona jest funkcja DNS.
Bloków zasobów, które należy wykonać wywołanie zasobów z [xDnsServer](https://github.com/PowerShell/xDnsServer) modułu do skonfigurowania podstawowej strefy i rekordy DNS.

Należy zauważyć, że dwa `xDnsRecord` bloki są opakowane w `foreach` pętli, które przechodzą przez tablice w danych konfiguracji.
Ponownie, dane konfiguracji są tworzone przez `DevEnv.ps1` skryptu, który kolejności przyjrzymy się dalej.

### <a name="configuration-data"></a>Dane konfiguracji

`DevEnv.ps1` Pliku (z katalogu głównego lokalnego repozytorium Demo_CI `./InfraDNS/DevEnv.ps1`) określa danych konfiguracyjnych środowisku w tablicy skrótów, a następnie przekazuje tej tablicy skrótów do wywołania `New-DscConfigurationDataDocument` funkcji, która jest zdefiniowana w `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

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

`New-DscConfigurationDataDocument` — Funkcja (zdefiniowane w `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programowo tworzy dokument danych konfiguracji na podstawie hashtable (dane węzła) i tablicy (węzeł-danych), które są przekazywane jako `RawEnvData` i `OtherEnvData` parametrów.

W naszym przypadku tylko `RawEnvData` parametr jest używany.

### <a name="the-psake-build-script"></a>Skrypt kompilacji psake

[Psake](https://github.com/psake/psake) zdefiniowane w skrypcie kompilacji `Build.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Build.ps1`) definiuje zadań, które są częścią kompilacji.
Definiuje również inne zadania, które zależy od każdego zadania.
Po wywołaniu skryptu psake zapewnia, że określonego zadania (lub zadania o nazwie `Default` Jeśli nie określono) działa i że wszystkie zależności również uruchomić (jest cykliczna, tak, aby uruchomić zależności zależności, i tak dalej).

W tym przykładzie `Default` zadania jest zdefiniowany jako:

```powershell
Task Default -depends UnitTests
```

`Default` Zadanie nie ma implementacji sam, ale ma zależność od `CompileConfigs` zadania.
Wynikowy łańcuch zależności zadań podrzędnych gwarantuje, czy działają wszystkie zadania w skrypcie kompilacji.

W tym przykładzie skrypt psake zostanie wywołana przez wywołanie `Invoke-PSake` w `Initiate.ps1` plik (znajdujący się w katalogu głównym repozytorium Demo_CI):

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

Podczas tworzenia definicji kompilacji w tym przykładzie w programie TFS, firma Microsoft będzie dostarczać naszym pliku skryptu psake jako `fileName` parametr tego skryptu.

Skrypt kompilacji definiuje następujące zadania:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Przebiegi `DevEnv.ps1`, która generuje plik danych konfiguracji.

#### <a name="installmodules"></a>InstallModules

Instaluje moduły wymagane przez tę konfigurację `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Wywołania [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów jednostkowych.

#### <a name="compileconfigs"></a>CompileConfigs

Kompiluje konfigurację (`DNSServer.ps1`) do pliku MOF przy użyciu danych konfiguracji, generowane przez `GenerateEnvironmentFiles` zadania.

#### <a name="clean"></a>Czyszczenie

Tworzy foldery używane dla przykładu, a następnie usuwa wszystkie wyniki testów, pliki danych konfiguracji i modułów z poprzednich przebiegów.

### <a name="the-psake-deploy-script"></a>Psake wdrożenia skryptu

[Psake](https://github.com/psake/psake) skrypt wdrożenia zdefiniowany w `Deploy.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Deploy.ps1`) definiuje zadania, które są wdrażanie i uruchamianie konfiguracji.

`Deploy.ps1` definiuje następujące zadania:

#### <a name="deploymodules"></a>DeployModules

Uruchamia sesję programu PowerShell na `TestAgent1` i instaluje moduły zawierające zasoby DSC, wymagane do konfiguracji.

#### <a name="deployconfigs"></a>DeployConfigs

Wywołania [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet, aby uruchomić konfigurację na `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów integracji.

#### <a name="acceptancetests"></a>AcceptanceTests

Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów akceptacyjnych.

#### <a name="clean"></a>Czyszczenie

Usuwa wszystkie moduły zainstalowane w poprzednich przebiegów i gwarantuje, że istnieje folder wynik testu.

### <a name="test-scripts"></a>Testowanie skryptów

Akceptacji, integracja i testy jednostkowe są zdefiniowane w skryptach w `Tests` folderu (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Tests`), każde WE plików o nazwie `DNSServer.tests.ps1` w ich odpowiednich folderów.

Test skrypty użyj [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

#### <a name="unit-tests"></a>Testy jednostkowe

Konfiguracje testowe DSC, samodzielnie, aby upewnić się, konfiguracje będzie wykonywał, czego oczekuje się, gdy uruchamiają oni testy jednostek.
Skrypt używa testów jednostkowych [usług Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Testy integracji

Testy integracji testu konfiguracji systemu, aby upewnić się, że gdy zintegrowana z innymi składnikami, system jest skonfigurowany zgodnie z oczekiwaniami. Te testy w docelowym węźle po został skonfigurowany za pomocą DSC.
Skrypt testu integracji używa kombinacji [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

#### <a name="acceptance-tests"></a>Testy odbiorcze

Testy odbiorcze przetestowanie systemu, aby upewnić się, że działa zgodnie z oczekiwaniami.
Na przykład sprawdza, aby upewnić się, że strony sieci web zwraca potrzebnych informacji po otrzymaniu kwerendy.
Te testy zdalnie korzystać z węzła docelowego w celu przetestowania scenariusze ze świata rzeczywistego.
Skrypt testu integracji używa kombinacji [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.

## <a name="define-the-build"></a>Definiowanie kompilacji

Teraz, gdy firma Microsoft przekazaniu nasz kod programem TFS i przyjrzano się, jak działa czynnością jest zdefiniowanie naszych kompilacji.

W tym miejscu omówimy kroki kompilacji, które należy dodać do kompilacji. Aby uzyskać instrukcje dotyczące sposobu tworzenia definicji kompilacji w programie TFS, zobacz [Utwórz i kolejki definicję kompilacji](/azure/devops/pipelines/get-started-designer).

Utwórz nową definicję kompilacji (wybierz **pusty** szablonu) o nazwie "InfraDNS".
Dodaj poniższe kroki, aby użytkownik definicja kompilacji:

- Skrypt programu PowerShell
- Publikuj wyniki testu
- Kopiowanie plików
- Publikowanie artefaktów

Po dodaniu tych kroków kompilacji, Edytuj właściwości każdego kroku w następujący sposób:

### <a name="powershell-script"></a>Skrypt programu PowerShell

1. Ustaw **typu** właściwość `File Path`.
1. Ustaw **ścieżka skryptu** właściwość `initiate.ps1`.
1. Dodaj `-fileName build` do **argumenty** właściwości.

Ten krok kompilacji działa `initiate.ps1` pliku, który wywołuje skrypt kompilacji psake.

### <a name="publish-test-results"></a>Publikuj wyniki testu

1. Ustaw **Format wyniku testu** do `NUnit`
1. Ustaw **plików z wynikami testów** do `InfraDNS/Tests/Results/*.xml`
1. Ustaw **tytuł przebiegu testu** do `Unit`.
1. Upewnij się, że **opcje sterowania** **włączone** i **są zawsze uruchamiane** są zaznaczone.

Ten krok kompilacji, uruchamia testy jednostkowe w skrypcie usług Pester przyjrzeliśmy się wcześniej i zapisuje wyniki w `InfraDNS/Tests/Results/*.xml` folderu.

### <a name="copy-files"></a>Kopiowanie plików

1. Dodaj wszystkie następujące wiersze do **zawartość**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Ustaw **TargetFolder** do `$(Build.ArtifactStagingDirectory)\`

W tym kroku kopiuje kompilacji i test skrypty w katalogu przemieszczania tak, mogą być publikowane jako artefaktów kompilacji w następnym kroku.

### <a name="publish-artifact"></a>Publikowanie artefaktów

1. Ustaw **ścieżka do publikowania** do `$(Build.ArtifactStagingDirectory)\`
1. Ustaw **nazwa artefaktu** do `Deploy`
1. Ustaw **typ artefaktu** do `Server`
1. Wybierz `Enabled` w **opcje kontroli**

## <a name="enable-continuous-integration"></a>Włącz ciągłą integrację

Teraz możemy skonfigurować wyzwalacz, który powoduje, że projekt do tworzenia w dowolnym momencie celu ewidencjonowana jest zmiana `ci-cd-example` gałęzi repozytorium git.

1. W programie TFS, kliknij przycisk **kompilowanie i wydawanie** kartę
1. Wybierz `DNS Infra` definicji kompilacji, a następnie kliknij przycisk **edycji**
1. Kliknij przycisk **wyzwalaczy** kartę
1. Wybierz **ciągłej integracji (CI)** i wybierz `refs/heads/ci-cd-example` na liście rozwijanej gałęzi
1. Kliknij przycisk **Zapisz** i następnie **OK**

Obecnie każda zmiana wyzwalacze repozytorium usługi git w programie TFS zautomatyzowanej kompilacji.

## <a name="create-the-release-definition"></a>Tworzenie definicji wydania

Utwórzmy definicji wydania, tak aby projekt został wdrożony do środowiska deweloperskiego przy każdym zaewidencjonowaniu kodu.

Aby to zrobić, Dodaj nowe definicja wydania skojarzona z `InfraDNS` wcześniej utworzoną definicję kompilacji.
Pamiętaj o wybraniu **ciągłe wdrażanie** tak, aby nowe wydanie zostaną wyzwolone za każdym zakończeniu nowej kompilacji.
([Jak: Praca z definicji wersji](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) i skonfiguruj ją w następujący sposób:

Z definicją wydania, należy dodać następujące kroki:

- Skrypt programu PowerShell
- Publikuj wyniki testu
- Publikuj wyniki testu

Edytuj następujące kroki:

### <a name="powershell-script"></a>Skrypt programu PowerShell

1. Ustaw **ścieżka skryptu** pole `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ustaw **argumenty** pole `-fileName Deploy`

### <a name="first-publish-test-results"></a>Najpierw opublikować wyniki testu

1. Wybierz `NUnit` dla **Format wyniku testu** pola
1. Ustaw **pliki wyników testu** pole `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ustaw **tytuł przebiegu testu** do `Integration`
1. W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**

### <a name="second-publish-test-results"></a>Po drugie opublikować wyniki testu

1. Wybierz `NUnit` dla **Format wyniku testu** pola
1. Ustaw **pliki wyników testu** pole `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ustaw **tytuł przebiegu testu** do `Acceptance`
1. W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**

## <a name="verify-your-results"></a>Sprawdź wyniki

Teraz, ilekroć możesz wypychać zmiany `ci-cd-example` gałąź do TFS, nowa kompilacja zostanie uruchomiona.
Jeśli kompilacja zakończy się pomyślnie, zostanie wywołany nowego wdrożenia.

Wynik wdrożenia można sprawdzić, otwierając przeglądarki na komputerze klienckim i przechodząc do `www.contoso.com`.

## <a name="next-steps"></a>Następne kroki

Ten przykład umożliwia skonfigurowanie serwera DNS `TestAgent1` tak, aby adres URL `www.contoso.com` jest rozpoznawana jako `TestAgent2`, ale nie wdrażają faktycznie witryny sieci Web.
Szkielet, aby to zrobić, znajduje się w repozytorium, w obszarze `WebApp` folderu.
Wycinki kodu, aby utworzyć skrypty psake, testy usług Pester i konfiguracje DSC umożliwia wdrażanie własnych witryny sieci Web.
