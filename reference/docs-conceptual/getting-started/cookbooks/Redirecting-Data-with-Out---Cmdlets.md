---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Przekierowywanie danych przy użyciu poleceń cmdlet Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952124"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Przekierowywanie danych z Out-* poleceń cmdlet

Środowisko Windows PowerShell udostępnia kilka polecenia cmdlet umożliwiające sterowanie danych wyjściowych bezpośrednio. Te polecenia cmdlet udziału dwie najważniejsze czynniki.

Po pierwsze one zazwyczaj przekształcania danych do jakiegoś tekstu. Są to zrobić, ponieważ ich wyprowadzania danych składników systemu, które wymagają wprowadzania tekstu. Oznacza to, że potrzebuje do reprezentowania obiektów jako tekst. W związku z tym tekst jest w formacie zostanie wyświetlony w oknie konsoli środowiska Windows PowerShell.

Po drugie, te polecenia cmdlet użyj polecenia programu Windows PowerShell **limit** ponieważ one wysyłać informacje z programu Windows PowerShell do innych lokalizacji. **Wyjściowego hosta** polecenie cmdlet nie jest wyjątkiem: wyświetlanie okna host znajduje się poza środowiska Windows PowerShell. Jest to ważne w przypadku, gdy dane są przesyłane z programu Windows PowerShell, faktycznie jest usunięty. Użytkownik może wystąpić, jeśli próbuje utworzyć potok danych strony do okno hosta, a następnie spróbuj go sformatować jako listę, jak pokazano poniżej:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Może spodziewać się polecenie, aby wyświetlić strony informacji o procesie w formacie listy. Zamiast tego umożliwia wyświetlenie listy tabelarycznej domyślne:

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

**Wyjściowego hosta** polecenia cmdlet wysyła dane bezpośrednio do konsoli programu tak **Format-Lista** polecenia nigdy nie otrzymuje żadnych czynności, aby sformatować.

Prawidłowy sposób struktury tego polecenia jest umieszczenie **wyjściowego hosta** polecenia cmdlet na końcu potoku, jak pokazano poniżej. Powoduje to przetwarzania danych w liście przed stronicowana i wyświetlane.

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

Dotyczy to wszystkich **limit** polecenia cmdlet. **Limit** polecenia cmdlet powinny zawsze występować na końcu potoku.

> [!NOTE]
> Wszystkie **limit** poleceń cmdlet renderować dane wyjściowe jako tekst, przy użyciu formatowania obowiązująca, w oknie konsoli, łącznie z limitów długość wiersza.

#### <a name="paging-console-output-out-host"></a>Stronicowanie danych wyjściowych konsoli (wyjściowego hosta)

Domyślnie, programu Windows PowerShell wysyła dane do okna hosta, który jest dokładnie wyjściowego hosta polecenie cmdlet ma. Podstawowym zastosowaniem wyjściowego hosta polecenia cmdlet jest stronicowania danych, jak wspomniano wcześniej. Na przykład następujące zastosowania polecenia wyjściowego hosta dane wyjściowe polecenia cmdlet Get-Command strony:

```powershell
Get-Command | Out-Host -Paging
```

Można również użyć **więcej** funkcji do danych strony. W programie Windows PowerShell **więcej** jest funkcją, która wywołuje **wyjściowego Host-stronicowania**. Polecenie pokazuje przy użyciu **więcej** funkcji, aby dane wyjściowe polecenia Get strony:

```powershell
Get-Command | more
```

Jeśli jako argumenty funkcji więcej uwzględniony jednego lub więcej nazw plików, funkcja odczytu określonych plików i strony ich zawartość do hosta:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Odrzucanie danych wyjściowych (wyjściowego o wartości Null)

**Wyjściowego o wartości Null** polecenia cmdlet jest przeznaczona do natychmiast odrzucić wszystkie dane wejściowe odbiera. Jest to przydatne dla odrzucanie zbędne dane, który można pobrać jako efekt uboczny uruchomienia polecenia. Gdy wpisz następujące polecenie, nie powrócisz niczego polecenia:

```powreshell
Get-Command | Out-Null
```

**Wyjściowego o wartości Null** polecenia cmdlet nie odrzucenia danych wyjściowych błędu. Na przykład po wprowadzeniu poniższego polecenia, zostanie wyświetlony komunikat informujący o tym, że programu Windows PowerShell nie rozpoznaje "Jest-NotACommand":

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Drukowanie danych (Out-drukarki)

Dane można drukować przy użyciu **Out-drukarki** polecenia cmdlet. **Out-drukarki** polecenia cmdlet będzie używać drukarki domyślnej, jeśli nie podasz nazwę drukarki. Wszystkie drukarki z systemem Windows można użyć, określając jej nazwę wyświetlaną. Nie istnieje potrzeba dla dowolnego rodzaju mapowania portu drukarki lub rzeczywistego fizycznej drukarki. Na przykład jeśli masz narzędzia obrazu dokumentu Microsoft Office, zainstalowane, należy wysłać dane do pliku obrazu, wpisując:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Zapisywanie danych (pliku wyjściowego)

Możesz wysłać dane wyjściowe do pliku zamiast okna konsoli za pomocą **out-file** polecenia cmdlet. Następujące polecenie w wierszu wysyła listę procesów do pliku **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Wyniki za pomocą **out-file** polecenie cmdlet nie może być oczekiwać jeśli są używane do przekierowania tradycyjnych danych wyjściowych. Aby poznać jego zachowanie, musi być znane kontekst, w którym **out-file** działania polecenia cmdlet.

Domyślnie **out-file** polecenie cmdlet tworzy plik Unicode. W dłuższej perspektywie jest to najlepsze domyślny, ale oznacza to, że narzędzia, które oczekują plików ASCII nie będą działać poprawnie z domyślny format danych wyjściowych. Można zmienić domyślny format danych wyjściowych ASCII przy użyciu **kodowanie** parametru:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** formatów plików zawartości, aby wyglądały jak dane wyjściowe konsoli. Powoduje to, że dane wyjściowe do skrócenia dokładnie tak jak w oknie konsoli w większości przypadków. Jeśli na przykład uruchom następujące polecenie:

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

Aby uzyskać dane wyjściowe nie wymusza zawija wiersza, aby dopasować szerokości ekranu, można użyć **szerokość** parametr, aby określić szerokość linii. Ponieważ **szerokość** parametr 32-bitowa liczba całkowita, wartość maksymalna, może mieć to 2147483647. Wpisz następujące polecenie, aby ustawić szerokość linii ta wartość maksymalna:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

**Out-file** polecenia cmdlet jest najbardziej przydatne, gdy chcesz zapisać dane wyjściowe, jak będzie wyświetlana na konsoli. Aby uzyskać bardziej precyzyjną kontrolę nad format danych wyjściowych musisz mieć bardziej zaawansowane narzędzia. Przedstawiono w następnego rozdziału oraz niektóre szczegóły na temat manipulowanie obiektem.