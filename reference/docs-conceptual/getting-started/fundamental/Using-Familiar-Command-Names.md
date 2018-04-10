---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie znanych nazw poleceń
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-familiar-command-names"></a>Używanie znanych nazw poleceń
Wywołuje się przy użyciu mechanizmu *aliasów*, programu Windows PowerShell umożliwia odwoływanie się do polecenia przez alternatywne nazwy. Aliasy umożliwiają użytkownicy mający doświadczenie w innych powłok ponowne użycie wspólnej nazwy poleceń, które znają podobnych operacji w programie Windows PowerShell. Mimo że nie omówimy aliasy programu Windows PowerShell szczegółowo, nadal można je jako Rozpoczynanie pracy z programu Windows PowerShell.

Wygładzanie kojarzy nazwę polecenia wpisany z innego polecenia. Na przykład programu Windows PowerShell ma funkcji o nazwie wewnętrznej **hosta wyczyść** który czyści okno danych wyjściowych. Po wpisaniu jednego **ze specyfikacją cls** lub **wyczyść** polecenie w wierszu polecenia programu Windows PowerShell interpretuje, że jest to alias **hosta wyczyść** funkcji i uruchamia  **Wyczyść hosta** funkcji.

Ta funkcja pozwala użytkownikom, aby dowiedzieć się, środowiska Windows PowerShell. Pierwszy, większość użytkowników Cmd.exe i UNIX ma duże zestawy poleceń, które użytkownicy już znane według nazwy i odpowiedniki środowiska Windows PowerShell może nie dawać wyników identyczne, są one Zamknij w formularzu, które użytkownicy mogą używać ich do pracy bez konieczności najpierw pamiętania nazwy środowiska Windows PowerShell. Po drugie główne źródło frustracji spowodowanej nowa powłoka dowiedzieć się, gdy użytkownik jest już zapoznać się z innym powłoki jest błędów, które są spowodowane "palca pamięci". Jeśli używasz Cmd.exe lat, kiedy ma pełne danych wyjściowych ekranu i wyczyścić go, reflexively należy wpisać **ze specyfikacją cls** polecenie i naciśnij klawisz ENTER. Bez alias do **hosta wyczyść** funkcji w programie Windows PowerShell, po prostu otrzyma komunikat o błędzie "**"ze specyfikacją cls"nie jest rozpoznawana jako polecenie cmdlet, funkcji, program wykonywalny lub plik skryptu.**" i pozostać z nie wiadomo co można zrobić, aby wyczyścić dane wyjściowe.

Poniżej znajduje się krótki lista typowych poleceń Cmd.exe i UNIX, które można używać wewnątrz środowiska Windows PowerShell:

|||||
|-|-|-|-|
|CAT|Dir|instalacji|rm|
|cd|echo|Przenieś|rmdir|
|chdir|wymazywanie|popd|uśpienia|
|Wyczyść|h|PS|Sortowanie|
|ze specyfikacją CLS|Historia|pushd|TEE|
|Kopiuj|kasowanie|pwd|typ|
|del|LP|r|zapisu|
|różnicowego|Ls|ren||

Jeśli okaże się, że przy użyciu jednej z tych poleceń reflexively i chcesz dowiedzieć się rzeczywistą nazwę natywnego polecenia programu Windows PowerShell, możesz użyć **Get Alias** polecenia:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Aby przykłady był bardziej czytelny, Podręcznik użytkownika programu Windows PowerShell zazwyczaj pozwala uniknąć aliasy użycia. Jednak znajomość więcej o aliasach to wczesne nadal warto Jeśli pracujesz z dowolnego wstawki kodu programu Windows PowerShell z innego źródła lub chcesz zdefiniować własny aliasów. Pozostałej części tej sekcji przedstawimy standardowe aliasy i sposób definiowania własnych aliasów.

### <a name="interpreting-standard-aliases"></a>Interpretowanie standardowe aliasów
W odróżnieniu od aliasy opisane powyżej, które są przeznaczone dla nazwy — zgodność z innych interfejsów, aliasy wbudowanych w programie Windows PowerShell zazwyczaj są przeznaczone do skrócenia. Te krótszej nazwy można wpisać szybko, ale są niemożliwe do odczytania, jeśli nie znasz odwołują się.

Programu Windows PowerShell próbuje znaleźć kompromis między jasności i skrócenia dostarczając zestaw standardowych aliasy, które są oparte na nazwy skrótu dla typowych zleceń i rzeczowniki. Umożliwia to podstawowy zestaw aliasów dla typowych poleceń cmdlet, które są do odczytu, gdy znasz nazwy skróconej. Na przykład w standardowe aliasy zlecenie **uzyskać** jest skracana do **g**, zlecenie **ustawić** jest skracana do **s**, rzeczownik **Elementu** jest skracana do **i**, rzeczownikiem **lokalizacji** jest skracana do **l**i rzeczownik polecenia jest skracana do **cm**.

Poniżej przedstawiono prosty przykład ilustrujący, jak to działa. Standardowa aliasu dla elementu Get pochodzi z łączenie **g** GET i **i** dla elementu: **gi**. Standardowa aliasu dla elementu zestawu pochodzi z łączenie **s** dla zestawu i **i** dla elementu: **si**. Standardowa aliasu dla lokalizacji Get pochodzi z łączenie **g** GET i **l** do lokalizacji, **gl**. Standardowa aliasu dla lokalizacji zestawu pochodzi z łączenie **s** dla zestawu i **l** do lokalizacji, **sl**. Standardowa alias Get-Command pochodzi z łączenie **g** GET i **cm** polecenia, **gcm**. Nie jest brak polecenia Set polecenia cmdlet, ale jeśli wystąpiły, firma Microsoft będzie mógł odgadnąć, czy alias standardowe pochodzą od **s** dla zestawu i **cm** dla polecenia: **scm**. Ponadto osoby zapoznać się z aliasów programu Windows PowerShell, który wystąpi **scm** można odgadnąć, czy alias odwołuje się do polecenia Set.

### <a name="creating-new-aliases"></a>Tworzenie nowego aliasów
Możesz utworzyć własne aliasy, za pomocą polecenia cmdlet Set-aliasu. Na przykład następujące instrukcje Tworzenie aliasów standardowe polecenia cmdlet, omówione w interpretacji aliasy standardowe:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Wewnętrznie Windows PowerShell korzysta z poleceń, takich jak te podczas uruchamiania, ale te aliasy nie są włączone. Przy próbie faktycznie wykonać jedną z tych poleceń, wystąpi błąd z informacją, że alias nie może być modyfikowany. Przykład:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```