---
title: Zatwierdzone czasowniki dla poleceń programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: d8a0561d6fbb4447a691c434e0518e3e16ce41e7
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56852178"
---
# <a name="approved-verbs-for-powershell-commands"></a>Zatwierdzone czasowniki dla poleceń programu PowerShell

Dla nazwy poleceń cmdlet i ich klasy pochodne programu Microsoft .NET Framework, programu PowerShell używa parę czasownik rzeczownik.
Na przykład `Get-Command` dostarczane przez program PowerShell polecenia cmdlet służy do pobierania wszystkich poleceń, które są zarejestrowane w programie PowerShell.
Czasownik część nazwy Określa akcję wykonywaną przez polecenie cmdlet.
Rzeczownik część nazwy identyfikuje jednostki wykonywania akcji.

> [!NOTE]
> PowerShell używany jest termin *zlecenie* do opisania programu word, który oznacza akcję, nawet jeśli słowo nie jest standardowy czasownika w języku angielskim.
> Na przykład określenie *New* jest prawidłową nazwą polecenie programu PowerShell, ponieważ oznacza akcję, mimo że nie ma czasownika w języku angielskim.

## <a name="verb-naming-rules"></a>Reguły nazewnictwa zlecenia

Poniższa lista zawiera wytyczne, które należy wziąć pod uwagę przy wyborze zlecenie dla nazwy polecenia cmdlet:

* Po określeniu zlecenie, firma Microsoft zaleca korzystanie z jednej nazwy wstępnie zdefiniowanych zlecenie dostarczane przez program PowerShell (aliasów dla tych wstępnie zdefiniowanych czasowników są zawarte w poniższych tabelach).
  Korzystając z wstępnie zdefiniowanych zlecenie, jest zapewnienie spójności między poleceń cmdlet, które tworzysz, poleceń cmdlet, które są dostarczane przez program PowerShell i poleceń cmdlet, które są przeznaczone dla innych osób.

* Można użyć wstępnie zdefiniowanych czasowników do opisania zakresu ogólne działania i uściślić działania polecenia cmdlet przy użyciu parametrów.

* Aby wymusić spójność w poleceniach cmdlet, nie należy używać synonimów zatwierdzonych żądań.

* Formularz tylko każdego zlecenia, który znajduje się w tym temacie.
  Na przykład użyć "Get", ale nie należy używać "Wprowadzenie" lub "Pobiera".

* Użyj Pascal wielkość liter dla zleceń.
  W Pascal wielkość liter początkowej litery każdego wyrazu jest pisany wielkimi literami, takie jak "ForEach".

* Nie używaj następujących zleceń zarezerwowanych ani aliasów.
  Te polecenia są używane za pomocą języka programu PowerShell lub przez specjalnych przypadków polecenia cmdlet dostarczane przez program PowerShell.
  - Instrukcja ForEach (foreach)
  - Format (f)
  - Grupy (gp)
  - Sortowanie (sr)
  - Program Tee (Usuń)
  - Gdzie (pytania "Wh")

## <a name="similar-verbs-for-different-actions"></a>Podobnych poleceń dla rozmaitych akcji

Następujące czasowniki podobne reprezentują różne akcje.

### <a name="new-vs-set"></a>Cena subskrypcji nowej Ustaw
`New` Zlecenia służy do tworzenia nowego zasobu.
`Set` Zlecenia służy do modyfikowania istniejącego zasobu, opcjonalnie tworzenia zasobu, jeśli nie istnieje, takich jak `Set-Variable` polecenia cmdlet.

### <a name="find-vs-search"></a>Znajdź programu vs. Wyszukiwanie
`Find` Zlecenia służy do wyszukiwania dla obiektu.
`Search` Zlecenie jest używany do tworzenia odwołanie do zasobu w kontenerze.

### <a name="get-vs-read"></a>Pobierz program vs. Odczyt
`Get` Zlecenia służy do pobierania zasobu, takiego jak plik.
`Read` Zlecenie jest używana do pobierania informacji ze źródła, takiego jak plik.

