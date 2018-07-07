---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie zestawu SDK programu Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893542"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalowanie zestawu SDK programu Windows PowerShell

W poniższym temacie opisano sposób instalowania zestawu SDK programu PowerShell w różnych wersjach systemu Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalowanie programu Windows PowerShell 3.0 zestawu SDK dla systemu Windows 8 i Windows Server 2012

Windows PowerShell 3.0 jest automatycznie instalowany z systemem Windows 8 i Windows Server 2012.
Ponadto można pobrać i zainstalować zestawy referencyjne dla programu Windows PowerShell 3.0 w ramach zestawu SDK dla systemu Windows 8.
Te zestawy umożliwiają pisanie poleceń cmdlet, dostawców i programy hosta dla programu Windows PowerShell 3.0.
Po zainstalowaniu zestawu SDK Windows dla systemu Windows 8, zestawy programu Windows PowerShell są automatycznie instalowane w folderze zestawu odwołania w `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Aby uzyskać więcej informacji, zobacz [witryny pobierania systemu Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Przykłady kodu programu Windows PowerShell są także dostępne w Centrum opracowywania rozwiązań.
Aby uzyskać więcej informacji, zobacz stronę próbki kodu w [witryny Centrum deweloperów](https://code.msdn.microsoft.com:443/windowsdesktop/).

Ponadto program Windows PowerShell 3.0 jest wstecznie zgodny z za pomocą Windows PowerShell 2.0 SDK, które zawierają wiele przykładów kodu.
Aby uzyskać więcej informacji na temat sposobu pobierania zestawu SDK programu Windows PowerShell 2.0 zobacz poniżej.
(Zwróć uwagę, przykłady kodu 2.0 są zgodne z systemem Windows 8 i Windows PowerShell 3.0, można zainstalować program Windows PowerShell 2.0 na platformie systemu Windows 8).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalowanie programu Windows PowerShell 3.0 SDK for Windows 7 i Windows Server 2008 R2

Windows 7 i Windows Server 2008 R2 automatycznie mieć zainstalowany program PowerShell w wersji 2.0.
Ponadto w tych systemach można zainstalować program PowerShell 3.0.
(Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).).
Jak opisano powyżej, można także zainstalować zestaw Windows 8 SDK na Windows 7 i Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalowanie programu Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003 i Server 2008

Windows PowerShell 2.0 SDK zawiera zestawy odwołań wymagane do zapisania poleceń cmdlet, dostawców i hostowanie aplikacji i udostępnia C# przykładowy kod, który może służyć jako punkt początkowy, po rozpoczęciu pisania kodu.

Aby zainstalować zestaw SDK, zobacz [zestawu SDK programu Windows PowerShell 2.0](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Zestawy referencyjne

Zestawy odwołania są instalowane domyślnie w następującej lokalizacji: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Nie można załadować kodu, który jest kompilowany dla zestawów programu Windows PowerShell 2.0 do instalacji programu Windows PowerShell w wersji 1.0.
> Jednak kod, który jest kompilowany dla zestawów programu Windows PowerShell w wersji 1.0 mogą zostać załadowane do instalacji programu Windows PowerShell 2.0.

## <a name="samples"></a>Przykłady

Przykłady kodu są instalowane domyślnie w następującej lokalizacji: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Każda próbka jest krótki opis można znaleźć w poniższych sekcjach.

## <a name="cmdlet-samples"></a>Przykłady polecenia cmdlet

### <a name="getprocesssample01"></a>GetProcessSample01

Pokazuje, jak pisanie prostego polecenia cmdlet, które pobiera wszystkie procesy na komputerze lokalnym.

### <a name="getprocesssample02"></a>GetProcessSample02

Pokazuje, jak dodać parametry do polecenia cmdlet.
Polecenie cmdlet przyjmuje jedną lub więcej nazw proces i zwraca pasujących procesów.

### <a name="getprocesssample03"></a>GetProcessSample03

Pokazuje, jak dodać parametry, które akceptują dane wejściowe z potoku.

### <a name="getprocesssample04"></a>GetProcessSample04

Pokazuje, jak obsługiwać błędy niekończące.

### <a name="getprocesssample05"></a>GetProcessSample05

Pokazuje, jak wyświetlić listę określonych procesów.

### <a name="selectobject"></a>SelectObject —

Przedstawia sposób zapisania filtru, aby wybrać tylko niektórych obiektów.

### <a name="selectstring"></a>SelectString

Pokazuje, jak na potrzeby wyszukiwania plików pod kątem określonego wzorców.

### <a name="stopprocesssample01"></a>StopProcessSample01

Pokazuje, jak zaimplementować *PassThru* parametr i jak prośba o opinię użytkownika przez wywołania [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) i [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) metody.
Określ użytkowników *PassThru* parametr, gdy chce wymusić polecenia cmdlet, aby zwrócić obiekt,

### <a name="stopprocesssample02"></a>StopProcessSample02

Pokazuje, jak można zatrzymać określonego procesu.

### <a name="stopprocesssample03"></a>StopProcessSample03

Pokazuje sposób deklarowania aliasów parametrów i sposób obsługi symboli wieloznacznych.

### <a name="stopprocesssample04"></a>StopProcessSample04

Pokazuje sposób deklarowania zestawów parametrów, obiekt, który jest polecenie cmdlet przyjmuje jako dane wejściowe i jak określić domyślnego parametru skonfigurowany do używania.

## <a name="remoting-samples"></a>Przykłady usług zdalnych

### <a name="remoterunspace01"></a>RemoteRunspace01

Pokazuje, jak utworzyć zdalnego obszaru działania, który jest używany do ustanawiania połączenia zdalnego.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Pokazuje sposób tworzenia puli zdalnego obszaru działania oraz sposobu uruchamiania wielu poleceń, jednocześnie przy użyciu tej puli.

### <a name="serialization01"></a>Serialization01

Pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacje z wybranej właściwości publiczne tej klasy jest zachowywany między serializacji/deserializacji.

### <a name="serialization02"></a>Serialization02

Pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacji z wystąpienia tej klasy jest zachowywany między serializacji/deserializacji, jeśli informacje nie są dostępne w publicznej właściwości klasy.

### <a name="serialization03"></a>Serialization03

Pokazuje, jak Przyjrzyj się istniejącej klasy .NET i upewnij się, deserializacji wystąpienia tej klasy i klas pochodnych (wypełnienia) na obiekty .NET na żywo.

## <a name="event-samples"></a>Przykłady zdarzeń

### <a name="event01"></a>Event01

Pokazuje, jak utworzyć polecenie cmdlet służące do rejestrowania zdarzeń pochodząca od ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Pokazuje, jak do pokazuje, jak otrzymywać powiadomienia zdarzenia programu Windows PowerShell, które są generowane na komputerach zdalnych.
Zdarzenie PSEventReceived udostępniane za pośrednictwem [obszarem działania](/dotnet/api/system.management.automation.runspaces.runspace) klasy.

## <a name="hosting-application-samples"></a>Przykłady aplikacji hostingu

### <a name="runspace01"></a>Runspace01

Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet synchronicznie.
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym.

### <a name="runspace02"></a>Runspace02

Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) poleceń cmdlet synchronicznie.
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym i `Sort-Object` sortuje obiekty, w zależności od ich [identyfikator](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) Właściwość.
Wyniki tych poleceń jest wyświetlana przy użyciu [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) kontroli.

### <a name="runspace03"></a>Runspace03

Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić skrypt synchronicznie i sposób obsługi błędy niepowodujące.
Skrypt otrzymuje listę nazw procesu, a następnie pobierze te procesy.
Wyniki skryptu, między innymi niepowodujące błędy, które zostały wygenerowane podczas uruchamiania skryptu, są wyświetlane w oknie konsoli.

### <a name="runspace04"></a>Runspace04

Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy do uruchamiania poleceń oraz jak catch kończący błędów, które są zgłaszane w przypadku uruchamiania polecenia.
Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy.
W rezultacie żadne obiekty nie są zwracane i generowany jest błąd powodujący zakończenie.

### <a name="runspace05"></a>Runspace05

Przedstawiono sposób dodawania przystawki do [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiekt cmdlet przystawki jest dostępne po otwarciu obszaru działania.
Przystawka udostępnia polecenia cmdlet Get-Proc (zdefiniowane przez [GetProcessSample01 przykładowe](https://technet.microsoft.com/library/ff602028.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.

### <a name="runspace06"></a>Runspace06

Przedstawiono sposób dodawania modułu, aby [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiekt moduł jest załadowany po otwarciu obszaru działania.
Moduł zawiera polecenia cmdlet Get-Proc (zdefiniowane przez [przykładowe GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.

### <a name="runspace07"></a>Runspace07

Pokazuje, jak utworzyć obszar działania, a następnie użyj tego obszaru działania na dwa polecenia cmdlet były uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.

### <a name="runspace08"></a>Runspace08

Pokazuje, jak dodać do potoku z poleceń i argumentów [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu i jak polecenia były uruchamiane synchronicznie.

### <a name="runspace09"></a>Runspace09

Pokazuje, jak dodać skrypt do potoku [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu oraz sposobu uruchamiania skryptu asynchronicznie.
Zdarzenia są używane do obsługi danych wyjściowych skryptu.

### <a name="runspace10"></a>Runspace10

Pokazuje, jak utworzyć domyślny początkowy stan sesji, jak dodać polecenia cmdlet, aby [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), jak utworzyć obszar działania, używającej stanu sesji początkowej i jak uruchamiać polecenia przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell)obiektu.

### <a name="runspace11"></a>Runspace11

Ilustruje sposób używania [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klasy, aby utworzyć polecenie proxy, który wywołuje istniejące polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów.
Polecenie proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania.
Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.

### <a name="powershell01"></a>PowerShell01

Pokazuje, jak utworzyć za pomocą ograniczonego obszaru działania [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiektu.

### <a name="powershell02"></a>PowerShell02

Pokazuje, jak użyć puli obszarem działania w celu jednoczesnego uruchamiania wielu poleceń.

## <a name="host-samples"></a>Przykładowe pliki hosta

### <a name="host01"></a>Host01

Pokazuje sposób implementacji aplikacji hosta, który używa niestandardowego hosta.
W tym przykładzie zostanie utworzony obszar działania, który używa niestandardowego hosta a następnie [PowerShell](/dotnet/api/system.management.automation.powershell) interfejsu API jest używane do uruchamiania skryptu, który wywołuje "Zamknij".
Aplikacja hosta następnie analizuje dane wyjściowe skryptu i wyświetla wyniki.

### <a name="host02"></a>Host02

Pokazuje, jak napisać aplikację hosta, która używa środowiska wykonawczego programu Windows PowerShell, oraz implementacji niestandardowego hosta.
Aplikacja hosta ustawia kulturę hosta na język niemiecki, przebiegów [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet i wyświetla wynik jako użytkownik je zobaczy przy użyciu pwrsh.exe, a następnie Drukuje bieżące data i godzina w języku niemieckim.

### <a name="host03"></a>Host03

Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.

### <a name="host04"></a>Host04

Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikom określić wiele opcji do wyboru.

### <a name="host05"></a>Host05

Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ta aplikacja hosta obsługuje również połączenia z komputerami zdalnymi przy użyciu [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) i [PsSession zakończenia](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) polecenia cmdlet.

### <a name="host06"></a>Host06

Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu, wprowadzonej przez użytkownika.

## <a name="provider-samples"></a>Przykłady dostawcy

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Pokazuje sposób deklarowania klas dostawcy, który pochodzi bezpośrednio z [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klasy.
Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Pokazuje, jak zastąpić [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) i [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) metody umożliwiające obsługę wywołań `New-PSDrive` i `Remove-PSDrive` polecenia cmdlet.
Klasa dostawcy, w tym przykładzie pochodzi z [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klasy.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Pokazuje, jak zastąpić [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) i [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) metody umożliwiające obsługę wywołań `Get-Item` i `Set-Item` polecenia cmdlet.
Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasy.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Pokazuje, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet.
Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery.
Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego.
Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasy.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Pokazuje, jak zastąpić obsługuje wywołań metod kontener `Move-Item` i `Join-Path` polecenia cmdlet.
Metody te powinny być zrealizowane, gdy użytkownik chce przenieść elementy znajdujące się w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery.
Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasy.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Pokazuje, jak i Zastąp zawartość metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet.
Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych.
Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasy która implementuje [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interfejsu.