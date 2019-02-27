---
title: Dokumentacja programu PowerShell Windows — nowości
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848594"
---
# <a name="whats-new"></a>Co nowego

Windows PowerShell 2.0 udostępnia następujące nowe funkcje do użycia podczas zapisywania poleceń cmdlet, dostawców i aplikacji hosta.

## <a name="modules"></a>Moduły

Możesz teraz pakiet i dystrybuować rozwiązania programu Windows PowerShell przy użyciu modułów. Moduły pozwalają na partycję, organizowanie i abstrakcyjnej kodu programu Windows PowerShell na jednostki samodzielnych, wielokrotnego użytku. Aby uzyskać więcej informacji na temat modułów Zobacz pisanie modułu programu Windows PowerShell.

## <a name="the-powershell-class"></a>Klasa programu PowerShell

Klasa PowerShell udostępnia prostsze rozwiązania do tworzenia aplikacji, określane jako aplikacji hosta, który programowe wykonywanie poleceń. Ta klasa umożliwia tworzenie potoku z poleceń, określ obszar działania, który jest używany do uruchamiania poleceń, a także określić polecenia wywoływania, synchronicznie lub asynchronicznie.

## <a name="the-runspacepool-class"></a>Klasa RunspacePool

Dzięki pulom obszarem działania do tworzenia wielu obszarach działania za pomocą jednego wywołania. Metoda CreateRunspacePool zapewnia kilka przeciążeń, które mogą służyć do tworzenia obszarach działania, które mają te same funkcje, takie jak tego samego hosta, stan początkowy sesji i informacje o połączeniu.

## <a name="the-initialsessionstate-class"></a>Klasa InitialSessionState

Klasa InitialSessionState służy do tworzenia konfiguracji stanu sesji, który jest używany po otwarciu obszaru działania. Możesz utworzyć konfigurację niestandardową, konfigurację domyślną, która zawiera polecenia, dostarczone przez mshshort i konfiguracji, w której polecenia są ograniczone możliwości sesji.

## <a name="remote-runspaces"></a>Zdalne obszary działania

Można teraz tworzyć obszary działania, który można otworzyć na komputerach zdalnych, dzięki czemu możesz uruchamiać polecenia na komputerze zdalnym i zbieranie wyników lokalnie. Aby utworzyć zdalnego obszaru działania, należy określić informacje dotyczące połączenia zdalnego, podczas tworzenia obszaru działania. Zobacz metody CreateRunspace i CreateRunspacePool przykłady. Informacje o połączeniu jest zdefiniowana w klasie RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementy w prywatnym obszarze działania

Teraz można utworzyć obszarach działania, której elementy są publicznych lub prywatnych. Dzięki temu można tworzyć obszary działania, której elementy są dostępne dla obszaru działania, ale nie są dostępne dla użytkownika. Zobacz opis klasy ConstrainedSessionStateEntry, aby dowiedzieć się, które elementy obszaru działania może się prywatnych.

## <a name="runspace-threading-modes-and-apartment-state"></a>Obszar działania wątkowości trybów i stan apartamentu

Można teraz określić, jak wątki są tworzone i używane po uruchomieniu poleceń w obszarze działania. Zobacz właściwości System.Management.Automation.Runspaces.Runspace.ThreadOptions i System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Możesz teraz uzyskać stan apartamentu wątków, które są używane do uruchamiania poleceń w obszarze działania. Zobacz właściwości System.Management.Automation.Runspaces.Runspace.ApartmentState i System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Polecenia cmdlet Transaction

Teraz można utworzyć polecenia cmdlet, które mogą być używane w transakcji. Gdy polecenie cmdlet jest używane w transakcji, jego akcje są tymczasowe i mogą być akceptowane lub odrzucony przez polecenia cmdlet transaction dostarczane przez środowisko Windows PowerShell.

Aby uzyskać więcej informacji na temat transakcji, zobacz instrukcje obsługi transakcji.

## <a name="transaction-provider"></a>Dostawca transakcji

Teraz można utworzyć dostawcy, których można używać w obrębie transakcji. Podobnie jak polecenia cmdlet, gdy dostawca jest używane w transakcji, jego akcje są tymczasowe i mogą być akceptowane lub odrzucony przez polecenia cmdlet transaction dostarczane przez środowisko Windows PowerShell.

Aby uzyskać więcej informacji na temat określania Obsługa transakcji w obrębie klasy dostawcy Zobacz właściwość System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Polecenia cmdlet Job

Teraz możesz zapisać poleceń cmdlet, które można wykonywać z tego działania jako zadanie. Te zadania są uruchamiane w tle bez interakcji z bieżącej sesji. Aby uzyskać więcej informacji o sposobie obsługi zadań w programie Windows PowerShell Zobacz zadania w tle.

## <a name="cmdlet-output-types"></a>Typy danych wyjściowych polecenia cmdlet

Można teraz określić typów programu .NET Framework, które są zwracane przez poleceń cmdlet od zadeklarowania atrybutu OutputType podczas zapisywania poleceń cmdlet. Dzięki temu inne osoby ustalić, jakiego rodzaju obiektów są zwracane przez polecenie cmdlet, analizując właściwość atrybutu OutputType polecenia cmdlet.

## <a name="event-support"></a>Obsługa zdarzeń

Teraz możesz tworzyć polecenia cmdlet służące do dodawania i korzystanie ze zdarzeń. Zobacz opis klasy PSEvent.

## <a name="proxy-commands"></a>Polecenia serwera proxy

Teraz możesz tworzyć polecenia serwera proxy, które można wykonać inne polecenie. Polecenie proxy umożliwia kontrolowanie, jakie funkcje polecenia cmdlet źródłowy jest dostępny dla użytkownika. Na przykład można utworzyć polecenia serwera proxy, który usuwa parametr, który jest dostarczany za pomocą polecenia źródła. Zobacz opis klasy ProxyCommand.

## <a name="multiple-choice-prompts"></a>Wiele monity o wybór

Teraz mogą pisać aplikacje, które mogą dostarczać monity, które umożliwiają użytkownikowi wybranie wielu opcji. Zobacz interfejs IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Interaktywnych sesji

Teraz mogą pisać aplikacje, które można uruchomić i zatrzymać interaktywnej sesji na komputerze zdalnym.
Zobacz interfejs IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Pomocy polecenia Cmdlet niestandardowych dostawców

Teraz można utworzyć niestandardowe tematy pomocy dla polecenia cmdlet dostawcy. Tematy pomocy niestandardowe polecenia cmdlet można wyjaśniają, jak polecenie cmdlet działa w dostawcy ścieżkę i dokumentu funkcji specjalnych, łącznie z parametrów dynamicznych, które dostawcy dodaje do polecenia cmdlet.
