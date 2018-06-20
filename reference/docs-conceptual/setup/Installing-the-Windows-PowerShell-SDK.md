---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie zestawu SDK programu Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953569"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalowanie zestawu SDK programu Windows PowerShell

Poniższy temat zawiera opis sposobu instalowania zestawu SDK programu PowerShell w różnych wersjach systemu Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalowanie programu Windows PowerShell 3.0 SDK dla systemu Windows 8 i Windows Server 2012

Program Windows PowerShell 3.0 jest automatycznie instalowany z systemem Windows 8 i Windows Server 2012.
Ponadto można pobrać i zainstalować zestawów odwołań dla programu Windows PowerShell 3.0 w ramach zestawu SDK systemu Windows 8.
Te zestawy pozwalają na zapis poleceń cmdlet, dostawców i programy hosta dla programu Windows PowerShell 3.0.
Podczas instalowania zestawu SDK systemu Windows dla systemu Windows 8, zestawy programu Windows PowerShell są automatycznie instalowane w folderze zestawu odwołania w \Program plików (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Aby uzyskać więcej informacji, zobacz [witryny pobierania systemu Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Przykłady kodu dla środowiska Windows PowerShell są także dostępne w Centrum opracowywania rozwiązań.
Aby uzyskać więcej informacji, zobacz strony przykładowego kodu na [witryny Centrum deweloperów](http://code.msdn.microsoft.com/windowsdesktop/).

Ponadto program Windows PowerShell 3.0 jest wstecznie zgodna z systemem Windows PowerShell 2.0 SDK, która obejmuje określonej liczby próbek kodu.
Aby uzyskać więcej informacji o sposobie pobrania zestawu SDK systemu Windows PowerShell 2.0 zobacz poniżej.
(Należy pamiętać, przykłady kodu 2.0 są zgodne z systemem Windows 8 i Windows PowerShell 3.0, można zainstalować program Windows PowerShell 2.0 na platformie Windows 8).

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalowanie programu Windows PowerShell 3.0 SDK dla systemu Windows 7 i Windows Server 2008 R2

Windows 7 i Windows Server 2008 R2 automatycznie ma zainstalowaną środowiska PowerShell 2.0.
Ponadto w tych systemach można zainstalować programu PowerShell 3.0.
(Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).).
Zgodnie z powyższym opisem można także zainstalować zestawu SDK systemu Windows 8, Windows 7 i Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalowanie programu Windows PowerShell 2.0 SDK dla systemu Windows 7, Vista, XP, Server 2003 i Server 2008

Windows PowerShell 2.0 SDK zawiera zestawy referencyjne wymagane do zapisywania poleceń cmdlet, dostawców i hostingu aplikacji i zapewnia C# przykładowy kod, który może służyć jako punkt początkowy, po rozpoczęciu pisania kodu.

Aby zainstalować zestaw SDK, zobacz [programu Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Zestawy referencyjne

Zestawy referencyjne są domyślnie instalowane w następującej lokalizacji: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Uwaga**: nie można załadować kodu, który jest skompilowany zestawy Windows PowerShell 2.0 do instalacji programu Windows PowerShell w wersji 1.0.
>Jednak kod, który jest skompilowany zestawy Windows PowerShell 1.0 mogą zostać załadowane do instalacji programu Windows PowerShell 2.0.

## <a name="samples"></a>Przykłady

Przykłady kodu są domyślnie instalowane w następującej lokalizacji: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Każda próbka jest krótki opis można znaleźć w poniższych sekcjach.

## <a name="cmdlet-samples"></a>Polecenia cmdlet próbek
**GetProcessSample01**

Przedstawia sposób zapisania prostego polecenia cmdlet, które pobiera wszystkie procesy na komputerze lokalnym.

**GetProcessSample02**

Przedstawiono sposób dodawania parametrów do polecenia cmdlet.
Polecenie cmdlet przyjmuje jeden lub więcej nazw procesu i zwraca dopasowywania procesów.

**GetProcessSample03**

Przedstawiono sposób dodawania parametrów, które akceptuje dane wejściowe z potoku.

**GetProcessSample04**

Przedstawia sposób obsługi błędów nonterminating.

**GetProcessSample05**

Pokazuje, jak można wyświetlić listę określonych procesów.

**SelectObject**

Przedstawia sposób zapisania filtr, aby wybrać tylko niektórych obiektów.

**SelectString**

Przedstawiono sposób wyszukiwania plików określonych wzorców.

**StopProcessSample01**

Pokazuje, jak wdrożyć *PassThru* parametr i jak utworzyć żądanie opinii użytkowników wywołań [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) i [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) metody.
Określ użytkowników *PassThru* parametru, jeśli chcą, aby wymusić polecenia cmdlet, aby zwrócić obiekt,

**StopProcessSample02**

Pokazuje, jak zatrzymać określonego procesu.

**StopProcessSample03**

Pokazuje sposób zadeklarować aliasów dla parametrów i obsługuje symbole wieloznaczne.

**StopProcessSample04**

Pokazuje, jak zadeklarować zestawów parametrów obiektu cmdlet przyjmuje jako dane wejściowe i sposobu określania domyślnego parametru zestaw do użycia.

## <a name="remoting-samples"></a>Przykłady usługi zdalne

**RemoteRunspace01**

Przedstawia sposób tworzenia zdalnego obszaru działania, który jest używany do ustanawiania połączenia zdalnego.

**RemoteRunspacePool01**

Pokazuje, jak utworzyć pulę zdalnego obszaru działania i jak równoczesne uruchamianie wielu poleceń za pomocą tej puli.

**Serialization01**

Pokazuje, jak sprawdzić w istniejącej klasy .NET, a następnie upewnij się, że informacje z wybranej właściwości publiczne tej klasy jest zachowana w serializacji/deserializacji.

**Serialization02**

Przedstawia sposób Spójrz na istniejącej klasy .NET i upewnij się, że informacje z wystąpienia tej klasy jest zachowywanie między serializacji/deserializacji podczas informacje nie są dostępne w publicznej właściwości klasy.

**Serialization03**

Przedstawia sposób Spójrz na istniejącej klasy .NET i upewnij się, że zdeserializować wystąpienia tej klasy i klas pochodnych (rehydrated) na żywo obiekty .NET.

## <a name="event-samples"></a>Przykłady zdarzeń

**Event01**

Przedstawia sposób tworzenia polecenia cmdlet dla rejestracji zdarzenia przez wynikających z ObjectEventRegistrationBase.

**Event02**

Pokazuje sposób do pokazano, jak otrzymywać powiadomienia zdarzeń programu Windows PowerShell, które są generowane na komputerach zdalnych.
Używa zdarzeń PSEventReceived za pośrednictwem [obszaru działania](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) klasy.

## <a name="hosting-application-samples"></a>Hosting aplikacji — przykłady

**Runspace01**

Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenia cmdlet synchronicznie.
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym.

**Runspace02**

Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) i [sortowania obiektu](http://go.microsoft.com/fwlink/?LinkID=113403) poleceń cmdlet synchronicznie.
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla każdego przetwarzania uruchomiony na komputerze lokalnym i obiektu sortowania sortuje obiekty na podstawie ich [identyfikator](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) właściwości.
Wyniki z tych poleceń jest wyświetlany za pomocą [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) formantu.

**Runspace03**

Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić skrypt synchronicznie i sposób obsługi błędów niepowodujący.
Skrypt otrzymuje listę nazw procesu, a następnie pobiera tych procesów.
Wyniki skryptu, między innymi niepowodujący błędów, które zostały wygenerowane podczas wykonywania skryptu, są wyświetlane w oknie konsoli.

**Runspace04**

Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasy na potrzeby uruchamiania poleceń i jak błędy Trwa przerywanie działania catch, które są generowane podczas uruchamiania polecenia.
Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy.
W związku z tym żadne obiekty nie są zwracane i zostanie zgłoszony błąd powodujący przerwanie.

**Runspace05**

Przedstawiono sposób dodawania przystawki do [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiekt, tak aby polecenia cmdlet przystawki jest dostępna po otwarciu obszaru działania.
Przystawka udostępnia polecenia cmdlet Get-Proc (zdefiniowane przez [próbki GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.

**Runspace06**

Pokazuje, jak dodać moduł do [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiekt, tak aby po otwarciu obszaru działania ładowany jest moduł.
Moduł zawiera polecenia cmdlet Get-Proc (zdefiniowane przez [próbki GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.

**Runspace07**

Pokazuje, jak utworzyć obszaru działania, a następnie użyj tego obszaru działania do uruchamiania dwóch poleceń cmdlet synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.

**Runspace08**

Przedstawiono sposób dodawania polecenia i argumentów do potoku z [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu i uruchamiania poleceń synchronicznie.

**Runspace09**

Pokazuje, jak dodać skrypt do potoku z [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu oraz sposobu uruchamiania skryptu asynchronicznie.
Zdarzenia są używane do obsługi danych wyjściowych skryptu.

**Runspace10**

Przedstawia sposób tworzenia domyślnej początkowy stan sesji, jak dodać polecenia cmdlet, aby [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), jak utworzyć obszaru działania, używającej stanu sesji początkowej i sposób uruchamiania polecenia przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)obiektu.

**Runspace11**

Przedstawia sposób użycia [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) klasy, aby utworzyć polecenie serwera proxy, który wywołuje istniejącego polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów.
Polecenie serwera proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania.
Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.

**PowerShell01**

Pokazuje, jak utworzyć za pomocą ograniczonego obszaru działania [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiektu.

**PowerShell02**

Przedstawia sposób użycia puli obszaru działania równoczesne uruchamianie wielu poleceń.

## <a name="host-samples"></a>Przykłady hosta

**Host01**

Przedstawia sposób wykonania aplikacji hosta, który używa hosta niestandardowego.
W tym przykładzie obszaru działania jest tworzony, który korzysta z hosta niestandardowego a następnie [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) interfejsu API jest używany do uruchamiania skryptu, który wywołuje "exit".
Następnie aplikacja hosta analizuje dane wyjściowe skryptu i wyświetla wyniki.

**Host02**

Przedstawia sposób zapisania aplikacji hosta, który używa środowiska wykonawczego programu Windows PowerShell wraz z implementacji hosta niestandardowego.
Aplikacja hosta ustawia kulturę hosta na język niemiecki, uruchamia [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenia cmdlet i wyświetla wyniki w postaci użytkownik zobaczy je przy użyciu pwrsh.exe, a następnie drukuje bieżąca data i godzina w języku niemieckim.

**Host03**

Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.

**Host04**

Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikowi określenie wiele wyborów.

**Host05**

Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ta aplikacja hosta obsługuje również wywołania do komputerów zdalnych przy użyciu [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) i [zakończenia-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) polecenia cmdlet.

**Host06**

Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.
Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu wprowadzonej przez użytkownika.

## <a name="provider-samples"></a>Przykłady dostawcy

**AccessDBProviderSample01**

Pokazuje, jak można zadeklarować klasy dostawcy, który pochodzi bezpośrednio z [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) klasy.
Został uwzględniony w tym miejscu jedynie, aby informacje były kompletne.

**AccessDBProviderSample02**

Pokazuje, jak zastąpić [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) i [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) metody do wywołania polecenia cmdlet New-elementu PSDrive i elementu PSDrive Usuń obsługi.
Klasa dostawcy, w tym przykładzie pochodzi z [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) klasy.

**AccessDBProviderSample03**

Pokazuje, jak zastąpić [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) i [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) metod do obsługi wywołania do elementu Get i Set-Item poleceń cmdlet.
Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasy.

**AccessDBProviderSample04**

Pokazuje, jak zastąpić metody kontenera do obsługi połączeń w celu Copy-Item, Get-ChildItem nowy element i polecenia cmdlet Remove-elementów.
Te metody powinny zostać wdrożone, gdy magazyn danych zawiera elementy, które są kontenerami.
Kontener jest grupą elementów podrzędnych w obszarze wspólnego elementu nadrzędnego.
Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasy.

**AccessDBProviderSample05**

Pokazuje, jak zastąpić metody kontenera do obsługi wywołania polecenia cmdlet Move-Item i ścieżki sprzężenia.
Te metody powinny zostać wdrożone, gdy użytkownik chce przenieść elementów w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery.
Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasy.

**AccessDBProviderSample06**

Pokazuje, jak zastąpić metody zawartości do obsługi wywołania z zawartością wyczyść pobrania zawartości i polecenia cmdlet Set-zawartości.
Te metody powinny zostać wdrożone, gdy użytkownik chce zarządzać zawartością elementów w magazynie danych.
Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasy która implementuje [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interfejsu.