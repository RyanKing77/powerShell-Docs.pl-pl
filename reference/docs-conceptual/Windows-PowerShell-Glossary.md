---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Słownik programu Windows PowerShell
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-glossary"></a>Słownik programu Windows PowerShell


|Termin|Definicja|
|--------|--------------|
|Moduł binarne|Moduł programu Windows PowerShell, których główny moduł jest pliku binarnego modułu (.dll). Binarny modułu może lub nie może zawierać manifestu modułu.|
|Typowy parametr|Parametr, który jest dodawany do wszystkich poleceń cmdlet, zaawansowane funkcje i przepływy pracy przez aparat programu Windows PowerShell.|
|Źródło kropka|W programie Windows PowerShell, aby uruchomić polecenie wpisując kropka i spacja przed wykonaniem polecenia. Uruchom polecenia, które są kropka powierzając jej ich konserwację w bieżącym zakresie zamiast w nowego zakresu. Wszystkie zmienne, aliasy, funkcji lub dyski tworzonych przez polecenie są tworzone w bieżącym zakresie i są dostępne dla użytkowników, po zakończeniu polecenia.|
|Moduł dynamicznej|Moduł, który istnieje tylko w pamięci. Polecenia cmdlet New-Module i Import-PSSession tworzenia dynamicznej modułów.|
|parametru dynamicznego|Parametr, który zostanie dodany do polecenia cmdlet programu Windows PowerShell, funkcji lub skryptu w niektórych warunkach. Polecenia cmdlet, funkcji, dostawców i skryptów można dodawać parametrów dynamicznych.|
|formatowanie pliku|Plik XML programu PowerShell systemu Windows. rozszerzenie format.ps1xml i który definiuje sposób środowiska Windows PowerShell wyświetla obiekt na podstawie jego typu .NET Framework.|
|globalnego stanu sesji|Stan sesji, który zawiera dane, które są dostępne dla użytkownika z sesji środowiska Windows PowerShell.|
|Host|Interfejs, który korzysta z aparatu programu Windows PowerShell do komunikowania się z użytkownikiem. Na przykład host Określa obsługi monity między środowiska Windows PowerShell i użytkownikiem.|
|Host aplikacji|Program, który ładuje aparat programu Windows PowerShell do procesu i używa go do wykonania operacji.|
|dane wejściowe przetwarzania — metoda|Metoda, która polecenia cmdlet można użyć do przetwarzania rekordów, które otrzymuje jako dane wejściowe. Metody wejściowe przetwarzania to metoda BeginProcessing, metoda ProcessRecord metody EndProcessing i metody StopProcessing.|
|Moduł manifestu|Moduł programu Windows PowerShell z manifestu, którego klucz RootModule jest puste.|
|manifestu modułu|Środowisko Windows PowerShell plik danych (psd1), który opisuje zawartość modułu i który określa sposób przetwarzania modułu.|
|Moduł stanu sesji|Stan sesji, który zawiera dane publiczne i prywatne modułu programu Windows PowerShell. Dane prywatne, w tym stanie sesji nie jest dostępne dla użytkownika z sesji środowiska Windows PowerShell.|
|Błąd niepowodujący|Błąd, który nie zatrzymuje przed kontynuowaniem do przetworzenia polecenia programu Windows PowerShell.|
|rzeczownik|Wyrazu następującego łącznik nazwę polecenia cmdlet programu Windows PowerShell. Rzeczownik Opisuje zasoby, na których działa polecenia cmdlet.|
|Zestaw parametrów|Grupa parametrów, które mogą służyć do tego samego polecenia do wykonania określonej akcji.|
|potoku|W programie Windows PowerShell, aby wysłać wyniki poprzednie polecenie jako dane wejściowe następne polecenie w potoku.|
|Potoku|Serii poleceń połączone przez operatorów potoku (&#124;) (ASCII 124). Każdy operatora potoku wysyła wyniki poprzednie polecenie jako dane wejściowe do następnego polecenia.|
|PSSession|Typ sesji środowiska Windows PowerShell, który jest tworzony, zarządzane i zamknięte przez użytkownika.|
|Moduł główny|Moduł określona w kluczu RootModule w manifeście modułu.|
|runspace|W programie Windows PowerShell, czyli środowisku operacyjnym, w którym wykonywane jest każde polecenie w potoku.|
|Blok skryptu|W programie Windows PowerShell programowania języka, to zbiór instrukcji lub wyrażeń, które mogą być używane jako pojedyncza jednostka. Blok skryptu mogą akceptować argumenty i zwracać wartości.|
|Moduł skryptu|Moduł programu Windows PowerShell, których główny moduł jest plik modułu skryptu (.psm1). Moduł skryptu może lub nie może zawierać manifestu modułu.|
|plik skryptu modułu|Plik zawierający skrypt programu Windows PowerShell. Skrypt definiuje elementów członkowskich, które eksportuje moduł skryptu. Skrypt modułu pliki mają rozszerzenie nazwy pliku .psm1.|
|powłoki|Interpreter poleceń, który służy do przekazywania poleceń do systemu operacyjnego.|
|Parametr przełącznika|Parametr, który nie przyjmuje argumentu.|
|błąd powodujący przerwanie|Wystąpił błąd zatrzymuje przetwarzanie polecenia programu Windows PowerShell.|
|Transakcji|Atomowej jednostki pracy. Praca w transakcji, należy wykonać jako całości. Jeśli dowolną część transakcji nie powiedzie się, cała transakcja nie powiedzie się.|
|typy plików|Plik XML programu PowerShell systemu Windows, który ma rozszerzenie .ps1xml i który rozszerza właściwości typów programu Microsoft .NET Framework w programie Windows PowerShell.|
|Zlecenie|Program word poprzedza łącznik nazwę polecenia cmdlet programu Windows PowerShell. Zlecenie Opisuje akcję, która wykonuje polecenie cmdlet.|
|Windows PowerShell|Powłoka wiersza polecenia i oparty na zadaniach technologia skryptów, która zapewnia kompleksowe sterowanie Administratorzy IT i automatyzacji systemu zadań administracyjnych.|
|Polecenia programu Windows PowerShell|Elementy w potoku, które powodują akcję przeprowadzenie. Poleceń programu Windows PowerShell są wpisywane w klawiatury lub wywołać programowo.|
|Plik danych programu Windows PowerShell|Plik tekstowy, który ma rozszerzenie nazwy pliku psd1. Program Windows PowerShell korzysta z plików danych do różnych celów, takich jak przechowywanie danych manifestu modułu i przechowywanie przetłumaczone ciągi dla internacjonalizacji skryptu.|
|Dysk programu Windows PowerShell|Dysk wirtualny, który zapewnia bezpośredni dostęp do magazynu danych. Może być zdefiniowany przez dostawcę środowiska Windows PowerShell lub utworzone w wierszu polecenia. Dyski utworzone w wierszu polecenia są specyficzne dla sesji dysków i zostaną utracone po zamknięciu sesji.|
|Windows PowerShell Integrated Scripting Environment (ISE)|Aplikacja hosta programu Windows PowerShell, która umożliwia uruchamianie poleceń i zapisu, testowanie i debugowanie skryptów w środowisku standardem Unicode przyjaznych, składni kolorze.|
|Moduł programu Windows PowerShell|Samodzielna jednostka wielokrotnego użytku, która pozwala na partycję, organizować i abstrakcyjnej kodu programu Windows PowerShell. Moduł może zawierać polecenia cmdlet, dostawców, funkcje, zmienne i inne typy zasobów, które można importować jako pojedyncza jednostka.|
|Dostawca programu Windows PowerShell|Microsoft .NET Framework na podstawie program, który udostępnia dane w magazynie danych specjalne w programie Windows PowerShell, aby można wyświetlać i zarządzać nią.|
|Skrypt programu Windows PowerShell|Skrypt, który jest napisany w języku środowiska Windows PowerShell.|
|Plik skryptu programu Windows PowerShell|Plik, który ma rozszerzenie ps1 i zawierający skrypt, który jest napisany w języku środowiska Windows PowerShell.|
|Przystawka programu Windows PowerShell|Zasób, który definiuje zestaw poleceń cmdlet, dostawców i typy programu Microsoft .NET Framework, które mogą zostać dodane do środowiska Windows PowerShell.|
|Przepływ pracy programu Windows PowerShell|Przepływ pracy to sekwencja zaprogramowanych, połączonych ze sobą czynności służących do wykonywania długotrwałych zadań lub do zapewnienia koordynacji wielu czynności na wielu różnych urządzeniach albo w wielu węzłach zarządzanych. Przepływ pracy programu Windows PowerShell umożliwia informatykom i deweloperom tworzenie sekwencji zadań związanych z zarządzaniem wieloma urządzeniami lub jednego zadania w przepływie pracy, jak przepływów pracy. Przepływ pracy programu Windows PowerShell umożliwia dostosowanie i uruchomić skrypty programu Windows PowerShell i plików XAML jako przepływów pracy.|