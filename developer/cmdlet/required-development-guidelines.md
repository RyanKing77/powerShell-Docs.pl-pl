---
title: Wymagane wskazówki dotyczące programowania | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986679"
---
# <a name="required-development-guidelines"></a>Wskazówki dotyczące projektowania — użycie wymagane

Podczas pisania poleceń cmdlet należy przestrzegać następujących wytycznych. Są one podzielone na wytyczne dotyczące projektowania poleceń cmdlet i wytycznych dotyczących pisania kodu poleceń cmdlet. Jeśli nie przestrzegasz tych wytycznych, polecenia cmdlet mogą zakończyć się niepowodzeniem, a użytkownicy mogą mieć słabe środowisko, gdy używają poleceń cmdlet.

## <a name="in-this-topic"></a>W tym temacie

### <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

- [Używaj tylko zatwierdzonych czasowników (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nazwy poleceń cmdlet: Znaki, których nie można użyć (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nazwy parametrów, których nie można użyć (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Obsługa żądań potwierdzenia (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Parametr Force obsługi dla sesji interakcyjnych (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Obiekty wyjściowe dokumentu (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Wskazówki dotyczące kodu

- [Pochodne z klas poleceń cmdlet lub PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Określ atrybut cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Zastąp metodę przetwarzania danych wejściowych (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Określ atrybut OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Nie zachowuj dojść do obiektów wyjściowych (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Niezawodna obsługa błędów (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Wdrażanie poleceń cmdlet przy użyciu modułu programu Windows PowerShell (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Wytyczne dotyczące projektowania

Podczas projektowania poleceń cmdlet w celu zapewnienia spójnego środowiska użytkownika między użyciem poleceń cmdlet i innych poleceń cmdlet należy przestrzegać następujących wytycznych. Po znalezieniu wytycznych dotyczących projektowania, które dotyczą danej sytuacji, należy zapoznać się z wytycznymi dotyczącymi kodu dotyczącymi podobnych wytycznych.

### <a name="use-only-approved-verbs-rd01"></a>Używaj tylko zatwierdzonych czasowników (RD01)

Czasownik określony w atrybucie polecenia cmdlet musi pochodzić z rozpoznanego zestawu czasowników udostępnianych przez program Windows PowerShell. Nie może być jednym z zabronionych synonimów. Użyj stałych ciągów, które są zdefiniowane przez następujące wyliczenia, aby określić czasowniki poleceń cmdlet:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Aby uzyskać więcej informacji na temat zatwierdzonych nazw zleceń, zobacz [czasowniki poleceń cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Użytkownicy potrzebują zestawu odnajdywania i oczekiwanych nazw poleceń cmdlet. Użyj odpowiedniego zlecenia, aby użytkownik mógł szybko ocenić działanie polecenia cmdlet i łatwo poznać możliwości systemu. Na przykład następujące polecenie wiersza polecenia pobiera listę wszystkich poleceń w systemie, których nazwy zaczynają się od "Start": `get-command start-*`. Użyj rzeczowników w poleceniach cmdlet, aby odróżnić polecenia cmdlet od innych poleceń cmdlet. Rzeczownik wskazuje zasób, na którym operacja zostanie wykonana. Sama operacja jest reprezentowana przez zlecenie.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nazwy poleceń cmdlet: Znaki, których nie można użyć (RD02)

Podczas nazwy poleceń cmdlet nie należy używać żadnego z następujących znaków specjalnych.

|Znak|Nazwa|
|---------------|----------|
|#|znak numeru|
|,|pliku|
|()|nawiasów|
|{}|nawiasy klamrowe|
|[]|nawias|
|&|znaku|
|-|**Uwaga dotycząca** łącznika:  Łącznik może służyć do oddzielania czasownika od rzeczownika, ale nie może być używany w rzeczowniku lub w czasowniku.|
|/|znak ukośnika|
|\\| ukośnik odwrotny|
|$|znak dolara|
|^|użyciu|
|;|Dziel|
|:|średnikami|
|"|podwójny cudzysłów|
|'|znak pojedynczego cudzysłowu|
|<>|nawiasy kątowe|
|&#124;|pionowy pasek|
|?|znak zapytania|
|@|przy podpisaniu|
|`|Wróć do osi (akcent słaby)|
|*|znaku|
|%|znak procentu|
|+|znak plus|
|=|znak równości|
|~|tyld|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nazwy parametrów, których nie można użyć (RD03)

Środowisko Windows PowerShell udostępnia wspólny zestaw parametrów dla wszystkich poleceń cmdlet oraz dodatkowe parametry, które są dodawane w określonych sytuacjach. Podczas projektowania własnych poleceń cmdlet nie można używać następujących nazw: Confirm, Debug, ErrorAction, ErrorVariable, subbuffer, subvariable, WarningAction, WarningVariable, WhatIf, UseTransaction i verbose. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Common](./common-parameter-names.md)Parameters Names.

### <a name="support-confirmation-requests-rd04"></a>Obsługa żądań potwierdzenia (RD04)

W przypadku poleceń cmdlet, które wykonują operację modyfikującą system, powinny wywołać metodę [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , aby zażądać potwierdzenia, a w szczególnych przypadkach wywołać [ Metoda System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . (Metoda [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) powinna być wywoływana tylko po wywołaniu metody [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ).

Aby wykonać te wywołania, polecenie cmdlet musi określić, że obsługuje żądania potwierdzenia przez ustawienie `SupportsShouldProcess` słowa kluczowego dla atrybutu cmdlet. Aby uzyskać więcej informacji na temat ustawiania tego atrybutu, zobacz [polecenie cmdlet Attribute deklaracji](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Jeśli atrybut cmdlet klasy cmdlet wskazuje, że polecenie cmdlet obsługuje wywołania do metody [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , a polecenie cmdlet nie może wykonać wywołania [ System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Metoda, użytkownik może nieoczekiwanie modyfikować system.

Użyj metody [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) do modyfikacji systemu. Preferencja użytkownika i `WhatIf` parametr sterują metodą [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Z kolei wywołanie metody [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wykonuje dodatkowe sprawdzenie pod kątem potencjalnie niebezpiecznych modyfikacji. Ta metoda nie jest kontrolowana przez żadną preferencję użytkownika `WhatIf` ani parametr. Jeśli polecenie cmdlet wywołuje metodę [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , powinna mieć `Force` parametr, który pomija wywołania tych dwóch metod, i które kontynuuje wykonywanie operacji. Jest to ważne, ponieważ umożliwia używanie polecenia cmdlet w skryptach i hostach, które nie są interaktywne.

Jeśli polecenia cmdlet obsługują te wywołania, użytkownik może określić, czy akcja powinna być faktycznie wykonywana. Na przykład polecenie cmdlet [stop-Process](/powershell/module/microsoft.powershell.management/stop-process) wywołuje metodę [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) przed zatrzymaniem zestawu krytycznych procesów, w tym procesów system, Winlogon i Spoolsv.

Aby uzyskać więcej informacji na temat obsługi tych metod, zobacz [żądanie potwierdzenia](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Parametr Force obsługi dla sesji interakcyjnych (RD05)

Jeśli polecenie cmdlet jest używane interaktywnie, należy zawsze dostarczyć parametr Force, aby przesłonić akcje interaktywne, takie jak monity lub odczytywanie wierszy danych wejściowych. Jest to ważne, ponieważ umożliwia używanie polecenia cmdlet w skryptach i hostach, które nie są interaktywne. Host interaktywny może implementować następujące metody.

- [System. Management. Automation. host. PSHostUserInterface. Prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Obiekty wyjściowe dokumentu (RD06)

Program Windows PowerShell korzysta z obiektów, które są zapisywane w potoku. Aby użytkownicy mogli korzystać z obiektów, które są zwracane przez poszczególne polecenia cmdlet, należy udokumentować obiekty, które są zwracane, i należy udokumentować, do czego są używane elementy zwracanych obiektów.

## <a name="code-guidelines"></a>Wskazówki dotyczące kodu

Podczas pisania kodu polecenia cmdlet należy przestrzegać następujących wytycznych. Po znalezieniu wytycznych dotyczących kodu, które dotyczą danej sytuacji, należy zapoznać się z zaleceniami dotyczącymi projektowania, aby poznać podobne wskazówki.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Pochodne z klas poleceń cmdlet lub PSCmdlet (RC01)

Polecenie cmdlet musi pochodzić od klasy bazowej [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) lub [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Polecenia cmdlet, które pochodzą z klasy [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) , nie są zależne od środowiska uruchomieniowego programu Windows PowerShell. Można je wywołać bezpośrednio z dowolnego języka Microsoft .NET Framework. Polecenia cmdlet, które pochodzą z klasy [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , są zależne od środowiska uruchomieniowego programu Windows PowerShell. W związku z tym są one wykonywane w obszarze działania.

Wszystkie klasy poleceń cmdlet, które są implementowane, muszą być klasami publicznymi. Aby uzyskać więcej informacji na temat tych klas poleceń cmdlet, zobacz [polecenie cmdlet przegląd](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Określ atrybut cmdlet (RC02)

Aby można było rozpoznać polecenie cmdlet w programie Windows PowerShell, jego Klasa .NET Framework musi być uzupełniona atrybutem cmdlet. Ten atrybut określa następujące funkcje polecenia cmdlet.

- Para czasownik-i-rzeczownik, która identyfikuje polecenie cmdlet.

- Domyślny zestaw parametrów, który jest używany, gdy określono wiele zestawów parametrów. Domyślny zestaw parametrów jest używany, gdy program Windows PowerShell nie ma wystarczających informacji, aby określić, który parametr ma być używany.

- Wskazuje, czy polecenie cmdlet obsługuje wywołania metody [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Ta metoda wyświetla komunikat z potwierdzeniem, zanim polecenie cmdlet dokona zmiany w systemie. Aby uzyskać więcej informacji na temat sposobu wykonywania żądań potwierdzenia, zobacz [żądanie potwierdzenia](./requesting-confirmation-from-cmdlets.md).

- Wskaż poziom wpływu (lub ważność) akcji skojarzonej z komunikatem potwierdzającym. W większości przypadków należy użyć wartości domyślnej średniej. Aby uzyskać więcej informacji o tym, jak poziom wpływu wpływa na żądania potwierdzenia, które są wyświetlane użytkownikowi, zobacz [żądanie potwierdzenia](./requesting-confirmation-from-cmdlets.md).

Aby uzyskać więcej informacji na temat sposobu deklarowania atrybutu polecenia cmdlet, zobacz [polecenie cmdletattribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Zastąp metodę przetwarzania danych wejściowych (RC03)

Aby polecenie cmdlet uczestniczyło w środowisku Windows PowerShell, należy zastąpić co najmniej jedną z następujących *metod przetwarzania danych wejściowych*.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ta metoda jest wywoływana jednokrotnie i służy do udostępniania funkcji wstępnego przetwarzania.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ta metoda jest wywoływana wiele razy i służy do udostępniania funkcji rejestrowania przez rekord.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Metoda ta jest wywoływana jednokrotnie i służy do zapewnienia funkcji przetwarzania końcowego.

### <a name="specify-the-outputtype-attribute-rc04"></a>Określ atrybut OutputType (RC04)

Atrybut OutputType (wprowadzony w programie Windows PowerShell 2,0) określa typ .NET Framework, który powróci do potoku przez polecenie cmdlet. Określając typ danych wyjściowych poleceń cmdlet, można łatwiej odnajdować obiekty zwracane przez polecenie cmdlet. Aby uzyskać więcej informacji na temat dekorowania nazwy klasy poleceń cmdlet z tym atrybutem, zobacz [deklaracji atrybutu OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Nie zachowuj dojść do obiektów wyjściowych (RC05)

Polecenie cmdlet nie powinno zachować żadnych dojść do obiektów, które są przesyłane do metody [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Te obiekty są przenoszone do następnego polecenia cmdlet w potoku lub są używane przez skrypt. Jeśli zachowasz uchwyty do obiektów, dwie jednostki będą być właścicielami poszczególnych obiektów, co powoduje błędy.

### <a name="handle-errors-robustly-rc06"></a>Niezawodna obsługa błędów (RC06)

Środowisko administracyjne z własnej próby wykrywa i wprowadza ważne zmiany w systemie, który administrujesz. W związku z tym ważne jest, aby polecenia cmdlet prawidłowo obsługiwały błędy. Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [raportowanie błędów programu Windows PowerShell](./error-reporting-concepts.md).

- Gdy błąd uniemożliwi przetworzenie kolejnych rekordów przez polecenie cmdlet, jest to błąd powodujący przerwanie. Polecenie cmdlet musi wywołać metodę [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) , która odwołuje się do obiektu [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Jeśli nie przechwycono wyjątku przez polecenie cmdlet, samo środowisko uruchomieniowe programu Windows PowerShell zgłasza błąd kończący, który zawiera mniej informacji.

- W przypadku błędu niekończącego, który nie zatrzymuje operacji na następnym rekordzie, który pochodzi z potoku (na przykład rekordu utworzonego przez inny proces), polecenie cmdlet musi wywołać metodę [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , która odwołuje się do obiektu [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Przykładem błędu niekończącego jest błąd występujący w przypadku niepowodzenia zatrzymania określonego procesu. Wywołanie metody [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) umożliwia użytkownikowi spójne wykonywanie żądanych akcji i przechowywanie informacji dla określonych akcji, które nie powiodły się. Polecenie cmdlet powinno obsługiwać każdy rekord niezależnie od tego, jak to możliwe.

- Obiekt [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) , do którego odwołuje się [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) i [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , wymaga elementu wyjątek w jego rdzeniu. Postępuj zgodnie z .NET Framework wytycznych dotyczących projektowania podczas określania wyjątku do użycia. Jeśli błąd jest semantycznie taki sam jak istniejący wyjątek, użyj tego wyjątku lub pochodzi z tego wyjątku. W przeciwnym razie Utwórz nowy wyjątek lub hierarchię wyjątków bezpośrednio z typu [System. Exception](/dotnet/api/System.Exception) .

Obiekt [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) wymaga również kategorii błędów, która grupuje błędy użytkownika. Użytkownik może wyświetlić błędy w oparciu o kategorię, ustawiając wartość `$ErrorView` zmiennej Shell na CategoryView. Możliwe kategorie są definiowane przez Wyliczenie [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Jeśli polecenie cmdlet tworzy nowy wątek i jeśli kod, który jest uruchomiony w tym wątku zgłasza nieobsługiwany wyjątek, program Windows PowerShell nie przechwytuje tego błędu i zakończy proces.

- Jeśli obiekt ma w swoim destruktorze kod, który powoduje nieobsługiwany wyjątek, program Windows PowerShell nie przechwytuje błędu i zakończy proces. Występuje to również, gdy obiekt wywołuje metody Dispose, które powodują nieobsługiwany wyjątek.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Wdrażanie poleceń cmdlet przy użyciu modułu programu Windows PowerShell (RC07)

Utwórz moduł programu Windows PowerShell umożliwiający pakowanie i wdrażanie poleceń cmdlet. Obsługa modułów jest wprowadzana w programie Windows PowerShell 2,0. Zestawów zawierających klasy poleceń cmdlet można używać bezpośrednio jako plików modułów binarnych (jest to bardzo przydatne podczas testowania poleceń cmdlet) lub można utworzyć manifest modułu, który odwołuje się do zestawów poleceń cmdlet. (W przypadku korzystania z modułów można także dodać istniejące zestawy przystawek). Aby uzyskać więcej informacji o modułach, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zobacz też

[Zdecydowanie zalecane wskazówki dotyczące programowania](./strongly-encouraged-development-guidelines.md)

[Wytyczne dotyczące programowania](./advisory-development-guidelines.md)

[Pisanie polecenia cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