### <a name="invoke-vs-start"></a>Wywoływanie programu vs. Uruchom środowisko
`Invoke` Zlecenia służy do wykonywania operacji, która zwykle jest operacja synchroniczna, takie jak uruchomienie polecenia.
`Start` Zlecenia służy do rozpoczęcia operacji, która jest ogólnie operację asynchroniczną, takie jak uruchomienie procesu.

### <a name="ping-vs-test"></a>Polecenie ping programu vs. Test
Użyj `Test` zlecenie.

## <a name="common-verbs"></a>Typowe zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) wyliczenie klasy w celu zdefiniowania akcji ogólnych, które można zastosować do niemal każdego polecenia cmdlet.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Dodaj](/dotnet/api/System.Management.Automation.VerbsCommon.Add) ()|Dodaje zasób do kontenera lub dołącza element do innego elementu. Na przykład `Add-Content` polecenia cmdlet dodaje zawartość do pliku. To polecenie jest powiązany z `Remove`.|Dla tej akcji nie używać zleceń, takich jak dołączanie, dołączanie, Concatenate lub wstawić.|
|[Wyczyść](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Usuwa wszystkie zasoby z kontenera, ale nie powoduje usunięcia kontenera. Na przykład `Clear-Content` polecenie cmdlet usuwa zawartości pliku, ale nie powoduje usunięcia pliku.|Dla tej akcji nie należy używać czasowników, takich jak opróżniania, wymazywania, wersji, Usuń oznaczenie, Unset lub Nullify.|
|[Zamknij](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Zmienia stan zasobów, aby stał się niedostępny, niedostępne lub uniemożliwiającym jego używanie. To polecenie jest powiązany z `Open.`||
|[Kopiuj](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Kopiuje zasobu na inną nazwę lub w innym kontenerze. Na przykład `Copy-Item` polecenia cmdlet, które umożliwia dostęp do danych przechowywanych kopiuje element z jednej lokalizacji w magazynie danych do innej lokalizacji.|Dla tej akcji nie należy używać czasowników, takich jak duplikat, klonowania, replikowanie lub synchronizacja.|
|[Wprowadź](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (czas wschodni)|Określa akcję, która umożliwia użytkownikowi przenoszenie do zasobu. Na przykład `Enter-PSSession` polecenia cmdlet umieszcza użytkownika w interaktywnej sesji. To polecenie jest powiązany z `Exit`.|Dla tej akcji nie należy używać czasowników, takich jak wypychania lub do.|
|[Zakończ](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (np.)|Ustawia bieżącego środowiska lub kontekst do ostatnio używanych kontekstu. Na przykład `Exit-PSSession` polecenia cmdlet umieszcza użytkownika w sesji, który został użyty do uruchomienia sesji interakcyjnych. To polecenie jest powiązany z `Enter`.|Dla tej akcji nie należy używać czasowników, takich jak Pop lub na zewnątrz.|
|[Znajdź](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Sprawdza, czy obiekt w kontenerze, który jest nieznany, dorozumianych, opcjonalne lub został określony.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Rozmieszcza obiektów w podanym formularzu ani układu.||
|[Pobierz](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Określa akcję, która pobiera zasób. To polecenie jest powiązany z `Set`.|Dla tej akcji nie należy używać czasowników, takich jak Odczyt, Open, Cat, typu, Dir, Uzyskaj, zrzutu, nabywania, Zbadaj, Znajdź lub wyszukiwania dla tej akcji.|
|[Ukryj](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Sprawia, że zasób wykryć. Polecenia cmdlet, którego nazwa zawiera czasownik Ukryj może na przykład ukrywają usługi przez użytkownika. To polecenie jest powiązany z `Show`.|Dla tej akcji nie należy używać zlecenia, takie jak bloku.|
|[Dołącz do](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Łączy zasoby w jeden zasób. Na przykład `Join-Path` polecenia cmdlet łączy ścieżki z jednej z jego ścieżek podrzędnych do tworzenia pojedynczej ścieżki. To polecenie jest powiązany z `Split`.|Dla tej akcji nie należy używać czasowników, takie jak łączenie, Unite, Połącz lub skojarz.|
|[Zablokuj](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Zabezpiecza zasobu. To polecenie jest powiązany z `Unlock`.|Dla tej akcji nie należy używać czasowników, takie jak ograniczanie lub bezpieczny.|
|[Przenieś](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Przenosi zasób z jednej lokalizacji. Na przykład `Move-Item` polecenie cmdlet powoduje przeniesienie elementu z jednej lokalizacji w magazynie danych do innej lokalizacji.|Dla tej akcji nie należy używać czasowników, takie jak Transfer, nazwa lub migracji.|
|[Nowe](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Tworzy zasób. ( `Set` Zlecenia może również służyć podczas tworzenia zasobu, który zawiera dane, takie jak `Set-Variable` polecenia cmdlet.)|Dla tej akcji nie należy używać czasowników, takie jak tworzenie, wygeneruj, kompilacji, upewnij lub Przydziel.|
|[Otwórz](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Zmienia stan zasobów, aby stał się dostępny, dostępny i użyteczne. To polecenie jest powiązany z `Close`.||
|[Optymalizowanie](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Zwiększa to efektywność zasobu.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Usuwa element z góry stosu. Na przykład `Pop-Location` polecenie cmdlet zmienia bieżącą lokalizację do lokalizacji, która została ostatnio wypychane na stosie.||
|[Wypychanie](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Dodaje element do góry stosu. Na przykład `Push-Location` polecenia cmdlet wypychanie bieżącej lokalizacji na stosie.||
|[Wykonaj ponownie](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Resetuje zasób do stanu, które było cofnąć.||
|[Usuń](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Usuwa zasób z kontenera. Na przykład `Remove-Variable` polecenie cmdlet Usuwa zmienną i jej wartość. To polecenie jest powiązany z `Add`.|Dla tej akcji nie Użyj zleceń, takich jak czyszczenie, Wytnij, usuwania, odrzuceń, taśmie ani wymazać.|
|[Zmień nazwę](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Zmienia nazwę zasobu. Na przykład `Rename-Item` polecenia cmdlet, który umożliwia dostęp do przechowywanych danych, zmiany nazwy elementu w magazynie danych.|Dla tej akcji nie należy używać zlecenia, takie jak zmiany.|
|[Resetuj](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (r)|Ustawia zasobu stanu pierwotnego.||
|[Wyszukiwanie](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Tworzy odwołanie do zasobu w kontenerze.|Dla tej akcji nie należy używać czasowników, np. Znajdź lub zlokalizuj.|
|[Wybierz](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Lokalizuje zasobem w kontenerze. Na przykład `Select-String` polecenia cmdlet szukany tekst w plikach i ciągów.|Dla tej akcji nie należy używać czasowników, np. Znajdź lub zlokalizuj.|
|[Ustaw](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Zastępuje danych w istniejącym zasobie lub tworzy zasób, który zawiera dane. Na przykład `Set-Date` polecenie cmdlet zmienia czas systemowy na komputerze lokalnym. ( `New` Zlecenie można również utworzyć zasób.) To polecenie jest powiązany z `Get`.|Dla tej akcji nie należy używać zlecenia, takie jak zapisu, Reset, przypisz lub konfiguracja.|
|[Pokaż](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Sprawia, że zasób widoczne dla użytkownika. To polecenie jest powiązany z `Hide`.|Dla tej akcji nie należy używać poleceń, takich jak wyświetlanie lub produktu.|
|[Pomiń](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Pomija zasoby lub punktów sekwencji.|Dla tej akcji nie należy używać zlecenia, takie jak obejścia lub szybkie.|
|[Podziel](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Oddziela części zasobu. Na przykład `Split-Path` polecenie cmdlet zwraca różne części ścieżki. To polecenie jest powiązany z `Join`.|Dla tej akcji nie należy używać czasownik takie oddzielne.|
|[Krok](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Przechodzi do następnego punktu lub zasobów w sekwencji.||
|[Przełącznik](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Określa akcję, która przełącza między dwa zasoby, takie jak między dwiema lokalizacjami, obowiązki lub stanów.||
|[Cofnij](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (NZ)|Określa zasób do jego poprzedniego stanu.||
|[Odblokuj](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Zjednoczone Królestwo)|Zwalnia z zasobem, który został zablokowany. To polecenie jest powiązany z `Lock`.|Dla tej akcji nie należy używać czasowników, takie jak wersja, Unrestrict lub niezabezpieczony.|
|[Obejrzyj](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Stale bada lub monitoruje zasób dla zmian.||

## <a name="communications-verbs"></a>Komunikacja zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) klasy w celu zdefiniowania akcji, które są stosowane do komunikacji.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Połącz](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (DW)|Tworzy łącze między źródłem i miejscem docelowym. To polecenie jest powiązany z `Disconnect`.|Dla tej akcji nie należy używać czasowników przykład przyłączenie lub Telnet.|
|[Odłącz](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Przerywa połączenie między źródłowym i docelowym. To polecenie jest powiązany z `Connect`.|Dla tej akcji nie należy używać zleceń, takich jak przerwania lub wylogowywania.|
|[Odczyt](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Uzyskuje dane ze źródła. To polecenie jest powiązany z `Write`.|Dla tej akcji nie użycia zlecenia, takie jak Pozyskaj monit oraz uzyskać.|
|[Odbieranie](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Akceptuje informacje wysyłane ze źródła. To polecenie jest powiązany z `Send`.|Dla tej akcji nie używać zleceń, takich jak Odczyt, Zaakceptuj, ani nie wglądu.|
|[Wyślij](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Dostarcza informacje do miejsca docelowego. To polecenie jest powiązany z `Receive`.|Dla tej akcji nie należy używać czasowników, takich jak Put, emisji, wiadomości E-mail lub faksu.|
|[Zapis](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Dodaje informacje do obiektu docelowego. To polecenie jest powiązany z `Read`.|Dla tej akcji nie należy używać czasowników, takich jak Put lub drukowania.|

## <a name="data-verbs"></a>Dane zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) klasy w celu zdefiniowania akcji, które są stosowane do obsługi danych.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Nazwa zlecenie (alias)|Akcja|Komentarze|
|-------------------------|------------|--------------|
|[Kopia zapasowa](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Dane są przechowywane przez replikowanie.|Dla tej akcji nie należy używać czasowników, takie jak zapisać nagrywania, replikowanie lub synchronizacja.|
|[Punkt kontrolny](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Tworzy migawkę bieżącego stanu danych lub w jego konfiguracji.|Ta akcja nie należy używać czasownika, np. różnica|
|[Porównaj](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Oblicza dane z jednego zasobu do obsługi danych z innego zasobu.|Ta akcja nie należy używać czasownika, np. różnica|
|[Kompresuj](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Kompaktuje danych zasobu. Współdziała z `Expand`.|Dla tej akcji nie należy używać czasownik takich jak Compact.|
|[Konwertuj](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|Zmienia dane z jednego reprezentacji do innego, gdy polecenie cmdlet obsługuje konwersję dwukierunkowy lub polecenie cmdlet obsługuje konwersję między wieloma typami danych.|Dla tej akcji nie używać zlecenia, takie jak zmiany rozmiaru, lub próbkowania.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Konwertuje jeden typ podstawowy (rzeczownik polecenia cmdlet wskazuje stan danych wejściowych) w danych wejściowych co najmniej jeden typ obsługiwanych danych wyjściowych.|Dla tej akcji nie należy używać czasowników, takie jak eksportu, dane wyjściowe lub poza.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Konwertuje wartość w co najmniej jeden typ danych wejściowych do typu podstawowe wyjście (rzeczownik polecenia cmdlet wskazuje typ danych wyjściowych).|Dla tej akcji należy używać czasowników, takich jak importu, wprowadzania lub.|
|[Odinstalowywanie](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Odłącza nazwanych jednostek z lokalizacji. To polecenie jest powiązany z `Mount`.|Dla tej akcji nie należy używać czasowników, np. odinstalowanie lub Odłącz od niego.|
|[Edytuj](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modyfikuje istniejące dane, dodając lub usuwając zawartości.|Dla tej akcji nie należy używać poleceń, takich jak zmiana, aktualizacji lub modyfikowanie dla tej akcji.|
|[Rozwiń](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Przywraca dane zasobu są kompresowane do stanu pierwotnego. To polecenie jest powiązany z `Compress`.|Dla tej akcji nie należy używać czasowników, takich jak Rozłóż lub Dekompresuj.|
|[Eksportuj](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Hermetyzuje podstawowe dane wejściowe w trwałym magazynie danych, np. plik, lub do formatu wymiany. To polecenie jest powiązany z `Import`.|Dla tej akcji nie należy używać czasowników, takie jak wyodrębnianie lub kopii zapasowej.|
|[Grupa](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Rozmieszcza lub kojarzy co najmniej jednego zasobu.|Dla tej akcji nie używać zleceń, takich jak skojarzyć agregacji, rozmieszczanie, lub skorelować.|
|[Importuj](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Tworzy zasób na podstawie danych przechowywanych w trwałym magazynie danych (np. plik) lub ma format wymiany. Na przykład `Import-CSV` polecenie cmdlet importuje dane z pliku wartości rozdzielanych przecinkami (CSV) do obiektów, które mogą być używane przez inne polecenia cmdlet. To polecenie jest powiązany z `Export`.|Dla tej akcji nie należy używać czasowników, takie jak BulkLoad lub obciążenia.|
|[Inicjowanie](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (ruch przychodzący)|Przygotowuje zasób do użycia i ustawia go do stanu domyślnego.|Dla tej akcji nie należy używać zlecenia, takie jak wymazywania, Init, odnawiania, ponownej kompilacji, ponownie zainicjować lub instalacji.|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Stosuje ograniczenia do zasobu.|Dla tej akcji nie należy używać czasownika, np. limit przydziału.|
|[Scal](/dotnet/api/System.Management.Automation.VerbsData.Merge) (g)|Tworzy pojedynczy zasób z wielu zasobów.|Dla tej akcji nie należy używać czasowników, takie jak łączenie lub łączony albo oczekuje.|
|[Zainstaluj](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Dołącza nazwanych jednostek do lokalizacji. To polecenie jest powiązany z `Dismount`.|Dla tej akcji nie należy używać zlecenie Connect.|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Do przesyłania danych poza środowiskiem. Na przykład `Out-Printer` polecenia cmdlet wysyła dane do drukarki.||
|[Publikowanie](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Sprawia, że zasób niedostępne dla innych użytkowników. To polecenie jest powiązany z `Unpublish`.|Dla tej akcji nie używać poleceń, takich jak wdrażanie, wersji lub zainstalować.|
|[Przywróć](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Ustawia zasób do wstępnie zdefiniowanego stanu, takie jak stan, ustawiane przez `Checkpoint`. Na przykład `Restore-Computer` polecenia cmdlet rozpoczyna przywracanie systemu na komputerze lokalnym.|Dla tej akcji nie należy używać zlecenia, takie jak naprawy, Return, Cofnij lub poprawka.|
|[Zapisz](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Zachowuje dane, aby uniknąć utraty.||
|[Synchronizacja](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Gwarantuje, że dwa lub więcej zasobów znajdują się w tym samym stanie.|Dla tej akcji nie używać zleceń, takich jak replikacja, Coerce, ani nie pasuje.|
|[Cofanie publikacji](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Zasób staje się niedostępny dla innych użytkowników. To polecenie jest powiązany z `Publish`.|Dla tej akcji nie używać czasowników, np. Odinstaluj, Przywróć, lub ukryć.|
|[Aktualizacja](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Zapewnia aktualne, aby zachować stan, dokładności, zgodność lub zgodności zasobu. Na przykład `Update-FormatData` polecenia cmdlet aktualizacji i dodaje pliki formatowania do bieżącej konsoli programu PowerShell.|Dla tej akcji nie używać czasowników, np. w wyniku odświeżenia, odnawiania, ponownego obliczenia lub ponownego indeksowania.|

## <a name="diagnostic-verbs"></a>Diagnostyczne zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) klasy w celu zdefiniowania akcji, które są stosowane do diagnostyki.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Debugowanie](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (baza danych)|Sprawdza, czy zasób do diagnozowania problemów operacyjnych.|Dla tej akcji nie należy używać zlecenia, takie jak diagnozowania.|
|[Miara](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identyfikuje zasoby, które są używane przez określonej operacji, i pobiera dane statystyczne o zasobie.|Dla tej akcji nie należy używać czasowników, takie jak Calculate, określanie lub analizy.|
|[Polecenie ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Użyj `Test` zlecenie.||
|[Napraw](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Przywraca zasobem w dobrej kondycji|Dla tej akcji nie należy używać zleceń, takich jak poprawki lub przywracania.|
|[Rozwiąż](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (PV)|Mapuje reprezentację bardziej szczegółowy skrót reprezentację zasobu.|Dla tej akcji nie należy używać czasowników, takich jak rozwijanie lub określić.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Sprawdza, operacja ani spójność zasobów.|Dla tej akcji nie należy używać czasowników, takich jak Diagnozuj, Analizuj, odzyskana lub sprawdź, czy.|
|[Śledzenie](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Śledzenie działań zasobu.|Dla tej akcji nie używać zlecenia, takie jak śledzenie, wykonaj, sprawdź lub Dig.|

## <a name="lifecycle-verbs"></a>Cykl życia zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasy w celu zdefiniowania akcji, które dotyczą cyklu życia zasobu.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Zatwierdź](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Potwierdza lub wyraża zgodę na stan zasobu lub procesu.||
|[Asercja](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (tak)|Potwierdza stan zasobu.|Dla tej akcji nie należy używać zlecenia, takie jak Certify.|
|[Tworzenie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Tworzy artefaktu (zwykle w pliku binarnym lub dokument) poza niektórych zestawu plików wejściowych (zazwyczaj kodu źródłowego lub dokumenty deklaratywne)|To polecenie został dodany do programu PowerShell w wersji 6|
|[Pełne](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Kończy operację.||
|[Upewnij się,](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Potwierdza, sprawdza lub sprawdza stan zasobu lub procesu.|Dla tej akcji nie należy używać czasowników, takich jak potwierdzonym, zgadzam się, Certify, weryfikacji i sprawdź, czy.|
|[Odmów](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Odmawia, obiekty, blokuje lub sprzeciwia stanu zasobu lub procesu.|Dla tej akcji nie używać zleceń, takich jak odmówić bloku, obiektu, lub odrzucić.|
|[Wdrażanie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Wysyła aplikacji, witryny sieci Web lub rozwiązania do zdalnego obiektu docelowego [s] w taki sposób, że odbiorcy tego rozwiązania do niego dostęp po zakończeniu wdrożenia Wypełnij|To polecenie został dodany do programu PowerShell w wersji 6|
|[Wyłącz](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfiguruje zasobu stanu niedostępny lub nieaktywne. Na przykład `Disable-PSBreakpoint` polecenia cmdlet sprawia, że punkt przerwania jest nieaktywny. To polecenie jest powiązany z `Enable`.|Dla tej akcji nie należy używać czasowników, takich jak zatrzymania lub Ukryj.|
|[Włącz](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfiguruje zasobu stanu dostępności lub aktywny. Na przykład `Enable-PSBreakpoint` polecenia cmdlet sprawia, że punkt przerwania jest aktywny. To polecenie jest powiązany z `Disable`.|Dla tej akcji nie należy używać czasowników, takich jak początek lub Rozpocznij.|
|[Zainstaluj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (ma)|Umieszcza zasobu w lokalizacji i opcjonalnie inicjuje ją. To polecenie jest powiązany z `Uninstall`.|Dla tej akcji czy nie zlecenie użycia takich jak Instalator.|
|[Wywoływanie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Wykonuje akcję, na przykład przez uruchomienie polecenia lub metody.|Dla tej akcji nie należy używać czasowników, np. Uruchom lub uruchom.|
|[Zarejestruj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Tworzy wpis dla zasobu w repozytorium, takich jak bazy danych. To polecenie jest powiązany z `Unregister`.||
|[Żądanie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Pyta, czy zasób lub prosi o uprawnienia.||
|[Uruchom ponownie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Zatrzymuje działanie i uruchamia go ponownie. Na przykład `Restart-Service` zatrzymuje polecenia cmdlet, a następnie uruchamia usługę.|Dla tej akcji nie należy używać zlecenia, takie jak odtwarzanie.|
|[Wznów](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Rozpoczyna operację, która została zawieszona. Na przykład `Resume-Service` polecenia cmdlet uruchamia to usługa, która została zawieszona. To polecenie jest powiązany z `Suspend`.||
|[Rozpocznij](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Inicjuje operację. Na przykład `Start-Service` polecenia cmdlet uruchamia usługę. To polecenie jest powiązany z `Stop`.|Dla tej akcji nie należy używać czasowników, takie jak uruchamianie, zainicjuj lub rozruchu.|
|[Zatrzymaj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Zaprzestaje działania. To polecenie jest powiązany z `Start`.|Dla tej akcji nie używać zleceń, takich jak przerwać końcu, Zatrzymaj, lub Anuluj.|
|[Prześlij](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Przedstawia ilość zasobów do zatwierdzenia.|Dla tej akcji nie należy używać czasownika, np. wpisu.|
|[Wstrzymywanie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Wstrzymuje działanie. Na przykład `Suspend-Service` polecenie cmdlet powoduje wstrzymanie usługi. To polecenie jest powiązany z `Resume`.|Dla tej akcji nie należy używać zlecenia, takie jak wstrzymania.|
|[Odinstaluj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Usuwa zasób z określonej lokalizacji. To polecenie jest powiązany z `Install`.||
|[Wyrejestruj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (usługi)|Usuwa wpis dla zasobu z repozytorium. To polecenie jest powiązany z `Register`.|Dla tej akcji nie należy używać zlecenia, takie jak usuwanie.|
|[Poczekaj](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Wstrzymuje działanie, dopóki nie wystąpi określone zdarzenie. Na przykład `Wait-Job` polecenia cmdlet wstrzymuje operacje, dopóki jedna lub więcej zadań w tle są kompletne.|Dla tej akcji nie należy używać czasowników, takie jak stan uśpienia lub wstrzymania.|

## <a name="security-verbs"></a>Czasowniki zabezpieczeń

Używa programu PowerShell [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) klasy w celu zdefiniowania akcji, które dotyczą zabezpieczeń.
W poniższej tabeli wymieniono najbardziej zdefiniowanych czasowników.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Blok](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Ogranicza dostęp do zasobu. To polecenie jest powiązany z `Unblock`.|Dla tej akcji nie należy używać czasowników, takie jak Zapobiegaj, Limit lub Odmów.|
|[Udziel](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Umożliwia dostęp do zasobu. To polecenie jest powiązany z `Revoke`.|Dla tej akcji nie należy używać poleceń, takich jak Zezwalaj lub Włącz.|
|[Ochrona](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Zabezpiecza zasobu z ataku lub utratą. To polecenie jest powiązany z `Unprotect`.|Dla tej akcji nie należy używać czasowników, takie jak szyfrowanie, ochrona lub zamknięciem.|
|[Odwołaj](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Określa akcję, która nie zezwala na dostęp do zasobu. To polecenie jest powiązany z `Grant`.|Dla tej akcji nie należy używać czasowników, np. Usuń lub wyłącz.|
|[Odblokuj](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Usuwa ograniczenia do zasobu. To polecenie jest powiązany z `Block`.|Dla tej akcji nie należy używać zlecenia, takie jak wyczyść lub Zezwalaj.|
|[Wyłącz ochronę](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (maksymalnie)|Usuwa zabezpiecza z zasobu, który zostały dodane, aby uniknąć utraty albo atak. To polecenie jest powiązany z `Protect`.|Dla tej akcji nie należy używać czasowników, takich jak odszyfrowywania lub Unseal.|

## <a name="other-verbs"></a>Pozostałe zlecenia

Używa programu PowerShell [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) klasy, aby zdefiniować nazwy kanonicznej zlecenia, które nie mieszczą się w kategorii nazwy określone zlecenie, takie jak wspólne, komunikacji danych, cykl życia lub nazwy zlecenie zabezpieczeń zlecenia.

|Zlecenie (alias)|Akcja|Komentarze|
|--------------------|------------|--------------|
|[Użyj](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Używa lub zawiera zasób coś zrobić.||

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Polecenia cmdlet deklaracji](./cmdlet-class-declaration.md)

[Windows PowerShell przewodnik](../prog-guide/windows-powershell-programmer-s-guide.md)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
