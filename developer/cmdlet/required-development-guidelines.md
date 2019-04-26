---
title: Wymaganymi wytycznymi projektowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067471"
---
# <a name="required-development-guidelines"></a>Wskazówki dotyczące projektowania — użycie wymagane

Poniższe zalecenia należy przestrzegać podczas wpisywania poleceń cmdlet. Są one podzielone na wytyczne do projektowania, poleceń cmdlet i zalecenia dotyczące pisania kodu polecenie cmdlet. Jeśli nie przestrzegać następujących wytycznych, poleceń cmdlet programu może zakończyć się niepowodzeniem i, że użytkownicy mają pogorszenie środowiska pracy podczas korzystania z poleceń cmdlet.

## <a name="in-this-topic"></a>W tym temacie

### <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

- [Użyj tylko zatwierdzone czasowniki (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nazwy poleceń cmdlet: Znaki, których nie można używać (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nazwy parametrów, których nie można używać (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Obsługuje żądania potwierdzenia (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Obsługa parametru Force interaktywnych sesji (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Obiekty danych wyjściowych dokumentów (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Wytyczne dotyczące kodu

- [Pochodzi z polecenia Cmdlet lub skryptu PSCmdlet klasy (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Określ atrybut polecenia Cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Zastąp dane wejściowe przetwarzania metody (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Określ atrybut OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Nie będzie przechowywała dojścia do obiektów danych wyjściowych (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Obsługa błędów niezawodnie (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Użyj modułu programu Windows PowerShell, aby wdrożyć poleceń cmdlet (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Poniższe zalecenia należy przestrzegać podczas projektowania poleceń cmdlet, aby zapewnić spójne środowisko użytkownika między przy użyciu poleceń cmdlet i inne polecenia cmdlet. Po znalezieniu wskazówek dotyczących projektu, która ma zastosowanie do konkretnej sytuacji, pamiętaj przyjrzeć się wskazówki dotyczące kodu podobne wskazówki dotyczące.

### <a name="use-only-approved-verbs-rd01"></a>Użyj tylko zatwierdzone czasowniki (RD01)

Zlecenie, określony w atrybucie polecenia Cmdlet muszą pochodzić z rozpoznanym zbiór zleceń dostarczane przez środowisko Windows PowerShell. Nie może być jedną zabronione synonimów. Użyj stałych ciągów, które są definiowane przez następujące wyliczenia, aby określić czasowników poleceń cmdlet:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Aby uzyskać więcej informacji na temat nazw czasownik Zobacz [czasowników poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Użytkownicy potrzebują zestawu nazwy poleceń cmdlet oczekiwanego i prostsze do odnalezienia. Użyj odpowiednie zlecenie, użytkownik może wprowadzić szybkiej oceny, działanie polecenia cmdlet, można łatwo wykryć, możliwości systemu. Na przykład polecenie pobiera listę wszystkich poleceń w systemie, w których nazwy zaczynają się od "start": `get-command start-*`. Używać rzeczowników w poleceń cmdlet do odróżniania poleceń cmdlet z innymi poleceniami cmdlet. Rzeczownikiem wskazuje zasobu, na którym będzie można wykonać operacji. Operacja, sama jest reprezentowana przez zlecenie.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nazwy poleceń cmdlet: Znaki, których nie można używać (RD02)

Po nadaniu nazwy poleceń cmdlet, nie należy używać żadnego z następujących znaków specjalnych.

|Znak|Nazwa|
|---------------|----------|
|#|znak liczby|
|, |Przecinkami|
|()|Nawiasy|
|{}|nawiasy klamrowe|
|[]|nawiasy kwadratowe|
|&|handlowe "i"|
|-|Łącznik **Uwaga:**  Łącznik może służyć do oddzielania zlecenia z rzeczownikiem, ale nie można używać w ramach rzeczownikiem lub zlecenie.|
|/|ukośnik|
|\|Ukośnik odwrotny|
|$|Znak dolara|
|^|Karetki|
|;|Średnikami|
|:|Średnikami|
|"|Podwójny cudzysłów|
|'|Znak pojedynczego cudzysłowu|
|<>|nawiasy kątowe|
|&#124;|kreska pionowa|
|?|znak zapytania|
|@|znak|
|"| kopii znaczników (akcent)|
|*|Gwiazdki|
|%|Znak procentu|
|+|Znak plus|
|=|Znak równości|
|~|Tylda|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nazwy parametrów, których nie można używać (RD03)

Program Windows PowerShell udostępnia wspólny zestaw parametrów do wszystkich poleceń cmdlet, a także dodatkowe parametry, które są dodawane w określonych sytuacjach. Podczas projektowania własnych poleceń cmdlet nie można używać następujących nazw: Upewnij się, debugowania, ErrorAction, ErrorVariable, OutBuffer OutVariable WarningAction, WarningVariable, WhatIf, UseTransaction i szczegółowe informacje. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [typowych nazw parametrów](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Obsługuje żądania potwierdzenia (RD04)

Dla polecenia cmdlet do wykonywania operacji, która modyfikuje systemu, należy wywołać [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody żądania potwierdzenia, a w szczególnych przypadkach należy wywołać [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody. ( [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodę należy wywoływać tylko po [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoda jest wywoływana.)

Aby te wywołania polecenia cmdlet należy określić obsługuje żądania potwierdzenia, ustawiając `SupportsShouldProcess` — słowo kluczowe atrybutu polecenia Cmdlet. Aby uzyskać więcej informacji na temat ustawienie tego atrybutu, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Jeśli polecenie Cmdlet atrybut klasy polecenia cmdlet oznacza, że polecenie cmdlet obsługuje wywołania [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody i polecenia cmdlet nie powiedzie się wywoływania [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody, użytkownik może zmodyfikować system nieoczekiwanie.

Użyj [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodę żadnych modyfikacji systemu. Preferencje użytkownika i `WhatIf` kontrolka parametrów [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody. Z kolei [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wywołanie wykonuje dodatkową kontrolę dla potencjalnie niebezpiecznych modyfikacji. Ta metoda nie są kontrolowane przez żadnych preferencji użytkownika lub `WhatIf` parametru. Jeśli Twojego polecenia cmdlet wywoła [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodę, powinny mieć `Force` parametr, który pomija wywołań do tych dwóch metod i która kontynuuje operację. Jest to ważne, ponieważ zezwala ona na Twojego polecenia cmdlet do użycia w skryptach nieinterakcyjnych i hosty.

W przypadku poleceń cmdlet programu obsługi tych wywołań, użytkownik można określić, czy rzeczywiście należy przeprowadzić akcji. Na przykład [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) wywołania polecenia cmdlet [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodę, zanim przestanie zbiór krytyczne procesy, łącznie z systemem usługi Winlogon, a Programem Spoolsv procesów.

Aby uzyskać więcej informacji na temat obsługi tych metod, zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Obsługa parametru Force interaktywnych sesji (RD05)

Jeśli Twojego polecenia cmdlet jest używana interaktywnie, zawsze podawać parametru Force, aby zastąpić interaktywne akcji, na przykład monitów lub odczytywania wierszy danych wejściowych). Jest to ważne, ponieważ zezwala ona na Twojego polecenia cmdlet do użycia w skryptach nieinterakcyjnych i hosty. Następujące metody może być implementowany przez host interaktywny.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Obiekty danych wyjściowych dokumentów (RD06)

Obiekty, które są zapisywane w potoku korzysta z programu Windows PowerShell. Aby użytkownicy mogą korzystać z obiektów, które są zwracane przez każde polecenie cmdlet należy udokumentować obiekty, które są zwracane, a należy udokumentować członkowie tych zwracanych obiektów służą do.

## <a name="code-guidelines"></a>Wytyczne dotyczące kodu

Należy przestrzegać następujących wytycznych podczas pisania kodu, polecenia cmdlet. Po znalezieniu wytyczne kodu, która ma zastosowanie do danej sytuacji, pamiętaj przyjrzeć się podobne wytycznych dotyczących projektowania.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Pochodzi z polecenia Cmdlet lub skryptu PSCmdlet klasy (RC01)

Polecenie cmdlet musi pochodzić z klasy [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) lub [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy bazowej. Polecenia cmdlet, które pochodzą z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy nie są zależne od środowiska uruchomieniowego programu Windows PowerShell. One można wywołać bezpośrednio z dowolnego języka platformy Microsoft .NET Framework. Polecenia cmdlet, które pochodzą z [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy są zależne od środowiska uruchomieniowego programu Windows PowerShell. W związku z tym są wykonywane w ramach obszaru działania.

Wszystkie klasy polecenia cmdlet, które należy zaimplementować muszą być publiczne klasy. Aby uzyskać więcej informacji na temat klasy te polecenia cmdlet, zobacz [Przegląd polecenia Cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Określ atrybut polecenia Cmdlet (RC02)

Dla polecenia cmdlet, aby zostały rozpoznane przez program Windows PowerShell jego klasy .NET Framework musi posiadać atrybut polecenia Cmdlet. Ten atrybut określa poniższe funkcje polecenia cmdlet.

- Para czasownik i rzeczownik, który identyfikuje polecenia cmdlet.

- Domyślny zestaw parametrów jest używany, jeśli określono wiele zestawów parametrów. Domyślny zestaw parametrów jest używany, gdy programu Windows PowerShell nie ma wystarczających informacji, aby określić parametr, który jest skonfigurowany do używania.

- Wskazuje, czy polecenie cmdlet obsługuje wywołania [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metody. Ta metoda wyświetla komunikat z potwierdzeniem dla użytkownika przed polecenia cmdlet sprawia, że zmiany do systemu. Aby uzyskać więcej informacji na temat sposobu potwierdzenia żądań zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

- Wskazuje poziom wpływu (lub ważności) akcję skojarzoną z komunikat potwierdzenia. W większości przypadków można używana domyślna wartość średnia. Aby uzyskać więcej informacji na temat wpływu żądania potwierdzenia, które są wyświetlane użytkownikowi poziom wpływu zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md).

Aby uzyskać więcej informacji o tym, jak zadeklarować atrybut polecenia cmdlet, zobacz [deklaracji CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Zastąp dane wejściowe przetwarzania metody (RC03)

Polecenia cmdlet do wzięcia udziału w środowisku Windows PowerShell, musi ono przesłonić co najmniej jedną z następujących *danych wejściowych metody przetwarzania*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ta metoda jest wywoływana jeden raz i służy do zapewnienia funkcji przetwarzania wstępnego.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ta metoda jest wywoływana wiele razy i jest używany do zapewnienia funkcji przez rekordami.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ta metoda jest wywoływana jeden raz i służy do zapewnienia funkcji przetwarzania końcowego.

### <a name="specify-the-outputtype-attribute-rc04"></a>Określ atrybut OutputType (RC04)

Atrybutu OutputType (zostanie wprowadzony w programie Windows PowerShell 2.0) określa typ .NET Framework, która Twojego polecenia cmdlet zwraca do potoku. Określając typ danych wyjściowych poleceń cmdlet należy obiektów zwróconych przez Twojego polecenia cmdlet mogą szybciej odnajdywać przez inne polecenia cmdlet. Aby uzyskać więcej informacji na temat urządzanie klasy polecenia cmdlet, za pomocą tego atrybutu, zobacz [deklaracji atrybutu OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Nie będzie przechowywała dojścia do obiektów danych wyjściowych (RC05)

Twoje polecenie cmdlet nie powinien zachować wszystkie dojścia do obiektów, które są przekazywane do [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody. Te obiekty są przekazywane do polecenia cmdlet dalej w potoku lub są one używane przez skrypt. Aby zachować dojścia do obiektów, dwie jednostki będą właścicielami każdego obiektu, który jest przyczyną błędów.

### <a name="handle-errors-robustly-rc06"></a>Obsługa błędów niezawodnie (RC06)

Środowisko administrowania natury wykrywa i sprawia, że ważne zmiany do systemu, który w przypadku administrowania. Dlatego jest istotne, poleceń cmdlet poprawnie obsługiwać błędy. Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [raportowanie błędów programu Windows PowerShell](./error-reporting-concepts.md).

- Gdy błąd uniemożliwia kontynuowanie przetworzyć żadnych więcej rekordów polecenia cmdlet, jest błąd powodujący zakończenie. Polecenia cmdlet należy wywołać [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodę, która odwołuje się do [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu. Jeśli wyjątek nie zostanie przechwycony przez polecenie cmdlet, programu Windows PowerShell środowisko uruchomieniowe zgłasza błąd powodujący zakończenie, która zawiera mniej informacji.

- Niepowodujące błędu, który nie zatrzymuje operację na następnej rekord, który pochodzi z potoku (na przykład rekord produkowane przez inny proces), polecenia cmdlet należy wywołać [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, która odwołuje się do [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu. Przykładem jest błąd niepowodujący jest błąd, który występuje, gdy nie można zatrzymać usługi określonego procesu. Wywoływanie [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoda umożliwia użytkownikowi spójnie wykonywania działań zleconych i przechowywania informacji dla określonej akcji, które się nie powieść. Twojego polecenia cmdlet powinny obsługiwać każdego wybranego rekordu jako niezależne, jak to możliwe.

- [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt, który odwołuje się do niej [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) i [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody wymaga wyjątek podstawą. Po określeniu wyjątek do użycia, postępuj zgodnie z wytycznymi projektowania .NET Framework. Jeśli błąd semantycznie jest taka sama jak istniejące wyjątek, użyj tego wyjątku lub pochodzi od tego wyjątku. W przeciwnym razie pochodzić nowy wyjątek lub hierarchia wyjątków bezpośrednio z [System.Exception](/dotnet/api/System.Exception) typu.

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu wymaga również kategoria błędu, który grupuje błędy dla użytkownika. Użytkownik może wyświetlić błędy, w oparciu o kategorię, ustawiając wartość `$ErrorView` CategoryView zmiennej powłoki. Możliwe kategorie są definiowane przez [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) wyliczenia.

- Jeśli polecenie cmdlet tworzy nowy wątek i kod, który działa w tym wątku zawiera nieobsługiwany wyjątek, programu Windows PowerShell nie będzie przechwytywać błąd i zakończy proces.

- Jeśli obiekt ma kod w destruktorze, który powoduje, że nieobsługiwany wyjątek, programu Windows PowerShell nie będzie przechwytywać błąd i zakończy proces. Również dzieje się tak, jeśli obiekt nie wywoła metody usuwania, które powodują nieobsługiwany wyjątek.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Użyj modułu programu Windows PowerShell, aby wdrożyć poleceń cmdlet (RC07)

Utwórz moduł programu Windows PowerShell w pakietach i wdrażać poleceń cmdlet. Obsługa modułów został wprowadzony w programie Windows PowerShell 2.0. Można użyć zestawów zawierających klasy Twojego polecenia cmdlet bezpośrednio jako pliki binarne modułu (jest to bardzo przydatne podczas testowania poleceń cmdlet), lub można utworzyć manifest modułu, który odwołuje się do zestawów polecenia cmdlet. (Można również dodać istniejące zestawy przystawki w przypadku korzystania z modułów.) Aby uzyskać więcej informacji na temat modułów, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące programowania zalecamy](./strongly-encouraged-development-guidelines.md)

[Wskazówki dotyczące porad dotyczących programowania](./advisory-development-guidelines.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
