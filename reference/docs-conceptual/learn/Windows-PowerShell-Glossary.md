---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Słownik programu PowerShell Windows
ms.openlocfilehash: 0827ec771b1744b87a8c0f0ddf48438f9ba484b2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030354"
---
# <a name="windows-powershell-glossary"></a>Słownik programu PowerShell Windows


|Termin|Definicja|
|--------|--------------|
|Moduł binarne|Moduł programu Windows PowerShell, którego moduł główny jest plikiem binarnym modułu (.dll). Binarny modułu może lub nie może zawierać manifestu modułu.|
|Typowy parametr|Parametr, który jest dodawany do wszystkich poleceń cmdlet, zaawansowane funkcje i przepływy pracy przez aparatu programu Windows PowerShell.|
|Źródło kropka|W programie Windows PowerShell można uruchomić polecenia, wpisując kropka i spacja przed wykonaniem polecenia. Uruchom polecenia, które są z dot źródło w bieżącym zakresie, a nie w nowy zakres. Wszelkie zmienne, aliasy, funkcji lub dyski, które polecenie tworzy są tworzone w bieżącym zakresie i są dostępne dla użytkowników po zakończeniu polecenia.|
|modułu dynamicznego|Moduł, który istnieje tylko w pamięci. Polecenia cmdlet New-Module i Import-PSSession utworzyć moduły dynamiczne.|
|Parametr dynamiczny|Parametr, który zostanie dodany do poleceń cmdlet programu Windows PowerShell, funkcji lub skryptu w określonych warunkach. Polecenia cmdlet, funkcji, dostawców i skrypty można dodać parametry dynamiczne.|
|formatowanie pliku|Pliku programu Windows PowerShell XML, który ma. rozszerzenie format.ps1xml i który definiuje, jak środowiska Windows PowerShell wyświetla obiekt na podstawie jego typu .NET Framework.|
|Globalny stan sesji|Stan sesji, który zawiera dane, które są dostępne dla użytkownika z sesji środowiska Windows PowerShell.|
|host|Interfejs, który korzysta z aparatu programu Windows PowerShell do komunikowania się z użytkownikiem. Na przykład host Określa, jak monity są obsługiwane między programu Windows PowerShell i użytkownika.|
|Aplikacja hosta|Program, który ładuje aparatu programu Windows PowerShell do swojego procesu i używa go do wykonywania operacji.|
|Metoda przetwarzania danych wejściowych|Metoda, która polecenia cmdlet można używać do przetwarzania rekordów otrzymywanych jako dane wejściowe. Metody przetwarzania danych wejściowych obejmują metody BeginProcessing, metoda ProcessRecord, metoda EndProcessing i metoda StopProcessing.|
|manifestu modułu|Moduł programu Windows PowerShell, zawierającej manifest, którego klucz polach RootModule jest puste.|
|manifestu modułu|Program Windows PowerShell plik danych (psd1), który opisuje zawartość modułu i który określa sposób przetwarzania modułu.|
|Stan sesji modułu|Stan sesji, który zawiera dane publicznych i prywatnych, modułu programu Windows PowerShell. Dane prywatne, w tym stanie sesji nie jest dostępny dla użytkownika z sesji środowiska Windows PowerShell.|
|Błąd niepowodujący|Błąd, który nie zatrzymuje programu Windows PowerShell z dalszego przetwarzania polecenia.|
|Rzeczownik|Wyrazu, który następuje łącznik na nazwę polecenia cmdlet programu Windows PowerShell. Rzeczownikiem opisano zasoby, na których działa polecenia cmdlet.|
|Zestaw parametrów|Grupa parametrów, które mogą służyć w tym samym poleceniu do wykonania określonej akcji.|
|Potoku|W programie Windows PowerShell do wysyłania wyników z poprzedniego polecenia jako dane wejściowe dla następnego polecenia w potoku.|
|Potok|Serię poleceń połączone przez operatorów potoku (&#124;) (ASCII 124). Każdy operator potok wysyła wyniki z poprzedniego polecenia jako dane wejściowe dla następnego polecenia.|
|PSSession|Typ sesji programu Windows PowerShell, który jest tworzony, zarządzane i zamknięte przez użytkownika.|
|Moduł głównego|Moduł określony w kluczu polach RootModule w manifeście modułu.|
|obszar działania|W programie Windows PowerShell, środowisko operacyjne, w którym jest wykonywany każde polecenie w potoku.|
|Blok skryptu|W programie Windows PowerShell programowania języka, zbiór instrukcji lub wyrażeń, które mogą być używane jako pojedyncza jednostka. Blok skryptu można zaakceptować argumenty i zwracać wartości.|
|Moduł skryptu|Moduł programu Windows PowerShell, którego moduł główny jest plik modułu skryptu (.psm1). Do modułu skryptu może lub nie może zawierać manifestu modułu.|
|plik modułu skryptu|Plik, który zawiera skrypt programu Windows PowerShell. Elementy członkowskie, które moduł skrypt eksportuje definiowane przez skrypt. Skrypt modułu pliki mają rozszerzenie nazwy pliku psm1.|
|powłoka|Interpreter poleceń, który służy do przekazywania poleceń do systemu operacyjnego.|
|Parametr przełącznika|Parametr, który nie przyjmuje argumentu.|
|błąd powodujący zakończenie|Błąd podczas zatrzymywania programu Windows PowerShell z przetworzeniem polecenia.|
|Transakcji|Pojedynczej Atomowej jednostki pracy. Praca w ramach transakcji, należy wykonać jako całości. dowolną część transakcji zakończy się niepowodzeniem, cała transakcja nie powiedzie się.|
|typy plików|Plik programu Windows PowerShell XML, który ma rozszerzenie .ps1xml i który rozciąga się właściwościom typów programu Microsoft .NET Framework w programie Windows PowerShell.|
|zlecenia|Wyrazu, który poprzedza łącznik nazwę polecenia cmdlet programu Windows PowerShell. Czasownik Opisuje akcję wykonywaną przez polecenie cmdlet.|
|Windows PowerShell|Powłoka wiersza polecenia oraz opartego na zadaniach technologii wykonywania skryptów, która zapewnia kompleksowe sterowanie Administratorzy IT i zautomatyzowane korzystanie z systemu zadań administracyjnych.|
|Polecenia programu Windows PowerShell|Elementy w potoku, które powodują akcji można przeprowadzić. Polecenia programu Windows PowerShell są wpisane na klawiaturze lub wywołana programowo.|
|Plik danych programu Windows PowerShell|Plik tekstowy, który ma rozszerzenie nazwy pliku psd1. Programu Windows PowerShell korzysta z plików danych do różnych celów, takich jak przechowywanie danych manifestu modułu i zapisując przetłumaczone ciągi dla internacjonalizacji skryptu.|
|Dysk programu Windows PowerShell|Dysku wirtualnego, który zapewnia bezpośredni dostęp do magazynu danych. Może być zdefiniowany przez dostawcę programu Windows PowerShell lub utworzone w wierszu polecenia. Dyski tworzone w wierszu polecenia są specyficzne dla sesji dysków i są tracone po zamknięciu sesji.|
|Windows PowerShell Integrated Scripting Environment (ISE)|Aplikacja hosta programu Windows PowerShell, która umożliwia uruchamianie poleceń i zapisu, testowanie i debugowanie skryptów w środowisku przyjazna, składni kolorowe zgodnych z kodowaniem Unicode.|
|Moduł programu Windows PowerShell|Samodzielna jednostka wielokrotnego użytku, która pozwala na partycję, organizowanie i abstrakcji w kodzie programu Windows PowerShell. Moduł może zawierać polecenia cmdlet, dostawcy, funkcje, zmienne i innych typów zasobów, które można importować jako pojedyncza jednostka.|
|Dostawca programu Windows PowerShell|Microsoft .NET Framework, na podstawie program, który sprawia, że dane w magazynie danych wyspecjalizowane dostępne w programie Windows PowerShell, aby można wyświetlać i zarządzać nią.|
|Skrypt programu Windows PowerShell|Skrypt, który został napisany w języku środowiska Windows PowerShell.|
|Plik skryptu programu Windows PowerShell|Jest to plik zawierający rozszerzeniem .ps1, i który zawiera skrypt, który został napisany w języku środowiska Windows PowerShell.|
|Przystawkę programu Windows PowerShell|Zasób, który definiuje zestaw poleceń cmdlet, dostawców i typów programu Microsoft .NET Framework, które można dodać do środowiska Windows PowerShell.|
|Przepływ pracy programu Windows PowerShell|Przepływ pracy to sekwencja zaprogramowanych, połączonych ze sobą czynności służących do wykonywania długotrwałych zadań lub do zapewnienia koordynacji wielu czynności na wielu różnych urządzeniach albo w wielu węzłach zarządzanych. Przepływ pracy programu Windows PowerShell umożliwia informatykom i deweloperom tworzenie sekwencji działań związanych z zarządzaniem wieloma urządzeniami lub pojedynczego zadania w ramach przepływu pracy jako przepływy pracy. Przepływ pracy programu Windows PowerShell umożliwia dostosowanie i uruchomić skrypty programu Windows PowerShell i pliki XAML przepływów pracy.|
