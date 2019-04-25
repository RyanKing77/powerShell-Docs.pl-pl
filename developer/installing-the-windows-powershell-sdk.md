---
title: Instalowanie zestawu SDK programu Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082485"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalowanie zestawu SDK programu Windows PowerShell

Dotyczy: Windows PowerShell 2.0, Windows PowerShell 3.0

W poniższym temacie opisano sposób instalowania zestawu SDK programu PowerShell w różnych wersjach systemu Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalowanie programu Windows PowerShell 3.0 zestawu SDK dla systemu Windows 8 i Windows Server 2012

Windows PowerShell 3.0 jest automatycznie instalowany z systemem Windows 8 i Windows Server 2012. Ponadto można pobrać i zainstalować zestawy referencyjne dla programu Windows PowerShell 3.0 w ramach zestawu SDK dla systemu Windows 8. Te zestawy umożliwiają pisanie poleceń cmdlet, dostawców i programy hosta dla programu Windows PowerShell 3.0. Po zainstalowaniu zestawu SDK Windows dla systemu Windows 8, zestawy programu Windows PowerShell są automatycznie instalowane w folderze zestawu odwołania w \Program pliki (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Aby uzyskać więcej informacji zobacz Windows 8 SDK, witryny pobierania plików. Przykłady kodu programu Windows PowerShell są także dostępne w Centrum opracowywania rozwiązań.
Aby uzyskać więcej informacji zobacz strony przykładowego kodu w witrynie Centrum deweloperów.

Ponadto program Windows PowerShell 3.0 jest wstecznie zgodny z za pomocą Windows PowerShell 2.0 SDK, które zawierają wiele przykładów kodu. Aby uzyskać więcej informacji na temat sposobu pobierania zestawu SDK programu Windows PowerShell 2.0 zobacz poniżej. (Zwróć uwagę, przykłady kodu 2.0 są zgodne z systemem Windows 8 i Windows PowerShell 3.0, można zainstalować program Windows PowerShell 2.0 na platformie systemu Windows 8).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalowanie programu Windows PowerShell 3.0 SDK for Windows 7 i Windows Server 2008 R2

Windows 7 i Windows Server 2008 R2 automatycznie mieć zainstalowany program PowerShell w wersji 2.0. Ponadto w tych systemach można zainstalować program PowerShell 3.0. (Aby uzyskać więcej informacji, zobacz Instalowanie programu Windows PowerShell.). Jak opisano powyżej, można także zainstalować zestaw Windows 8 SDK na Windows 7 i Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalowanie programu Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003 i Server 2008

Windows PowerShell 2.0 SDK zawiera zestawy odwołań wymagane do zapisania poleceń cmdlet, dostawców i hostowanie aplikacji i udostępnia C# przykładowego kodu, który może służyć jako punkt początkowy, po rozpoczęciu pisania kodu.

Aby zainstalować zestaw SDK, zobacz zestawu SDK programu Windows PowerShell 2.0.

### <a name="reference-assemblies"></a>Zestawy referencyjne

Zestawy odwołania są instalowane domyślnie w następującej lokalizacji: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Nie można załadować kodu, który jest kompilowany dla zestawów programu Windows PowerShell 2.0 do instalacji programu Windows PowerShell w wersji 1.0. Jednak kod, który jest kompilowany dla zestawów programu Windows PowerShell w wersji 1.0 mogą zostać załadowane do instalacji programu Windows PowerShell 2.0.


### <a name="samples"></a>Przykłady

Przykłady kodu są domyślnie instalowane w następującej lokalizacji: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. Każda próbka jest krótki opis można znaleźć w poniższych sekcjach.

#### <a name="cmdlet-samples"></a>Przykłady polecenia cmdlet

- GetProcessSample01 — pokazuje, jak pisanie prostego polecenia cmdlet, które pobiera wszystkie procesy na komputerze lokalnym.
- GetProcessSample02 — pokazuje, jak dodać parametry do polecenia cmdlet. Polecenie cmdlet przyjmuje jedną lub więcej nazw proces i zwraca pasujących procesów.
- GetProcessSample03 — pokazuje, jak dodać parametry, które akceptują dane wejściowe z potoku.
- GetProcessSample04 — pokazuje, jak obsługiwać błędy niekończące.
- GetProcessSample05 — pokazuje, jak wyświetlić listę określonych procesów.
- SelectObject — przedstawia sposób zapisania filtru, aby wybrać tylko niektórych obiektów.
- SelectString — pokazuje, jak na potrzeby wyszukiwania plików pod kątem określonego wzorców.
- StopProcessSample01 — pokazuje sposób implementacji parametru PassThru oraz prośba o opinię użytkownika przez wywołania metody ShouldProcess i ShouldContinue. Użytkownicy z parametru PassThru określić, gdy chce wymusić polecenia cmdlet, aby zwrócić obiekt,
- StopProcessSample02 — pokazuje, jak zatrzymać proces.
- StopProcessSample03 — pokazuje sposób deklarowania aliasów parametrów i sposób obsługi symboli wieloznacznych.
- StopProcessSample04 — pokazuje sposób deklarowania zestawów parametrów, obiekt, który jest polecenie cmdlet przyjmuje jako dane wejściowe i jak określić domyślnego parametru skonfigurowany do używania.

#### <a name="remoting-samples"></a>Przykłady usług zdalnych

- RemoteRunspace01 — pokazuje, jak utworzyć zdalnego obszaru działania, który jest używany do ustanawiania połączenia zdalnego.
- RemoteRunspacePool01 — przedstawia sposób tworzenia puli zdalnego obszaru działania oraz sposobu uruchamiania wielu poleceń, jednocześnie przy użyciu tej puli.
- Serialization01 — pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacje z wybranej właściwości publiczne tej klasy jest zachowywany między serializacji/deserializacji.
- Serialization02 — pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacji z wystąpienia tej klasy jest zachowywany między serializacji/deserializacji, jeśli informacje nie są dostępne w publicznej właściwości klasy.
- Serialization03 — pokazuje, jak Przyjrzyj się istniejącej klasy .NET i upewnij się, deserializacji wystąpienia tej klasy i klas pochodnych (wypełnienia) na obiekty .NET na żywo.

#### <a name="event-samples"></a>Przykłady zdarzeń

- Event01 — pokazuje, jak utworzyć polecenie cmdlet służące do rejestrowania zdarzeń pochodząca od ObjectEventRegistrationBase.
- Event02 — pokazuje, jak do pokazuje, jak otrzymywać powiadomienia zdarzenia programu Windows PowerShell, które są generowane na komputerach zdalnych. Używa ona zdarzeń PSEventReceived udostępniane za pośrednictwem klasy obszarze działania.

#### <a name="hosting-application-samples"></a>Przykłady aplikacji hostingu

- Runspace01 — przedstawia sposób użycia klas programu PowerShell do uruchamiania `Get-Process` polecenia cmdlet synchronicznie.
`Get-Process` Polecenie cmdlet zwraca obiekty proces dla wszystkich procesów działających na komputerze lokalnym.
- Runspace02 — przedstawia sposób użycia klas programu PowerShell do uruchamiania `Get-Process` i `Sort-Object` poleceń cmdlet synchronicznie. `Get-Process` Polecenie cmdlet zwraca obiekty proces dla wszystkich procesów działających na komputerze lokalnym i `Sort-Object` sortuje obiekty, w zależności od ich właściwości identyfikatora. Wyniki tych poleceń jest wyświetlane przy użyciu formantu DataGridView.
- Runspace03 — pokazuje, jak używać klas programu PowerShell do uruchamiania skryptu synchronicznie i jak obsługiwać błędy niepowodujące. Skrypt otrzymuje listę nazw procesu, a następnie pobierze te procesy. Wyniki skryptu, między innymi niepowodujące błędy, które zostały wygenerowane podczas uruchamiania skryptu, są wyświetlane w oknie konsoli.
- Runspace04 — pokazuje sposób użycia klas programu PowerShell do uruchamiania poleceń oraz catch przerywa błędy, które są generowane podczas uruchamiania polecenia. Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy. W rezultacie żadne obiekty nie są zwracane i generowany jest błąd powodujący zakończenie.
- Runspace05 — pokazuje, jak dodać przystawkę do obiektu InitialSessionState, tak aby polecenia cmdlet przystawki jest dostępne po otwarciu obszaru działania. Ta przystawka zawiera procedura Get polecenia cmdlet (zdefiniowanej przez przykład GetProcessSample01) jest wykonywana synchronicznie przy użyciu obiekt programu PowerShell.
- Runspace06 — pokazuje, jak dodać moduł do obiektu InitialSessionState tak, aby moduł jest załadowany po otwarciu obszaru działania. Moduł zawiera procedura Get polecenia cmdlet (zdefiniowanej przez przykład GetProcessSample02) jest wykonywana synchronicznie przy użyciu obiekt programu PowerShell.
- Runspace07 — pokazuje, jak utworzyć obszar działania, a następnie użyj tego obszaru działania na dwa polecenia cmdlet były uruchamiane synchronicznie przy użyciu obiektu programu PowerShell.
- Runspace08 - pokazano, jak dodać polecenia i argumentów do potoku obiekt programu PowerShell oraz jak polecenia były uruchamiane synchronicznie.
- Runspace09 — pokazuje, jak dodać skrypt do potoku obiekt programu PowerShell oraz sposobu uruchamiania skryptu asynchronicznie. Zdarzenia są używane do obsługi danych wyjściowych skryptu.
- Runspace10 — pokazuje, jak utworzyć domyślny stan sesji początkowy, jak dodać polecenia cmdlet do InitialSessionState, jak utworzyć obszar działania, używającej stanu sesji początkowej i jak uruchamiać polecenia przy użyciu obiektu Środowisko PowerShell.
- Runspace11 — pokazuje sposób użycia klasy ProxyCommand, aby utworzyć polecenie serwera proxy, który wywołuje istniejące polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów. Polecenie proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania. Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.
- PowerShell01 — pokazuje, jak utworzyć ograniczonego obszaru działania, za pomocą obiektu InitialSessionState.
- PowerShell02 — pokazuje, jak użyć puli obszarem działania w celu jednoczesnego uruchamiania wielu poleceń.

#### <a name="host-samples"></a>Przykładowe pliki hosta

- Host01 — pokazuje sposób implementacji aplikacji hosta, który używa niestandardowego hosta. W tym przykładzie zostanie utworzony obszar działania, który używa niestandardowego hosta, a następnie interfejs API środowiska PowerShell służy do uruchamiania skryptu, który wywołuje "Zamknij". Aplikacja hosta następnie analizuje dane wyjściowe skryptu i wyświetla wyniki.
- Host02 — pokazuje, jak napisać aplikację hosta, która używa środowiska wykonawczego programu Windows PowerShell, oraz implementacji niestandardowego hosta. Aplikacja hosta ustawia kulturę hosta na język niemiecki, przebiegów `Get-Process` polecenia cmdlet i wyświetla wynik jako użytkownik je zobaczy przy użyciu pwrsh.exe, a następnie Drukuje bieżące data i godzina w języku niemieckim.
- Host03 — pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
- Host04 — pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikom określić wiele opcji do wyboru.
- Host05 — pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ta aplikacja hosta obsługuje również połączenia z komputerami zdalnymi przy użyciu `Enter-PsSession` i `Exit-PsSession` polecenia cmdlet.
- Host06 — pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli. Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu, wprowadzonej przez użytkownika.

#### <a name="provider-samples"></a>Przykłady dostawcy

- AccessDBProviderSample01 — pokazuje sposób deklarowania klas dostawcy, która wywodzi się bezpośrednio z klasy CmdletProvider. Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.

- AccessDBProviderSample02 — pokazuje, jak zastąpić metod NewDrive i RemoveDrive w celu obsługi wywołania `New-PSDrive` i `Remove-PSDrive` polecenia cmdlet. Klasa dostawcy, w tym przykładzie pochodzi z klasy DriveCmdletProvider.

- AccessDBProviderSample03 — pokazuje, jak zastąpić metod GetItem i SetItem w celu obsługi wywołania `Get-Item` i `Set-Item` polecenia cmdlet. Klasa dostawcy, w tym przykładzie pochodzi z klasy ItemCmdletProvider.

- AccessDBProviderSample04 — pokazuje, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet. Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery. Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego. Klasa dostawcy, w tym przykładzie pochodzi z klasy ItemCmdletProvider.

- AccessDBProviderSample05 — pokazuje, jak zastąpić obsługuje wywołań metod kontener `Move-Item` i `Join-Path` polecenia cmdlet. Metody te powinny być zrealizowane, gdy użytkownik chce przenieść elementy znajdujące się w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery. Klasa dostawcy, w tym przykładzie pochodzi z klasy NavigationCmdletProvider.

- AccessDBProviderSample06 — pokazuje, jak zastąpić treści metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet. Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych. Klasa dostawcy, w tym przykładzie pochodzi od klasy NavigationCmdletProvider i implementuje interfejs IContentCmdletProvider.
