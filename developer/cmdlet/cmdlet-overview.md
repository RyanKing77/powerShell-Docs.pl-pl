---
title: Polecenia cmdlet — omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229363"
---
# <a name="cmdlet-overview"></a>Polecenia cmdlet — omówienie

Polecenie cmdlet jest uproszczone polecenia, który jest używany w środowisku Windows PowerShell. Środowisko wykonawcze programu Windows PowerShell wywołuje te polecenia cmdlet w kontekście skryptów automatyzacji, które znajdują się w wierszu polecenia. Środowisko wykonawcze programu Windows PowerShell wywołuje również je programowo za pośrednictwem interfejsów API programu Windows PowerShell.

## <a name="cmdlets"></a>Polecenia cmdlet

Polecenia cmdlet wykonaj akcję i zwykle zwraca obiekt programu Microsoft .NET Framework do następnego polecenia w potoku. Aby zapisać polecenia cmdlet, musi implementować polecenia cmdlet klasy pochodnej z jednego z dwóch klas bazowych wyspecjalizowane polecenia cmdlet. Klasy pochodnej musi:

- Należy zadeklarować atrybut, który identyfikuje klasy pochodnej jako polecenia cmdlet.

- Zdefiniuj właściwości publiczne, które są oznaczone za pomocą atrybutów, które identyfikują właściwości publiczne jako parametry polecenia cmdlet.

- Musi zostać zastąpiona w przynajmniej jednej metody do rekordów proces przetwarzania danych wejściowych.

Możesz załadować zestaw, który zawiera klasę bezpośrednio przy użyciu [Import-Module](/powershell/module/microsoft.powershell.core/import-module) polecenia cmdlet, lub można utworzyć aplikacji hosta, która ładuje zestaw za pomocą [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) interfejsu API. Obie metody zapewniają dostęp programowy i wiersza polecenia, działanie polecenia cmdlet.

## <a name="cmdlet-terms"></a>Polecenia cmdlet warunki

Poniższe terminy są często stosowane w dokumentacji poleceń cmdlet programu Windows PowerShell:

### <a name="cmdlet-attribute"></a>Polecenia cmdlet atrybutu

