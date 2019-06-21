---
title: Pomoc oparta na komentarzach słowa kluczowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301529"
---
# <a name="comment-based-help-keywords"></a>Słowa kluczowe pomocy opartej na komentarzach

W tym temacie wymieniono i opisano słów kluczowych w Pomoc oparta na komentarz.

## <a name="keywords-in-comment-based-help"></a>Słowa kluczowe w oparta na komentarzach pomocy

Poniżej przedstawiono prawidłowe keywords Pomoc oparta na komentarzach. Są one wymienione w kolejności, w którym zwykle pojawiają się w temacie pomocy wraz z ich przeznaczenie. Tych słów kluczowych mogą być wyświetlane w dowolnej kolejności w Pomoc oparta na komentarz, a nie jest rozróżniana wielkość liter.

Należy pamiętać, że `.ExternalHelp` — słowo kluczowe mają pierwszeństwo przed wszystkie inne słowa kluczowe Pomoc oparta na komentarz. Gdy `.ExternalHelp` jest obecny, [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) polecenie cmdlet nie wyświetla Pomoc oparta na komentarz, nawet wtedy, gdy nie można odnaleźć pliku pomocy, który odpowiada wartość słowa kluczowego.

`.Synopsis` Krótki opis funkcji lub skrypcie. This — słowo kluczowe może służyć tylko raz w każdym temacie.

`.Description` Szczegółowy opis funkcji lub skrypcie. This — słowo kluczowe może służyć tylko raz w każdym temacie.

`.Parameter` *\<Nazwa parametru >* opis parametru. Możesz uwzględnić `.Parameter` — słowo kluczowe dla każdego parametru w funkcji lub skryptu.

`.Parameter` Słów kluczowych mogą być wyświetlane w dowolnej kolejności, w bloku komentarza, ale kolejność wyświetlania parametrów w `Param` instrukcję lub funkcję deklaracja określa kolejność wyświetlania parametrów w temacie Pomocy. Aby zmienić kolejność parametrów w temacie pomocy, zmienić kolejność parametrów w `Param` deklaracji instrukcję lub funkcję.

Można również określić opis parametru, umieszczając komentarz w `Param` instrukcję tuż przed parametru nazwę zmiennej. Jeśli używasz zarówno `Param` instrukcji komentarza i `.Parameter` — słowo kluczowe, opis, skojarzone z `.Parameter` słowo kluczowe jest używane i `Param` instrukcji komentarza jest ignorowane.

`.Example` Przykładowe polecenie używa funkcji lub skryptu i, opcjonalnie, przykładowe dane wyjściowe i opis. This — słowo kluczowe należy powtórzyć dla każdego przykładu.

`.Inputs` Microsoft .NET Framework typy obiektów, które mogą być przesyłane potokiem do funkcji lub skryptu. Może również zawierać opis obiektów danych wejściowych.

`.Outputs` Typ .NET Framework, które polecenie cmdlet zwraca obiekty. Może również zawierać opis zwracanych obiektów.

`.Notes` Dodatkowe informacje dotyczące funkcji lub skrypcie.

`.Link` Nazwa powiązanych tematów. This — słowo kluczowe należy powtórzyć dla każdego temat pokrewny. Ta zawartość jest wyświetlana w sekcji linki powiązane tematu Pomocy.

`.Link` Zawartości — słowo kluczowe może również obejmować zasobów identyfikator URI (Uniform) do wersji tego samego tematu Pomocy online. Wersja online zostanie otwarty, gdy używasz `Online` parametr Get-Help. Identyfikator URI musi zaczynać się od "http" lub "https".

`.Component` Technologia lub funkcja, który korzysta z funkcji lub skryptu lub do którego jest powiązany. Ta zawartość jest wyświetlany, gdy polecenie Get-Help zawiera `Component` parametr Get-Help.

`.Role` Rola do tematu Pomocy. Ta zawartość jest wyświetlany, gdy polecenie Get-Help zawiera `Role` parametr Get-Help.

`.Functionality` Zamierzonym użyciem funkcji. Ta zawartość jest wyświetlany, gdy polecenie Get-Help zawiera `Functionality` parametr Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Przekierowuje do tematu pomocy dla określonego polecenia. Możesz przekierować użytkowników do dowolnego tematu pomocy, w tym tematy pomocy dla funkcji, skryptów, polecenia cmdlet lub dostawcy.

`.ForwardHelpCategory` `<Category>` Określa kategoria pomocy elementu ForwardHelpTargetName. Prawidłowe wartości to: Alias, polecenie Cmdlet, HelpFile —, funkcji, dostawcy, ogólne, — często zadawane pytania, słownik, ScriptCommand, ExternalScript, filtr lub wszystkie. Użyj słowa kluczowego w celu uniknięcia konfliktów w przypadku poleceń o takiej samej nazwie.

`.RemoteHelpRunspace` `<PSSession-variable>` Określa sesji, który zawiera temat pomocy. Wprowadź zmienną, która zawiera sesji PSSession. This — słowo kluczowe jest używany przez `Export-PSSession` polecenia cmdlet, aby znaleźć tematy pomocy dla poleceń wyeksportowany.

`.ExternalHelp` `<XML Help File>` Określa ścieżkę i/lub nazwę pliku pomocy oparty na składni XML dla skryptu lub funkcji.

`.ExternalHelp` Informuje — słowo kluczowe [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) polecenia cmdlet, aby uzyskać pomoc dotyczącą skryptu lub funkcji w pliku oparte na języku XML. **. ExternalHelp** — słowo kluczowe jest wymagany w przypadku używania pliku pomocy oparty na składni XML dla skryptu lub funkcji. Bez tego `Get-Help` nie znajdzie pliku pomocy dla funkcji lub skryptu.

`.ExternalHelp` — Słowo kluczowe mają pierwszeństwo przed wszystkie inne słowa kluczowe Pomoc oparta na komentarz. Gdy `.ExternalHelp` jest obecny, [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) polecenie cmdlet nie wyświetla Pomoc oparta na komentarz, nawet wtedy, gdy nie można odnaleźć pliku pomocy, który odpowiada wartość słowa kluczowego.

Gdy funkcja jest eksportowana przez moduł skryptu, wartość `.ExternalHelp` powinna być nazwą pliku bez ścieżki. `Get-Help` szuka pliku w podkatalogu specyficzne dla ustawień regionalnych katalog modułu. Nie ma żadnych wymagań dla nazwy pliku, ale najlepszym rozwiązaniem jest użycie następujących format nazwy pliku: `<ScriptModule>.psm1-help.xml`.

Jeśli funkcja nie jest skojarzony z modułem, obejmują ścieżkę i nazwę pliku w wartości **. ExternalHelp** — słowo kluczowe. Jeśli określona ścieżka do pliku XML zawiera podkatalogi interfejsu użytkownika specyficznych dla kultury, `Get-Help` wyszukuje w podkatalogach cyklicznie dla pliku XML o nazwie skryptu lub funkcji, zgodnie z języka rezerwowego standardy ustanowione dla Windows, podobnie jak wykonuje wszystkie tematy pomocy opartych na języku XML.

Aby uzyskać więcej informacji dotyczących formatu plików oparty na standardzie XML pomóc pomocy polecenia cmdlet, zobacz [pomocy polecenia Cmdlet programu PowerShell Windows zapisywanie](./writing-help-for-windows-powershell-cmdlets.md).