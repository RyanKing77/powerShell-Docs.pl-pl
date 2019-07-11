---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Najlepsze rozwiązania dotyczące serwera ściągania
ms.openlocfilehash: a3c4ca039b1e061a9246848bef6aeecebcd89011
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727193"
---
# <a name="pull-server-best-practices"></a>Najlepsze rozwiązania dotyczące serwera ściągania

Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](/powershell/dsc/pull-server/pullserver#community-solutions-for-pull-service).

Podsumowanie: Ten dokument jest przeznaczony do uwzględnienia procesów i rozszerzalność do pomocy inżynierów, którzy są przygotowywanie rozwiązania. Szczegółowe informacje, należy zapewnić najlepsze rozwiązania, jak identyfikowane przez klientów i zweryfikowany przez zespół pracujący nad produktem zalecenia są przyszłych umożliwiających dostęp i uznawana za stabilną.

| |Informacje o dokumencie|
|:---|:---|
Autor | Michael Greene
Recenzenci | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Opublikowane | Kwietnia 2015 r.

## <a name="abstract"></a>Abstrakcyjny

Ten dokument jest przeznaczony oficjalne wytyczne dla każdego, kto Planowanie wdrożenia serwera ściągania Desired State Configuration programu Windows PowerShell. Serwer ściągania jest prostą usługę, które powinny zająć tylko kilka minut wdrożyć. Mimo że ten dokument będzie oferować wskazówek porad technicznych, używanej we wdrożeniu, wartość w tym dokumencie jest jako odniesienie do najlepszych rozwiązań i co wziąć pod uwagę przed wdrożeniem.
Czytelnicy powinny mieć podstawowe znajomość DSC i terminy używane do opisywania składników, które są uwzględnione w wdrożenia DSC. Aby uzyskać więcej informacji, zobacz [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview) tematu.
Oczekiwaniami DSC podlegać ewolucji w erze chmury podstawowej technologii, w tym serwera ściągania również oczekuje się rozwijać i wprowadzają nowe funkcje. Ten dokument zawiera tabelę wersji w dodatku, który zawiera odwołania do poprzednich wersji i odwołań pozwalającą na przyszłe wyglądających rozwiązania do tworzenia, nowoczesne projekty.

Dwie główne części tego dokumentu:

- Planowanie konfiguracji
- Przewodnik instalacji

### <a name="versions-of-the-windows-management-framework"></a>Wersje Windows Management Framework

Informacje przedstawione w tym dokumencie jest przeznaczony do zastosowania do systemu Windows Management Framework 5.0. Program WMF 5.0 nie jest wymagany do wdrażania i obsługi serwera ściągania, wersja 5.0 jest celem tego dokumentu.

### <a name="windows-powershell-desired-state-configuration"></a>Program Windows PowerShell Desired State Configuration

Desired State Configuration (DSC) to platforma zarządzania, która umożliwia wdrażanie i zarządzanie nimi danych konfiguracji za pomocą składni branży o nazwie Managed Object Format (MOF) do opisywania modelu wspólnych informacji (CIM). Projekt open source, Open Management Infrastructure (OMI), istnieje w celu dalszego rozwoju norm między platformami, łącznie z systemem Linux i sieć sprzętu, systemów operacyjnych. Aby uzyskać więcej informacji, zobacz [DMTF strony łączenia z pliku MOF specyfikacje](https://www.dmtf.org/standards/cim), i [OMI dokumentów i źródła](https://collaboration.opengroup.org/omi/documents.php).

Program Windows PowerShell zawiera zbiór rozszerzenia językowe dla Desired State Configuration, który umożliwia tworzenie i zarządzanie konfiguracjami deklaratywne.

### <a name="pull-server-role"></a>Rola serwera ściągania

Serwerze ściągania zapewnia scentralizowane service do przechowywania konfiguracji, które będą dostępne dla węzłów docelowych.

Rola serwera ściągania może być wdrożony jako wystąpienia serwera sieci Web lub udziału plików SMB. Funkcja serwer sieci web obejmuje interfejsu OData i może opcjonalnie uwzględnić możliwości dla węzłów docelowych się wstecz potwierdzeniem powodzenia lub niepowodzenia na konfiguracje są stosowane. Ta funkcja jest przydatna w środowiskach, w przypadku dużej liczby węzłów docelowych.
Po skonfigurowaniu węzła docelowego (określane również jako klienta), aby wskazywały serwer ściągania z ostatnią konfiguracją danych i wszystkie wymagane skrypty są pobierane i stosowane. Może to nastąpić jako jednorazowego wdrażania lub ponownie występujące zadania, które sprawia, że serwera ściągania istotny element zarządzania zmiany na dużą skalę. Aby uzyskać więcej informacji, zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](/powershell/dsc/pullServer/pullserver) i

[Wypychanie i ściąganie trybów konfiguracji](/powershell/dsc/pullServer/pullserver).

## <a name="configuration-planning"></a>Planowanie konfiguracji

Dla każdego wdrożenia oprogramowania przedsiębiorstwa ma informacji, które mogą być zbierane z wyprzedzeniem ułatwiające Planowanie architektury i przygotować czynności wymagane do ukończenia wdrażania. Poniższe sekcje zawierają informacje dotyczące sposobu przygotowania i połączenia organizacji, które prawdopodobnie wystąpi konieczność się tak zdarzyć z wyprzedzeniem.

### <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Wdrożenie serwera ściągania wymaga funkcji DSC usługi systemu Windows Server. Ta funkcja została wprowadzona w systemie Windows Server 2012 i został zaktualizowany przy użyciu bieżących wersji Windows Management Framework (WMF).

### <a name="software-downloads"></a>Pobieranie oprogramowania

Oprócz instalowania najnowszej zawartości z usługi Windows Update, istnieją dwa pliki do pobrania, które są traktowane jako najlepsze rozwiązanie, aby wdrożyć serwer ściągania DSC: Najnowsza wersja programu Windows Management Framework i modułu DSC, aby zautomatyzować aprowizację serwera ściągania.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 zawiera funkcję o nazwie usługi DSC. Funkcja usługi DSC udostępnia funkcje serwera ściągania, w tym pliki binarne, które obsługują punkt końcowy OData.
WMF znajduje się w systemie Windows Server i jest aktualizowany w erze agile między wersjami systemu Windows Server. [Nowe wersje programu WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) mogą obejmować aktualizacje funkcji usługi DSC. Z tego powodu jest najlepszym rozwiązaniem jest, aby pobrać najnowszą wersję programu WMF i przejrzyj informacje o wersji, aby określić, jeśli ta wersja obejmuje aktualizację funkcji usługi DSC. Należy również sprawdzić sekcji informacje o wersji, wskazującą, czy stan projektu dla aktualizacji lub scenariusz jest wymieniony jako stałe lub eksperymentalne.
Umożliwia elastyczne cyklu, poszczególne funkcje mogą być deklarowane stabilny, co oznacza, funkcja jest gotowa do użycia w środowisku produkcyjnym, nawet wtedy, gdy program WMF została wydana w wersji zapoznawczej.
Inne funkcje, które wcześniej zostały zaktualizowane przez program WMF wersje (patrz dalsze szczegółowe informacje o wersji programu WMF):

- Windows PowerShell, Windows PowerShell Integrated Scripting
- (ISE) środowiska Windows PowerShell Web Services (Zarządzanie OData
- Rozszerzenie usług IIS) Windows PowerShell Desired State Configuration (DSC)
- Windows Remote Management (WinRM) Instrumentacji zarządzania Windows (WMI)

### <a name="dsc-resource"></a>Zasób DSC

Wdrożenie serwera ściągania można uprościć Inicjowanie obsługi usługi przy użyciu skryptu konfiguracji DSC. Ten dokument zawiera skrypty konfiguracji, których można użyć do wdrożenia węźle gotowe serwerów produkcyjnych. Aby użyć skryptów konfiguracyjnych, modułu DSC jest wymagana oznacza to nie jest uwzględniony w systemie Windows Server. Nazwa modułu wymagane jest **xPSDesiredStateConfiguration**, który zawiera zasób DSC **xDscWebService**. Można go pobrać moduł xPSDesiredStateConfiguration [tutaj](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Użyj `Install-Module` polecenia cmdlet z **PowerShellGet** modułu.

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** modułu pobierze modułu do:

`C:\Program Files\Windows PowerShell\Modules`

Planowanie zadań|
---|
Czy masz dostęp do plików instalacji systemu Windows Server 2012 R2?|
Środowisko wdrażania, będą miały dostęp do Internetu Pobierz program WMF oraz modułu z galerii online?|
Jak należy zainstalować najnowsze aktualizacje zabezpieczeń, po zainstalowaniu systemu operacyjnego?|
Środowiska mają dostęp do Internetu, aby uzyskać aktualizacje, czy mają lokalnego serwera Windows Server Update Services (WSUS)?|
Czy masz dostęp do plików instalacyjnych systemu Windows Server, które już zawierają aktualizacje za pomocą iniekcji w trybie offline?|

### <a name="hardware-requirements"></a>Wymagania sprzętowe

Wdrożenia serwera ściągania są obsługiwane na serwerach fizycznych i wirtualnych. Wymagania w zakresie rozmiaru na serwerze ściągania dostosowanie wymagania dotyczące systemu Windows Server 2012 R2.

CPU: 1.4 GHz 64-bitowy procesor pamięci: 512 MB miejsca na dysku: 32 GB Network: Dwie karty Ethernet

Planowanie zadań|
---|
Będzie można wdrożyć na sprzęcie fizycznym lub na platformie wirtualizacji?|
Co to jest proces, aby zażądać nowego serwera w środowisku docelowym?|
Co to jest średnia łączny czas serwera staną się dostępne?|
Jakiego rozmiaru serwera będzie żądać?|

### <a name="accounts"></a>Konta

Nie istnieją wymagania konta usługi do wdrożenia wystąpienia serwera ściągania.
Jednak istnieją scenariusze, w której witryny sieci Web może działać w kontekście konta użytkownika lokalnego.
Na przykład jeśli istnieje potrzeba dostępu udostępniania magazynu zawartości witryny sieci Web i systemu Windows Server lub urządzenie hostujące udział plików magazynu nie są przyłączone do domeny.

### <a name="dns-records"></a>Rekordy DNS

Konieczne będzie nazwę serwera do użycia podczas konfigurowania klientów do pracy ze środowiskiem serwera ściągania.
W środowiskach testowych zazwyczaj jest używana nazwa hosta serwera lub adres IP serwera umożliwia rozpoznawanie nazw DNS nie jest dostępna.
W środowisku produkcyjnym lub w środowisku laboratoryjnym, która reprezentuje wdrożenia produkcyjnego najlepszym rozwiązaniem jest tworzenie rekordu CNAME systemu DNS.

CNAME systemu DNS umożliwia tworzenie aliasów do odwoływania się do hosta () rekordu.
Celem rekordu dodatkowych nazw jest zwiększenie elastyczności zmiany należy wymagać w przyszłości.
Rekord CNAME ułatwiają izolowanie konfiguracji klienta, tak aby zmiany w środowisku serwera, takie jak zastąpienie serwera ściągania lub dodawanie ściągnięcia dodatkowych serwerów, nie będzie wymagać odpowiednie zmiany w konfiguracji klienta.

Wybierając nazwę rekordu DNS, należy wziąć pod uwagę architektury rozwiązania.
Jeśli przy użyciu równoważenia obciążenia, certyfikat używany do zabezpieczenia komunikacji za pośrednictwem protokołu HTTPS należy udostępnić taką samą nazwę jak rekord DNS.

Scenariusz |Najlepszym rozwiązaniem jest
:---|:---
Środowisko testowe |Odtwórz środowisko produkcyjne, jeśli jest to możliwe. Nazwa hosta serwera jest odpowiednia dla prostych konfiguracje. Jeśli serwer DNS nie jest dostępny, mogą służyć adresu IP zamiast nazwy hosta.|
Wdrożeniem pojedynczego węzła |Tworzenie rekordu CNAME systemu DNS, który wskazuje na nazwę hosta serwera.|

Aby uzyskać więcej informacji, zobacz [Konfigurowanie okrężnego DNS w systemie Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Planowanie zadań|
---|
Czy wiesz, kim się skontaktować, aby rekordy DNS tworzonych i zmienianych?|
Co to jest średnia przetwarzania żądania dotyczące rekordu DNS?|
Potrzebujesz żądania rekordów statycznych nazwy hosta (A) dla serwerów?|
Co użytkownik zażąda jako rekord CNAME|
Jeśli to konieczne, jakiego rodzaju rozwiązanie do równoważenia obciążenia będzie można wykorzystują? (zobacz sekcję pod tytułem równoważenia obciążenia, aby uzyskać szczegółowe informacje)|

### <a name="public-key-infrastructure"></a>Infrastruktura kluczy publicznych

Większość organizacji dzisiejsze wymagają, że ruchu w sieci, szczególnie w przypadku ruchu, który obejmuje takie dane poufne, jak serwery są skonfigurowane, musi zostać zweryfikowane i/lub szyfrowane podczas przesyłania.
Choć jest możliwe do wdrożenia serwera ściągania przy użyciu protokołu HTTP, która ułatwia żądań klientów w zwykły tekst, jest najlepszym rozwiązaniem, aby zabezpieczać ruch przy użyciu protokołu HTTPS. Usługę można skonfigurować do używania protokołu HTTPS przy użyciu zestawu parametrów w zasobie DSC **xPSDesiredStateConfiguration**.

Wymagania dotyczące certyfikatów do zabezpieczenia ruchu HTTPS na serwerze ściągania nie są inne niż zabezpieczenia inne witryny sieci web protokołu HTTPS. **Serwera sieci Web** szablon w usługach certyfikatów systemu Windows Server spełnia wymagane możliwości.

Planowanie zadań|
---|
Jeśli żądania certyfikatu nie jest zautomatyzowane, który będzie należy skontaktować się z żądania certyfikatu?|
Co to jest średnia przetwarzania żądania?|
Jak będzie plik certyfikatu przeniesienia do Ciebie?|
Jak będzie klucz prywatny certyfikatu przeniesienia do Ciebie?|
Jak długo trwa domyślny czas wygaśnięcia?|
Zostały uregulowane na nazwę DNS w środowisku serwera ściągania, używanego do nazwy certyfikatu?|

### <a name="choosing-an-architecture"></a>Wybieranie architekturę

Można wdrożyć serwera ściągania przy użyciu jednej usługi sieci web hostowanych w usługach IIS lub udziału plików SMB. W większości sytuacji opcja usługi sieci web oferuje większą elastyczność. Nie jest niczym niezwykłym ruch HTTPS na przechodzenie przez granice sieci, natomiast ruch SMB często jest filtrowana lub zablokowany między sieciami. Usługa sieci web oferuje również możliwość dołączenia serwera zgodności lub sieci Web raportowania Menedżera (zarówno tematy które zostaną rozwiązane w przyszłych wersjach tego dokumentu), zapewniają mechanizm dla klientów, aby zgłosić stan ponownie do serwera w celu centralnego wglądu.
Protokół SMB zapewnia opcję dla środowiska, w której zasady mówią, serwer sieci web nie powinny być wykorzystywane i inne wymagania środowiska, wchodzące w roli serwera sieci web niepożądane.
W obu przypadkach należy pamiętać ocenić wymagania dotyczące podpisywania i szyfrowania ruchu sieciowego. Protokół HTTPS, podpisywanie SMB i zasad protokołu IPSEC są wszystkie opcje warte biorąc pod uwagę.

#### <a name="load-balancing"></a>Równoważenie obciążenia

Klienci, interakcje z usługą sieci web zgłosić wniosek informacji, które są zwracane w pojedynczą odpowiedź. Żadne kolejne żądania nie są wymagane, więc nie jest konieczne dla platform, aby upewnić się, że sesje są zachowywane na jednym serwerze w dowolnym momencie w czasie równoważenia obciążenia.

Planowanie zadań|
---|
Jakich rozwiązań stosowanych w odniesieniu do Równoważenie obciążenia ruchu między serwerami?|
Jeśli używasz sprzętowego równoważenia obciążenia, który spowoduje przejście na żądanie, aby dodać nową konfigurację do urządzenia?|
Co to jest średnia przetwarzania żądania skonfigurować nowe obciążenia zrównoważone usługi sieci web?|
Jakie informacje będą wymagane dla żądania?|
Będzie trzeba zażądać dodatkowych adresów IP lub będą zespołu odpowiedzialnego za równoważenie obciążenia obsługiwały?|
Czy masz wymagane rekordy DNS i będzie to wymagane przez zespół odpowiedzialny za konfigurowanie rozwiązania do równoważenia obciążenia?|
To rozwiązanie do równoważenia obciążenia wymaga obsługiwania infrastruktury kluczy publicznych przez urządzenie lub można załadować saldo, które ruch protokołu HTTPS, tak długo, jak nie ma żadnych wymagań sesji?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Tymczasowe konfiguracji i modułów na serwerze ściągania

W ramach planowania konfiguracji należy traktować, o które DSC modułów i konfiguracji będzie obsługiwana przez serwera ściągania. Na potrzeby planowania konfiguracji należy mieć podstawową wiedzę na temat jak przygotować i wdrożyć zawartości na serwerze ściągania.

W przyszłości w tej sekcji zostaną rozwinięte i zawartych w przewodniku obsługi dla serwera ściągania DSC.  Przewodnika przedstawimy proces codziennie zarządzania modułów i konfiguracji wraz z upływem czasu za pomocą usługi automation.

#### <a name="dsc-modules"></a>Moduły DSC

Klientom żądającym konfiguracji należy wymagane moduły DSC. Funkcje serwera ściągania jest zautomatyzować dystrybucji na żądanie modułów DSC na klientach. Jeśli serwera ściągania są wdrażane po raz pierwszy, może być jako laboratorium lub weryfikacji koncepcji, prawdopodobnie będą zależeć od modułów DSC, które są dostępne z repozytoriów publicznych, takich jak Galeria programu PowerShell lub repozytoriów PowerShell.org GitHub dla modułów DSC .

Warto pamiętać, że nawet w przypadku zaufanej online źródeł, takich jak Galeria programu PowerShell, dowolny moduł, który jest pobierany z publicznego repozytorium powinny być zweryfikowane pod przez użytkownika za pomocą środowiska PowerShell i wiedzę na temat środowiska, w której będzie modułów używane przed ich użyciem w środowisku produkcyjnym. Podczas wykonywania tego zadania jest odpowiedni moment, aby sprawdzić wszelkie dodatkowe ładunku w module, który może zostać usunięty, takie jak dokumentacja i przykładowe skrypty. Zmniejszy to przepustowość sieci na kliencie w ich pierwsze żądanie, gdy moduły będą pobierane przez sieć z serwera do klienta.

Każdy moduł musi zostać spakowana w określonym formacie pliku ZIP o nazwie ModuleName_Version.zip, który zawiera ładunek modułu. Po plik jest kopiowany do serwera, należy utworzyć plik sumy kontrolnej. Gdy klienci łączą się z serwerem, sumę kontrolną służy do Sprawdź, czy zawartość modułu DSC nie zmienił się od momentu jego opublikowania.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Planowanie zadań|
---|
Jeśli jest planowane w środowisku testowym lub laboratorium scenariuszy, do których są kluczem do sprawdzania poprawności?|
Są publicznie dostępne moduły, które zawierają zasoby obejmują wszystkie elementy, których potrzebujesz, czy będziesz tworzyć własne zasoby?|
Środowiska mają dostęp do Internetu na pobranie publicznych modułów?|
Kto będzie odpowiedzialny za przegląd moduły DSC?|
Jeśli planowane jest do środowiska produkcyjnego co będzie używana jako repozytorium lokalne przechowywanie modułów DSC?|
Centralny zespół zaakceptuje modułów DSC od zespołów aplikacji? Jaka będzie procesu?|
Będzie automatyzować pakowania, kopiowanie i Tworzenie sumy kontrolnej dla modułów, gotowe do produkcji DSC na serwerze, z repozytorium źródła?|
Twój zespół będzie odpowiedzialny za zarządzanie także platforma automatyzacji?|

#### <a name="dsc-configurations"></a>Konfiguracje DSC

Przeznaczenie serwera ściągania jest zapewnienie mechanizm scentralizowanego dystrybuowania konfiguracji DSC do węzłów klienta. Konfiguracje są przechowywane na serwerze jako dokument MOF.
Każdy dokument będą miały nazwę nadaną przy użyciu unikatowego **Guid**. Gdy klienci są skonfigurowani do nawiązać połączenie z serwerem ściągania, otrzymuje także **Guid** konfiguracji należy żądają. Odwoływanie się do konfiguracji przez ten system **Guid** gwarantuje unikatowość globalnych i jest elastyczne w taki sposób, że można zastosować konfiguracji z dokładnością na węzeł lub jako konfiguracji roli, która obejmuje wiele serwerów, które powinny mieć identycznych konfiguracji.

#### <a name="guids"></a>Identyfikatory GUID

Planowanie konfiguracji **identyfikatorów GUID** warto wymagają dodatkowej uwagi, gdy obsługiwanego przez wdrożenie serwera ściągania. Nie ma określonego sposobu obsługi **identyfikatorów GUID** i proces może być unikatowy dla każdego środowiska. Ten proces może wynosić od prostych po złożone: centralnie przechowywane pliku CSV, prostą tabela SQL, CMDB lub złożone rozwiązania wymagające integracji z innego narzędzia lub oprogramowania rozwiązania. Dostępne są dwie opcje ogólne:

- **Przypisywanie identyfikatorów GUID na serwer** — jest miarą wiarygodności konfiguracji każdego serwera są sterowane indywidualnie. To zapewnia poziom dokładności wokół aktualizacji i może działać dobrze w środowiskach z kilku serwerów.
- **Przypisywanie identyfikatorów GUID dla roli serwera** — wszystkie serwery, które wykonują tę samą funkcję, takich jak serwery sieci web, użyj tego samego identyfikatora GUID odwołania do wybranych danych wymaganej konfiguracji.  Należy pamiętać, że jeśli wiele serwerów mają ten sam identyfikator GUID, wszystkie z nich zostałaby zaktualizowana jednocześnie po zmianie konfiguracji.

  Identyfikator GUID jest coś, co powinien być uważany za poufne dane ponieważ może być wykorzystywane przez osobę z wyrządzenia w celu uzyskania informacji na temat sposobu wdrażania i skonfigurowanych w środowisku serwerów. Aby uzyskać więcej informacji, zobacz [bezpiecznie alokacji identyfikatorów GUID w programie PowerShell Desired State Configuration ściągnięcia trybie](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Planowanie zadań|
---|
Kto będzie odpowiedzialny za kopiowanie do folderu na serwerze ściągania konfiguracji w, gdy są one gotowe?|
Konfiguracje są tworzone przez zespół aplikacji, co ten proces należy przekazują je?|
Będzie można wykorzystać repozytorium do przechowywania konfiguracji zgodnie z ich są są tworzone, w zespołach?|
Czy zautomatyzujesz proces kopiowania serwer konfiguracji i Tworzenie sumy kontrolnej, gdy są one gotowe?|
Jak będzie mapowania identyfikatorów GUID do serwerów lub ról i gdzie będą to przechowywane?|
Co użytkownik użyje jako proces konfigurowania komputerów klienckich i jak będzie ją zintegrować z procesem tworzenia i przechowywania identyfikatorów GUID konfiguracji?|

## <a name="installation-guide"></a>Przewodnik instalacji

*Skrypty podanych w tym dokumencie przedstawiono stabilne. Zawsze skryptów należy uważnie przeczytać przed wykonaniem ich w środowisku produkcyjnym.*

### <a name="prerequisites"></a>Wymagania wstępne

Aby sprawdzić, która wersja programu PowerShell na serwerze, użyj następującego polecenia.

```powershell
$PSVersionTable.PSVersion
```

Jeśli to możliwe Uaktualnij do najnowszej wersji programu Windows Management Framework.
Następnie należy pobrać `xPsDesiredStateConfiguration` modułu przy użyciu następującego polecenia.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Polecenie będzie monitować użytkownika o zgodę przed pobraniem modułu.

### <a name="installation-and-configuration-scripts"></a>Skrypty instalacji i konfiguracji

Najlepszą metodą wdrażania serwera ściągania DSC jest użyć skryptu konfiguracji DSC. W tym dokumencie spowoduje wyświetlenie skryptów, w tym zarówno podstawowe ustawienia, które będzie skonfigurować usługi sieci web DSC i zaawansowanych ustawień skonfigurowanych systemu Windows Server end-to-end tym DSC usługi sieci web.

Uwaga:  Obecnie `xPSDesiredStateConfiguration` DSC moduł wymaga serwera, aby był ustawień regionalnych EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Podstawowa konfiguracja systemu Windows Server 2012

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Zaawansowana konfiguracja dla systemu Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Sprawdź funkcje serwera ściągania

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Konfigurowanie klientów

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Dodatkowe informacje, fragmenty kodu i przykłady

Ten przykład pokazuje, jak ręcznie zainicjować połączenie klienta (wymaga WMF5) do testowania.

```powershell
Update-DscConfiguration –Wait -Verbose
```

[DnsServerResourceRecordName Dodaj](http://bit.ly/1G1H31L) polecenie cmdlet służy do dodawania typu rekordu CNAME do strefy DNS.

Funkcja programu PowerShell [utworzyć sumy kontrolnej i opublikować MOF DSC do serwera ściągania SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatycznie generuje wymagane sumy kontrolnej, a następnie kopiuje pliki sumy kontrolnej i pliku MOF konfiguracji serwera ściągania SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Dodatek — opis ODATA typy plików danych usługi

Plik danych są przechowywane do utworzenia informacji podczas wdrażania serwera ściągania, która obejmuje usługę sieci web OData. Typ pliku jest zależna od systemu operacyjnego, zgodnie z poniższym opisem.

- **Windows Server 2012** typ pliku będzie zawsze mdb
- **Windows Server 2012 R2** typ pliku będą domyślnie .edb, chyba że .mdb jest określona w konfiguracji

W [zaawansowane przykładowy skrypt](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) instalacji serwera ściągania, można również znaleźć przykład sposobu automatycznie kontrolować ustawienia pliku web.config w celu zapobieżenia każdej okazji błąd spowodowany przez typ pliku.
