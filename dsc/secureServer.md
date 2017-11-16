---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Ściąganie server najlepsze rozwiązania"
ms.openlocfilehash: 66b97f4edb43926866b39731d720a2dc8c91eb2e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="pull-server-best-practices"></a>Ściąganie server najlepsze rozwiązania

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Podsumowanie: Ten dokument jest przeznaczony do uwzględnienia procesu i rozszerzalność ułatwiających engineers, którzy są przygotowywanie do rozwiązania. Szczegóły powinny udostępnienie najlepszych rozwiązań, określonych przez klientów i następnie zweryfikowany przez zespół pracujący nad produktem zalecenia są skierowane do przyszłych i uznawane za stabilną.

| |Informacje o dokumencie|
|:---|:---|
Autor | Jan Greene  
Recenzenci | Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic  
Opublikowane | Kwietnia 2015 r.

## <a name="abstract"></a>Abstrakcyjny

Celem niniejszego dokumentu jest oficjalnego wytyczne dla każdego Planowanie wdrożenia serwera ściągania konfiguracji żądanego stanu programu Windows PowerShell. Serwerem ściągania jest proste usługi, które powinien wykonać tylko minut do wdrożenia. Mimo że ten dokument zostanie oferują techniczne porad wskazówki, które mogą być używane w ramach wdrożenia, wartość tego dokumentu jest jako punkt odniesienia dla najlepszych rozwiązań i co można traktować przed wdrożeniem.
Czytniki powinny mieć podstawowe znajomość DSC i terminów używanych do opisywania składników, które są zawarte w wdrożenia usługi Konfiguracja DSC. Aby uzyskać więcej informacji, zobacz [żądany stan konfiguracji Omówienie środowiska Windows PowerShell](https://technet.microsoft.com/en-us/library/dn249912.aspx) tematu.
Oczekiwaniami DSC podlegać ewolucji w chmurze okresach podstawową technologią, łącznie z serwera ściągania również oczekuje rozwijać i wprowadzenie nowych funkcji. Ten dokument zawiera tabelę wersji w dodatku, który zawiera odwołania do poprzednich wersji i odwołania do przyszłych wyglądającej rozwiązania zachęca nowoczesne projektów.

Dwóch głównych sekcji tego dokumentu:

 - Planowanie konfiguracji
 - Przewodnik instalacji
 
### <a name="versions-of-the-windows-management-framework"></a>Wersje systemu Windows Management Framework 
Informacje w tym dokumencie mają na celu dotyczą Windows Management Framework 5.0. WMF 5.0 nie jest wymagany do wdrażania i obsługi serwera ściągania, w wersji 5.0 jest celem tego dokumentu.

### <a name="windows-powershell-desired-state-configuration"></a>Środowisko Windows PowerShell Konfiguracja żądanego stanu
Żądana Konfiguracja stanu (DSC) to platforma zarządzania, która umożliwia wdrażanie i zarządzanie nimi danych konfiguracji przy użyciu składni branży o nazwie Managed Object Format (MOF) do opisywania modelu informacji wspólnych (CIM). Istnieje projekt typu open source, Open Management Infrastructure (OMI), do dalszego programowanie z tymi standardami różnych platform, łącznie z systemem Linux i sieciowe systemy operacyjne sprzętu. Aby uzyskać więcej informacji, zobacz [strony DMTF łączenia ze specyfikacjami MOF](http://dmtf.org/standards/cim), i [OMI dokumentów i źródła](https://collaboration.opengroup.org/omi/documents.php).

Programu Windows PowerShell udostępnia zestaw rozszerzeń języka żądany stan konfiguracji, który służy do tworzenia i zarządzania nimi deklaratywne konfiguracjach.

### <a name="pull-server-role"></a>Rola serwera ściągania  
Serwer ściągania zapewnia scentralizowane usługi do przechowywania konfiguracji, które będą dostępne dla węzły docelowe.
 
Rola serwera ściągania może być wdrożony jako wystąpienie serwera sieci Web lub udziału plików SMB. Funkcja serwer sieci web zawiera interfejs OData i opcjonalnie możliwości węzły docelowe wysyłać raporty potwierdzenie powodzenie lub niepowodzenie zgodnie z konfiguracji są stosowane. Ta funkcja jest przydatna w środowiskach, w których istnieje wiele węzłów docelowych. Po skonfigurowaniu węzła docelowego (zwaną także klienta), aby wskazywały serwer ściągnięcia z najnowszą konfiguracją danych i wszystkie wymagane skrypty, zostały pobrane i zastosowane. Może to nastąpić jako jednorazowego wdrażania lub ponownie występującą zadania, które powoduje z serwerem ściągania istotny element zarządzania zmiany na dużą skalę. Aby uzyskać więcej informacji, zobacz [Windows PowerShell żądanego stanu ściągnięcia serwery konfiguracji](https://technet.microsoft.com/en-us/library/dn249913.aspx) i [wypychania i ściągania trybów konfiguracji](https://technet.microsoft.com/en-us/library/dn249913.aspx).

## <a name="configuration-planning"></a>Planowanie konfiguracji

Wszystkie wdrożenia oprogramowania przedsiębiorstwa jest informacje, które mogą być zbierane z wyprzedzeniem pomóc w planowaniu architektury i przygotowywane dla czynności wymagane do ukończenia wdrożenia. Poniższe sekcje zawierają informacje dotyczące sposobu przygotowania i organizacyjne połączeń, które prawdopodobnie będą musieli się zdarzyć z wyprzedzeniem.

### <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Wdrożenie serwera ściągania wymaga funkcji DSC usługi systemu Windows Server. Ta funkcja została wprowadzona w systemie Windows Server 2012 i został zaktualizowany przy użyciu bieżących wersjach systemu Windows Management Framework (WMF).

### <a name="software-downloads"></a>Pobieranie oprogramowania

Oprócz instalowania najnowszej zawartości z usługi Windows Update, istnieją dwa pliki do pobrania, które są traktowane jako najlepsze rozwiązanie do wdrożenia serwera ściągania usługi Konfiguracja DSC: najnowszą wersję programu Windows Management Framework i moduł DSC w celu zautomatyzowania serwera ściągania inicjowania obsługi administracyjnej.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 zawiera funkcję o nazwie usługi Konfiguracja DSC. Funkcja usługi Konfiguracja DSC zapewnia funkcje serwera ściągania, w tym pliki binarne, które obsługują punktu końcowego OData. WMF znajduje się w systemie Windows Server i jest aktualizowane na elastyczne okresach między wersjami systemu Windows Server. [Nowe wersje WMF 5.0](http://aka.ms/wmf5latest) mogą obejmować aktualizacje do funkcji usługi Konfiguracja DSC. Z tego powodu najlepszym rozwiązaniem jest Pobierz najnowszą wersję platformy WMF oraz do kontroli wersji, aby określić, czy wersja zawiera aktualizację do funkcji usługi Konfiguracja DSC. Należy także przejrzeć sekcję w informacjach o wersji wskazuje, czy stan projektowania dla aktualizacji lub scenariusza jest wymienione jako trwała lub eksperymentalne. Aby umożliwić cyklu zlecenia zwinnego poszczególne funkcje mogą być deklarowane stabilny, co oznacza funkcję jest gotowa do użycia w środowisku produkcyjnym, nawet wtedy, gdy WMF wprowadzone w wersji zapoznawczej.
Inne funkcje, które wcześniej zostały zaktualizowane przez wersje WMF (zobacz dalsze szczegółowe informacje o wersji platformy WMF):

 - Windows PowerShell, Windows PowerShell zintegrowane skryptów
 - (Zarządzanie OData usługi sieci Web (ISE) środowiska Windows PowerShell
 - Rozszerzenie usług IIS) systemu Windows PowerShell Konfiguracja żądanego stanu (DSC)
 - Windows Remote Management (WinRM) Instrumentacji zarządzania Windows (WMI)

### <a name="dsc-resource"></a>Zasób DSC

Wdrożenie serwera ściągania można uprościć przez usługi za pomocą skryptu konfiguracji DSC inicjowania obsługi administracyjnej. Ten dokument zawiera skrypty do konfiguracji, które mogą być używane do wdrażania węźle gotowy serwerów produkcyjnych. Aby użyć skryptów konfiguracyjnych, moduł DSC jest wymagane oznacza to nie jest uwzględniony w systemie Windows Server. Nazwa modułu wymagane jest **xPSDesiredStateConfiguration**, która obejmuje zasobów DSC **xDscWebService**. Moduł xPSDesiredStateConfiguration można pobrać [tutaj](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Użyj **instalacji modułu** polecenia cmdlet z **PowerShellGet** modułu.

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** moduł pobierze modułu do: 

`C:\Program Files\Windows PowerShell\Modules`

Planowanie zadań|
---|
Czy masz dostęp do plików instalacji systemu Windows Server 2012 R2?|
Środowisko wdrażania będą miały dostęp do Internetu, aby pobrać WMF i modułu z galerii online?|
Jak należy zainstalować najnowsze aktualizacje zabezpieczeń po zainstalowaniu systemu operacyjnego?|
Środowisko mają dostęp do Internetu w celu uzyskania aktualizacji lub ma lokalnego serwera Windows Server Update Services (WSUS)?|
Czy masz dostęp do plików instalacji systemu Windows Server, które już zawierają aktualizacje za pomocą iniekcji w trybie offline?|

### <a name="hardware-requirements"></a>Wymagania sprzętowe

Wdrożeń na serwerze ściągania są obsługiwane na serwerach fizycznych i wirtualnych. Dostosowanie rozmiaru wymagania dotyczące serwera ściągania wymagania dotyczące systemu Windows Server 2012 R2.

Procesor: 1,4 GHz 64-bitowy procesor  
Pamięci: 512 MB  
Miejsca na dysku: 32 GB  
Sieci: Kartę Ethernet Gigabit  

Planowanie zadań|
---|
Będzie można wdrożyć na sprzęcie fizycznym lub na platformie wirtualizacji?|
Co to jest proces, aby zażądać nowego serwera dla środowiska docelowego?|
Co to jest średnią łączny czas serwer stanie się dostępne?|
Jakie serwera rozmiar będzie żądać?|

### <a name="accounts"></a>Konta

Nie istnieją wymagania konta usługi do wdrożenia wystąpienie serwera ściągania. Istnieją jednak scenariuszy, w którym można uruchomić witryny sieci Web w kontekście konta użytkownika lokalnego. Na przykład jeśli istnieje potrzeba do dostępu do udziału magazynu dla zawartości witryny sieci Web i serwera systemu Windows lub urządzenia obsługującego udziału magazynu nie są przyłączone do domeny.

### <a name="dns-records"></a>Rekordy DNS

Konieczne będzie nazwę serwera do użycia podczas konfigurowania klientów do pracy z środowisku serwera ściągania. W środowisku testowym zazwyczaj jest używana nazwa hosta serwera lub adres IP serwera mogą być używane, gdy rozpoznawania nazw DNS jest niedostępna. W środowisku produkcyjnym lub w środowisku laboratoryjnym, który reprezentuje wdrożenia produkcyjnego najlepszym rozwiązaniem jest utworzenie rekordu CNAME systemu DNS.

Rekordu CNAME systemu DNS umożliwia tworzenie aliasów do odwoływania się do hosta () rekordu. Celem rekordu dodatkowe nazwy jest większą elastyczność zmiany należy wymagać w przyszłości. Rekord CNAME może pomóc izolowania konfiguracji klienta, tak aby zmian w środowisku serwera, takie jak zastępowania serwera ściągania lub dodawanie ściągania dodatkowych serwerów, nie będzie wymagać odpowiednie zmiany w konfiguracji klienta.

Przy wyborze nazwy rekordu DNS należy pamiętać o architektury rozwiązania. Jeśli przy użyciu równoważenia obciążenia, certyfikat używany do zabezpieczania ruchu za pośrednictwem protokołu HTTPS należy do tej samej nazwie jako rekord DNS. 

Scenariusz |Najlepsze praktyki
:---|:---
Środowisko testowe |Odtwórz środowisko produkcyjne, jeśli to możliwe. Nazwa hosta serwera jest odpowiednia dla prostego konfiguracje. Jeśli usługa DNS nie jest dostępna, można użyć adresu IP zamiast nazwy hosta.|
Wdrażanie jednego węzła |Tworzenie rekordu CNAME systemu DNS, który wskazuje nazwę hosta serwera.|

Aby uzyskać więcej informacji, zobacz [Konfigurowanie okrężnego DNS w systemie Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Planowanie zadań|
---|
Czy wiesz, który można skontaktować się z mają rekordy DNS tworzonych i zmienianych?|
Co to jest średnią przetwarzania żądania dotyczące rekordu DNS?|
Czy trzeba żądania rekordów statycznych nazwy hosta (A) dla serwerów?|
Co użytkownik zażąda jako rekord CNAME|
Jeśli to konieczne, jakiego typu rozwiązania do równoważenia obciążenia można korzystają? (patrz sekcja zatytułowany równoważenia obciążenia, aby uzyskać szczegółowe informacje)|

### <a name="public-key-infrastructure"></a>Infrastruktura kluczy publicznych

Większość organizacji dzisiaj wymagają czy ruch sieciowy, szczególnie w przypadku ruchu, który obejmuje takie dane poufne, jak serwery są skonfigurowane, musi być weryfikowane i/lub szyfrowane podczas przesyłania. Mimo że jest możliwa do wdrożenia serwera ściągania przy użyciu protokołu HTTP, która ułatwia żądań klientów w zwykły tekst, jest najlepszym rozwiązaniem jest bezpieczny ruch przy użyciu protokołu HTTPS. Usługę można skonfigurować do używania protokołu HTTPS przy użyciu zestawu parametrów w zasobie DSC **xPSDesiredStateConfiguration**.

Wymagania dotyczące certyfikatów w celu zabezpieczania ruchu HTTPS na serwerze ściągania nie są inne niż zabezpieczenia inne witryny sieci web HTTPS. **Serwera sieci Web** możliwości wymagane spełniający szablon usług certyfikatów serwera systemu Windows.

Planowanie zadań|
---|
Jeśli nie są automatycznego żądania certyfikatów, który trzeba będzie skontaktuj się z żądania certyfikatu?|
Co to jest średnią przetwarzania żądania?|
Jak zostanie plik certyfikatu przeniesiona do Ciebie?|
Jak będzie klucz prywatny certyfikatu przekazywanych do Ciebie?|
Jak długo trwa domyślny czas wygaśnięcia?|
Ma rozliczane na nazwę DNS w środowisku serwera ściągania, używanego programu nazwę certyfikatu?|

### <a name="choosing-an-architecture"></a>Wybieranie architektury

Serwer ściągania można wdrożyć przy użyciu jednej usługi sieci web na usług IIS lub udziału plików SMB. W większości przypadków opcji usługi sieci web zapewni większą elastyczność. Nie jest nietypowe dla ruchu HTTPS przechodzenia przez granice sieci, często filtrowane lub zablokowane między sieciami ruchu SMB. Usługa sieci web oferuje również możliwość dołączenia serwera zgodność lub sieci Web Reporting Manager (zarówno tematy mogą być adresowane w przyszłych wersjach tego dokumentu), które udostępniają mechanizm dla klientów w celu zgłoszenia stanu wstecz do serwera w celu scentralizowanego widoczności. Protokół SMB zapewnia opcję dla środowisk, w którym zasady wymuszają serwera sieci web nie powinien zostać użyte, a pozostałe wymagania środowiska, wchodzące w roli serwera sieci web niepożądane. W obu przypadkach należy pamiętać oszacować wymagania dotyczące podpisywania i szyfrowania ruchu sieciowego. HTTPS, podpisywania SMB i zasady IPSEC są wszystkie opcje warto uwzględnieniu.

#### <a name="load-balancing"></a>Równoważenie obciążenia  
Klienci interakcji z usługą sieci web należy żądanie informacji, która jest zwracana w jednej odpowiedzi. Żadne kolejne żądania są wymagane, więc nie jest niezbędna dla platformy, aby upewnić się, że sesje są zachowywane na jednym serwerze w dowolnym momencie w czasie równoważenia obciążenia.

Planowanie zadań|
---|
Jakie rozwiązanie będzie służyć do Równoważenie obciążenia ruchu w serwerów?|
Jeśli używasz sprzętowego równoważenia obciążenia, który zajmie żądanie, aby dodać nową konfigurację do urządzenia?|
Co to jest średnią przetwarzania dla żądania skonfigurować nowe obciążenia zrównoważonym usługi sieci web?|
Jakie informacje będą wymagane dla żądania?|
Trzeba będzie żądać dodatkowych adresów IP lub zespołu odpowiedzialnego za równoważenie obciążenia obsłuży który?|
Czy masz wymagane rekordy DNS i będzie to wymagane przez zespół odpowiedzialny za konfigurację rozwiązania do równoważenia obciążenia?|
Rozwiązanie równoważenia obciążenia wymaga obsługi infrastruktury kluczy publicznych przez urządzenie lub może on równoważyć obciążenie przez ruch protokołu HTTPS, dopóki nie ma żadnych wymagań sesji?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Konfiguracje przemieszczania i modułów na serwerze ściągania

W ramach planowania konfiguracji konieczne będzie traktować, o których DSC moduły i konfiguracje będzie obsługiwana przez z serwerem ściągania. Na potrzeby planowania konfiguracji, należy mieć podstawową wiedzę na temat sposobu przygotowania i wdrożenia zawartości na serwerze ściągania. 

W przyszłości w tej sekcji zostanie rozwinięty i zawarte w przewodniku obsługi dla serwera ściągania usługi Konfiguracja DSC.  Przewodnika przedstawimy codziennie proces zarządzania moduły i konfiguracje w czasie automatyzacji. 

#### <a name="dsc-modules"></a>Moduły DSC  
Żądania konfiguracji klientów należy wymagane moduły DSC. Funkcje serwera ściągania jest zautomatyzować dystrybucji na żądanie DSC modułów do klientów. Wdrażając serwera ściągania po raz pierwszy, prawdopodobnie jako laboratorium lub Weryfikacja koncepcji, prawdopodobnie zamierzasz są zależne od konfiguracji DSC modułów, które są dostępne z repozytoria publicznej, takich jak galerii programu PowerShell lub repozytoriów PowerShell.org GitHub dla modułów DSC .

Należy pamiętać, że nawet w przypadku zaufanej online źródeł, takich jak galerii programu PowerShell, każdy moduł, który jest pobierany z publicznej repozytorium należy ją sprawdzić przez innego środowiska PowerShell i wiedzy środowisko, w której będzie modułów używane przed ich użyciem w środowisku produkcyjnym. Podczas wykonywania tego zadania jest odpowiedni moment, aby sprawdzić wszelkie dodatkowe ładunku w module, który może być usunięty, takie jak dokumentacja i przykładowe skrypty. Zmniejsza to przepustowość sieci dla klienta w ich pierwsze żądanie po moduły będą pobierane przez sieć z serwera do klienta.

Każdy moduł muszą być spakowane w określonym formacie pliku ZIP o nazwie ModuleName_Version.zip, który zawiera ładunek modułu. Po skopiowaniu pliku na serwerze, należy utworzyć plik sumy kontrolnej. Jeżeli klienci łączą się z serwerem, suma kontrolna służy do Sprawdź, czy zawartość modułu DSC nie zmienił się od momentu jego opublikowania.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Planowanie zadań|
---|
Jeśli planujesz środowiska testu lub w laboratorium, jakie scenariusze są kluczem do sprawdzania poprawności?|
Czy istnieją publicznie dostępnych modułów, które zawierają zasoby, aby pokrywał się wszystko, czego potrzebujesz lub czy będzie potrzebna do tworzenia własnych zasobów?|
Środowisko będą miały dostęp do Internetu do pobierania modułów publicznych?|
Kto będzie odpowiedzialny za recenzowania modułów DSC?|
Jeśli planujesz środowiska produkcyjnego co będzie używana jako lokalnego repozytorium do przechowywania modułów DSC?|
Zespołu centralnego zaakceptuje DSC modułów zespoły aplikacji? Co to jest proces?|
Zostanie automatyzacji pakowania, kopiowanie i Tworzenie sumy kontrolnej dla modułów DSC gotowe do produkcji na serwer, z Twojego repozytorium źródła?|
Zespół będzie odpowiedzialny za zarządzanie z platformy automatyzacji?|

#### <a name="dsc-configurations"></a>Konfiguracji DSC

Cel serwera ściągania jest zapewnienie scentralizowane mechanizm dystrybuowania konfiguracji DSC dla węzłów klienta. Konfiguracje są przechowywane na serwerze jako dokumenty MOF. Każdy dokument będą miały nazwę nadaną przez unikatowy identyfikator GUID. Jeśli klientów skonfigurowano nawiązać połączenia z serwerem ściągania, otrzymuje także identyfikatora GUID dla konfiguracji, należy zażądać ich. Ten system odwołujące się do konfiguracji przez identyfikator GUID gwarantuje unikatowości globalne i jest elastyczny tak, aby konfiguracji mogą być stosowane z szczegółowości na węzeł lub Konfiguracja roli obejmującej wiele serwerów, które powinny mieć identyczne konfiguracje.

#### <a name="guids"></a>Identyfikatory GUID

Planowanie konfiguracji identyfikatorów GUID warto uwagi dodatkowe w przypadku poprzez wdrożenie serwera ściągania. Nie jest wymagane określonego sposobu obsługi identyfikatorów GUID i proces może być unikatowe dla każdego środowiska. Proces może należeć do zakresu od prostego do złożonych: centralnie przechowywany plik CSV, prosty tabeli SQL, CMDB lub złożonych rozwiązania wymagających integracji z innego narzędzia lub oprogramowania rozwiązania. Istnieją dwie metody ogólne:

 - **Przypisywanie identyfikatorów GUID na serwer** — zawiera miary gwarancji, że każdy serwer konfiguracji jest kontrolowany pojedynczo. Poziom dokładności wokół aktualizacji i nie może działać również w środowiskach z kilku serwerów.
 - **Przypisywanie identyfikatorów GUID dla każdej roli serwera** — wszystkie serwery, które wykonują tę samą funkcję, takich jak serwery sieci web, użyj tego samego identyfikatora GUID aby odwoływał się do danych konfiguracji.  Należy pamiętać, że jeśli wiele serwerów współużytkować ten sam identyfikator GUID, wszystkie z nich będzie można zaktualizować jednocześnie podczas zmiany konfiguracji.

Identyfikator GUID to element, którego należy traktować jako poufnych danych, ponieważ może być wykorzystywana przez osobę mającą złośliwymi działaniami w celu uzyskania informacji dotyczących sposobu wdrożone i skonfigurowane w środowisku serwerów. Aby uzyskać więcej informacji, zobacz [bezpiecznie alokacji identyfikatorów GUID w trybie programu PowerShell żądanego stanu konfiguracji ściągnięcia](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Planowanie zadań|
---|
Kto będzie odpowiedzialny za kopiowanie konfiguracji do folderu na serwerze ściągania, gdy są one gotowe?|
Konfiguracje są tworzone przez zespół aplikacji, co procesu należy przekazują je?|
Będzie można korzystać z repozytorium do przechowywania konfiguracji, jak długo muszą one być utworzone, zespołów?|
Będzie można zautomatyzować proces kopiowanie konfiguracji na serwerze i tworzenia sumy kontrolnej, gdy są one gotowe?|
Jak można przypisze identyfikatorów GUID do serwerów i ról i będzie to przechowywania?|
Jakie będzie używana jako proces konfigurowania komputerów klienckich i jak będą ją zintegrować z procesem tworzenia i przechowywania identyfikatorów GUID konfiguracji?|

## <a name="installation-guide"></a>Przewodnik instalacji

*Skrypty podanych w tym dokumencie przedstawiono stabilna. Zawsze skrypty należy dokładnie przejrzeć przed wykonaniem ich w środowisku produkcyjnym.*

### <a name="prerequisites"></a>Wymagania wstępne

Aby sprawdzić wersję programu PowerShell na serwerze, użyj następującego polecenia.

```powershell
$PSVersionTable.PSVersion
```

Jeśli to możliwe należy uaktualnić do najnowszej wersji Windows Management Framework.
Następnie należy pobrać `xPsDesiredStateConfiguration` modułu przy użyciu następującego polecenia.


```powershell
Install-Module xPSDesiredStateConfiguration
```

Polecenie poprosi użytkownika o zgodę przed pobraniem modułu.

### <a name="installation-and-configuration-scripts"></a>Instalacja i konfiguracja skryptów
-

Najlepszą metodą wdrażania serwera ściągania usługi Konfiguracja DSC jest użyć skryptu konfiguracji DSC. Ten dokument przedstawia skrypty w tym zarówno podstawowe ustawienia, które konfiguruje się tylko DSC usługi sieci web oraz zaawansowane ustawienia konfigurujące systemu Windows Server na trasie między innymi DSC usługi sieci web.

Uwaga: Obecnie `xPSDesiredStateConfiguation` modułu DSC wymaga serwer do ustawień regionalnych pl-pl.

### <a name="basic-configuration-for-windows-server-2012"></a>Podstawowa konfiguracja systemu Windows Server 2012
-------------------------------------------
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Konfiguracja zaawansowana dla systemu Windows Server 2012 R2

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
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN' 

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


## <a name="additional-references-snippets-and-examples"></a>Dodatkowe informacje, wstawki i przykłady

Ten przykład przedstawia sposób ręcznie zainicjować połączenie klienta (wymaga WMF5) do testowania. 

```powershell
Update-DSCConfiguration –Wait -Verbose
```

[DnsServerResourceRecordName Dodaj](http://bit.ly/1G1H31L) polecenie cmdlet umożliwia dodanie typu rekordu CNAME do strefy DNS. 

Funkcja programu PowerShell do [utworzyć sumy kontrolnej i opublikować MOF DSC serwerem ściągania SMB](http://bit.ly/1E46BhI) automatycznie generuje wymagane sumy kontrolnej, a następnie kopiuje pliki sumy kontrolnej i MOF konfiguracji na serwerze ściągania SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Dodatek — opis ODATA typów plików usługi danych

Plik danych są przechowywane do utworzenia informacji podczas wdrażania serwera ściągania, która obejmuje usługę sieci web OData. Typ pliku zależy od systemu operacyjnego, zgodnie z poniższym opisem.

 - **Windows Server 2012**  
Typ pliku będzie zawsze równa .mdb
 - **Windows Server 2012 R2**  
Typ pliku zostaną domyślnie .edb, chyba że .mdb jest określona w konfiguracji

W [zaawansowane przykładowy skrypt](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) instalacji serwera ściągania, będzie również znaleźć przykład automatycznie kontrolować ustawienia pliku web.config w celu zapobieżenia wszelkie ryzyko błąd spowodowany przez typ pliku.