Atrybut .NET Framework, który służy do deklarowania klasy polecenia cmdlet jako polecenia cmdlet.
Mimo że program PowerShell używa kilka atrybutów, które są opcjonalne, atrybut polecenia Cmdlet jest wymagany.
Aby uzyskać więcej informacji na temat tego atrybutu, zobacz [deklaracji atrybutu polecenia Cmdlet](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Parametr polecenia cmdlet

Właściwości publiczne, które definiują parametry, które są dostępne dla użytkownika lub aplikacji, która jest uruchomienie polecenia cmdlet.
Polecenia cmdlet wymaganych, nazwanych, pozycyjne, i *Przełącz* parametrów.
Przełącznik parametry umożliwiają zdefiniowanie parametrów, które są oceniane tylko wtedy, gdy parametry są określone w wywołaniu.
Aby uzyskać więcej informacji o różnych typach parametrów, zobacz [parametry polecenia Cmdlet](cmdlet-parameters.md).

### <a name="parameter-set"></a>Zestaw parametrów

Grupa parametrów, które mogą służyć w tym samym poleceniu do wykonania określonej akcji.
Polecenie cmdlet może mieć wiele zestawów parametrów, ale każdy zestaw parametrów musi mieć co najmniej jeden parametr, który jest unikatowy.
Projekt dobre polecenia cmdlet silnie sugeruje, że unikatowy parametr też być wymagany parametr.
Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [zestawy parametrów polecenia Cmdlet](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Parametr dynamiczny

Parametr, który jest dodawany do polecenia cmdlet w środowisku uruchomieniowym.
Zazwyczaj parametry dynamiczne są dodawane do polecenia cmdlet, gdy inny parametr jest równa określonej wartości.
Aby uzyskać więcej informacji na temat parametrów dynamicznych, zobacz [parametrów dynamicznych do polecenia Cmdlet](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Metoda przetwarzania danych wejściowych

Metoda, która polecenia cmdlet można używać do przetwarzania rekordów otrzymywanych jako dane wejściowe.
Metody przetwarzania danych wejściowych to [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody i [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) metody. Podczas implementowania polecenia cmdlet konieczne jest przesłonięcie co najmniej jeden z [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)i [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.
Zazwyczaj [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda jest metodą, które można przesłonić, ponieważ jest ona wywoływana dla każdego rekordu, który przetwarza polecenia cmdlet.
Z kolei [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody i [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody są wywoływane jeden raz w celu wykonania Przetwarzanie wstępne lub przetwarzanie końcowe rekordów.
Aby uzyskać więcej informacji o tych metodach, zobacz [metody przetwarzania danych wejściowych](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>Funkcja ShouldProcess

Program PowerShell służy do tworzenia poleceń cmdlet, które monitować użytkownika o opinię, zanim polecenia cmdlet sprawia, że zmiany do systemu.
Aby użyć tej funkcji, polecenia cmdlet należy zadeklarować, że obsługuje funkcję ShouldProcess, zadeklarować atrybut polecenia Cmdlet, gdy polecenie cmdlet musi wywołać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody z w obrębie danych wejściowych przetwarzania metody.
Aby uzyskać więcej informacji na temat obsługi funkcji ShouldProcess, zobacz [żądania potwierdzenia](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transakcji

Logiczna grupa poleceń, które są traktowane jako jedno zadanie.
Zadanie kończy się automatycznie, jeśli wszystkie polecenia w grupie zakończy się niepowodzeniem, a użytkownik ma możliwość zaakceptować lub odrzucić akcje wykonywane w ramach transakcji.
Aby uczestniczyć w transakcji, polecenia cmdlet należy zadeklarować, że obsługuje ona transakcji, gdy polecenia Cmdlet atrybut jest zadeklarowany.
Obsługa transakcji została wprowadzona w programie Windows PowerShell 2.0.
Aby uzyskać więcej informacji na temat transakcji, zobacz [sposobu obsługi transakcji](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Jak polecenia cmdlet różni się od poleceń

Polecenia cmdlet różnią się od poleceń w innych środowiskach powłoki poleceń w następujący sposób:

- Polecenia cmdlet są wystąpieniami klasy .NET Framework; nie są one autonomiczne pliki wykonywalne.

- Polecenia cmdlet mogą być tworzone z zaledwie tuzina wierszy kodu.

- Polecenia cmdlet zwykle nie własne analizy błędów prezentacji lub formatowanie danych wyjściowych. Analiza kodu, błąd prezentacji i formatowanie danych wyjściowych są obsługiwane przez środowisko uruchomieniowe programu Windows PowerShell.

- Poleceń cmdlet procesu wejściowych obiektów z potoku, a nie z strumienie tekstu i polecenia cmdlet zwykle dostarczaj obiektów jako dane wyjściowe do potoku.

- Polecenia cmdlet są zorientowane, ponieważ ich przetworzyć w danym momencie pojedynczy obiekt.

## <a name="cmdlet-base-classes"></a>Klasy podstawowe polecenia cmdlet

Program Windows PowerShell obsługuje poleceń cmdlet, które są uzyskiwane z następujących dwóch klas bazowych.

- Większość poleceń cmdlet są oparte na klas .NET Framework, które wynikają z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy bazowej. Wyprowadzanie z tej klasy umożliwia polecenia cmdlet, aby użyć minimalny zestaw, w zależności od środowiska uruchomieniowego programu Windows PowerShell. To ma dwie korzyści. Pierwszy korzyścią jest, że obiekty polecenia cmdlet są mniejsze i jest mniej prawdopodobne dotyczyły zmiany środowiska uruchomieniowego programu Windows PowerShell. Drugi korzyścią jest, że jeśli to konieczne, można bezpośrednio utworzyć wystąpienie obiektu polecenia cmdlet i następnie wywołać bezpośrednio, zamiast wywołanie go za pomocą środowiska uruchomieniowego programu Windows PowerShell.

- Polecenia cmdlet bardziej złożonych zależą od klas .NET Framework, które wynikają z [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy bazowej. Wyprowadzanie z tej klasy zapewnia znacznie szerszy dostęp do środowiska wykonawczego programu Windows PowerShell. Ten dostęp umożliwia Twojego polecenia cmdlet do wywoływania skryptów, dostęp do dostawcy i dostęp do stanu bieżącej sesji. (Aby uzyskać dostęp do stanu bieżącej sesji, pobieranie i Ustawianie zmiennych sesji i preferencje.) Wyprowadzanie z tej klasy zwiększa rozmiar obiektu polecenia cmdlet i oznacza, że Twoje polecenia cmdlet jest bardziej ściśle powiązany bieżącą wersję środowiska uruchomieniowego programu Windows PowerShell.

Ogólnie rzecz biorąc, chyba że potrzebujesz rozszerzonej dostępu do środowiska wykonawczego programu Windows PowerShell, użytkownik powinien pochodzić od [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy. Środowisko wykonawcze programu Windows PowerShell ma jednak możliwości szczegółowe rejestrowanie do wykonywania poleceń cmdlet. Jeśli model inspekcji zależy od tego rejestrowania, może uniemożliwić wykonywanie Twojego polecenia cmdlet w ramach innego polecenia cmdlet przez pochodząca od [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy.

## <a name="input-processing-methods"></a>Metody przetwarzania danych wejściowych

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy udostępnia następujące metody wirtualne, które są używane do przetwarzania rekordów. Wszystkie klasy pochodne polecenia cmdlet należy zastąpić, co najmniej jednym z pierwszych trzech metod:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Używane do zapewnienia opcjonalnych funkcji jednorazowe i przetwarzania wstępnego dla polecenia cmdlet.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Używane do zapewnienia funkcji przetwarzania przez rekordami polecenia cmdlet. [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodę mogą wywoływać dowolną liczbę razy, lub wcale, w zależności od danych wejściowych polecenia cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Używane do zapewnienia opcjonalnych funkcji jednorazowe i przetwarzanie końcowe dla polecenia cmdlet.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Używane, aby zatrzymać przetwarzanie, gdy użytkownik zatrzymuje polecenia cmdlet asynchronicznie (np. przez naciśnięcie klawiszy CTRL + C).

Aby uzyskać więcej informacji o tych metodach, zobacz [metody przetwarzania danych wejściowych polecenia Cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Atrybuty poleceń cmdlet

Program Windows PowerShell definiuje kilka atrybutów .NET Framework, które są używane do zarządzania poleceń cmdlet i określ typowych funkcji, które są dostarczane przez środowisko Windows PowerShell i mogą być wymagane przez polecenie cmdlet. Na przykład atrybuty są używane do wyznaczenia klasę jako polecenia cmdlet, aby określić parametrów polecenia cmdlet, a żądania sprawdzania poprawności danych wejściowych, tak aby deweloperzy polecenie cmdlet nie trzeba zaimplementować tę funkcję w ich kodzie polecenia cmdlet. Aby uzyskać więcej informacji na temat atrybutów, zobacz [programu Windows PowerShell atrybuty](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nazwy poleceń cmdlet

Program Windows PowerShell używa pary nazwa czasownik i rzeczownik poleceniach cmdlet nazwę. Na przykład `Get-Command` uwzględnione w programie Windows PowerShell polecenia cmdlet jest używana do pobierania wszystkich poleceń cmdlet, które są zarejestrowane w powłoce poleceń. Zlecenie Określa akcję wykonywaną przez polecenie cmdlet i rzeczownikiem identyfikuje zasób wykonywane działania polecenia cmdlet.

Te nazwy zostały określone, gdy klasy .NET Framework jest zadeklarowany jako polecenia cmdlet. Aby uzyskać więcej informacji o tym, jak zadeklarować klasę .NET Framework jako polecenia cmdlet, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Pisanie kodu dla polecenia Cmdlet

Ten dokument zawiera dwa sposoby, aby dowiedzieć się, jak polecenie cmdlet kod jest zapisywany. Jeśli wolisz wyświetlić kod bez dużo wyjaśnienie, zobacz [przykłady kodu polecenie Cmdlet](./examples-of-cmdlet-code.md). Jeśli wolisz, aby uzyskać więcej informacji o kodzie, zobacz [samouczek GetProc](./getproc-tutorial.md), [samouczek StopProc](./stopproc-tutorial.md), lub [samouczek SelectStr](./selectstr-tutorial.md) tematów.

Aby uzyskać więcej informacji na temat wskazówki dotyczące pisania poleceń cmdlet zobacz [wskazówki dotyczące programowania polecenia Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Zobacz też

[Pojęcia dotyczące polecenia Cmdlet programu PowerShell Windows](./windows-powershell-cmdlet-concepts.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
