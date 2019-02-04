---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Przekierowywanie danych przy użyciu poleceń cmdlet Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687139"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Przekierowywanie danych przy użyciu Out-* poleceń cmdlet

Windows PowerShell udostępnia kilka poleceń cmdlet umożliwiające kontrolowanie danych wyjściowych bezpośrednio. Te polecenia cmdlet mają dwie istotne cech.

Najpierw są zazwyczaj przekształcania danych do jakiegoś tekstu. Mogą to zrobić, ponieważ ich dane wyjściowe do składników systemu, które wymagają wprowadzania tekstu. Oznacza to, które są im potrzebne do reprezentowania obiektów jako tekst. W związku z tym tekst jest w formacie zostanie wyświetlony w oknie konsoli środowiska Windows PowerShell.

Po drugie, te polecenia cmdlet użyć zlecenie programu Windows PowerShell **się** ponieważ one wysyłać informacje za pomocą programu Windows PowerShell do innej lokalizacji. **Wyjściowego hosta** polecenie cmdlet nie jest wyjątkiem: wyświetlanie okna host znajduje się poza programu Windows PowerShell. Jest to ważne, ponieważ po wysłaniu danych z programu Windows PowerShell, faktycznie jest usuwany. Widać to w przypadku próby utworzenia potoku danych strony do okna hosta, a następnie ponów próbę sformatować je jako lista, jak pokazano poniżej:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Można by oczekiwać polecenia, aby wyświetlić strony informacji o procesie w formacie listy. Zamiast tego Wyświetla listy tabelarycznej domyślne:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

**Wyjściowego hosta** polecenia cmdlet wysyła dane bezpośrednio do konsoli, więc **Format-Lista** polecenia nigdy nie otrzymuje żadnych czynności, aby sformatować.

Poprawny sposób struktury to polecenie jest umieszczenie **wyjściowego hosta** polecenia cmdlet na końcu potoku, jak pokazano poniżej. Powoduje to przetwarzanie danych do sformatowania przed są stronicowane i wyświetlane na liście.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Dotyczy to wszystkich **się** polecenia cmdlet. **Się** polecenia cmdlet powinny zawsze pojawiają się na końcu potoku.

> [!NOTE]
> Wszystkie **się** poleceń cmdlet renderowania dane wyjściowe jako tekst, przy użyciu formatowania w praktyce, w oknie konsoli, w tym wierszu długość granicach.

#### <a name="paging-console-output-out-host"></a>Stronicowanie danych wyjściowych konsoli (wyjściowego hosta)

Domyślnie środowisko Windows PowerShell wysyła dane do okna hosta, które jest dokładnie wyjściowego hosta polecenia cmdlet robi. Podstawowym zastosowaniem hostowania wyjściowego polecenia cmdlet jest stronicowanie danych, tak jak Omówiliśmy to wcześniej. Na przykład następujące zastosowania polecenia wyjściowego hostowanie strony danych wyjściowych polecenia cmdlet Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

Można również użyć **więcej** funkcji do danych strony. W programie Windows PowerShell **więcej** jest funkcją, która wywołuje **wyjściowego hosta — stronicowania**. Następujące polecenie, który demonstruje sposób użycia **więcej** funkcję, aby dane wyjściowe polecenia Get strony:

```powershell
Get-Command | more
```

Jeśli dołączysz jeden lub więcej nazw plików jako argumenty do funkcji więcej funkcja odczytuje określone pliki i stronie ich zawartość do hosta:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Odrzucanie danych wyjściowych (wyjściowego o wartości Null)

**Wyjściowego o wartości Null** polecenia cmdlet jest przeznaczona do natychmiast odrzucić wszystkie dane wejściowe odbierze. Jest to przydatne do odrzucania niepotrzebnych dane, które otrzymujesz jako efekt uboczny uruchomienia polecenia. Kiedy należy wpisać następujące polecenie, nie uzyskasz żadnych powrót z polecenia:

```powershell
Get-Command | Out-Null
```

**Wyjściowego o wartości Null** polecenie cmdlet nie odrzuca dane wyjściowe błędu. Na przykład wprowadzając następujące polecenie, zostanie wyświetlony komunikat informujący o tym, że programu Windows PowerShell nie rozpoznaje "Jest-NotACommand":

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Drukowanie danych (Out-drukarka)

Wydrukować dane, używając **Out-drukarki** polecenia cmdlet. **Out-drukarki** polecenia cmdlet użyje drukarki domyślnej, jeśli nie podasz nazwę drukarki. Można użyć żadnych drukarek, systemem Windows, podając jego nazwę wyświetlaną. Nie ma potrzeby dla każdego rodzaju mapowania portu drukarki lub rzeczywistego fizyczne drukarki. Na przykład jeśli narzędzia obrazowania dokumentu Microsoft Office, zainstalowane, możesz wysłać dane do pliku obrazu, wpisując:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Zapisywanie danych (pliku wyjściowego)

Wysłać dane wyjściowe do pliku, a nie w oknie konsoli przy użyciu **out-file** polecenia cmdlet. Następujące polecenie w wierszu wysyła listę procesów do pliku **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Wyniki użycia **out-file** polecenie cmdlet nie można oczekiwać, jeśli są używane do przekierowania danych wyjściowych tradycyjnych. Aby poznać jej zachowanie, należy pamiętać o kontekście, w którym **out-file** działania polecenia cmdlet.

Domyślnie **out-file** polecenie cmdlet tworzy plik w formacie Unicode. Jest to najlepsze domyślne w perspektywie długoterminowej, ale oznacza to, że narzędzia, które oczekują plików ASCII nie będą działać poprawnie przy użyciu domyślnego formatu danych wyjściowych. Można zmienić domyślnego formatu danych wyjściowych ASCII, za pomocą **kodowanie** parametru:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** formatów plików zawartości, aby wyglądał jak na dane wyjściowe z konsoli. To powoduje, że dane wyjściowe do skrócenia dokładnie tak jak w oknie konsoli, w większości przypadków. Jeśli na przykład uruchom następujące polecenie:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

Dane wyjściowe będą wyglądać następująco:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Aby uzyskać dane wyjściowe nie wymusza zawinięte, aby dopasować szerokości ekranu, można użyć **szerokość** parametru, aby określić szerokość linii. Ponieważ **szerokość** jest parametrem 32-bitowa liczba całkowita może mieć wartość maksymalna to 2147483647. Wpisz następujące polecenie, aby ustawić szerokość linii ta wartość maksymalna:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

**Out-file** polecenia cmdlet jest najbardziej użyteczna, gdy użytkownik chce zapisać danych wyjściowych, ponieważ może być wyświetlany w konsoli. Aby uzyskać bardziej precyzyjną kontrolę nad format danych wyjściowych należy bardziej zaawansowanych narzędzi. Przyjrzymy się w następnym rozdziale, wraz z informacjami o manipulowanie obiektem.