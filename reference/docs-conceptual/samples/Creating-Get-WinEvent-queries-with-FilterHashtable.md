---
ms.date: 3/18/2019
title: Tworzenie zapytań polecenia Get-WinEvent za pomocą parametru FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984225"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Tworzenie zapytań polecenia Get-WinEvent za pomocą parametru FilterHashtable

Do odczytu, oryginalnym czerwca 3 2014 r. **Scripting Guy** blog post, zobacz [FilterHashTable korzystanie w dzienniku zdarzeń filtr przy użyciu programu PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

W tym artykule znajduje się fragment, oryginalnym wpisu w blogu i wyjaśnia, jak używać `Get-WinEvent` polecenia cmdlet **FilterHashtable** parametru, aby filtrować dzienników zdarzeń. W programie PowerShell `Get-WinEvent` polecenie cmdlet jest zaawansowaną metodą do filtrowania zdarzeń Windows i dzienniki diagnostyczne. Zwiększa wydajność, kiedy `Get-WinEvent` zapytanie używa **FilterHashtable** parametru.

Podczas pracy z dziennikami zdarzeń dużych, nie jest efektywne wysyłanie obiektów w dół potoku w celu `Where-Object` polecenia. Przed program PowerShell 6 `Get-EventLog` polecenia cmdlet została inną opcję, aby pobrać dane dziennika. Na przykład poniższe polecenia są nieefektywne filtru **Microsoft-Windows-defragmentowania** dzienników:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

Następujące polecenie używa tablicy skrótów, które poprawia wydajność:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Wpisy na blogu dotyczące wyliczenia

W tym artykule przedstawiono informacje o sposobie używania wartości wyliczane w tabeli wyznaczania wartości skrótu. Aby uzyskać więcej informacji na temat wyliczania przeczytaj **Scripting Guy** wpisów w blogu. Aby utworzyć funkcję, która zwraca wartości wyliczenia, zobacz [wyliczeń i wartości](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Aby uzyskać więcej informacji, zobacz [Scripting Guy szeregu blogu wpisy dotyczące wyliczenia](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Hash, pary klucz/wartość tabeli

Aby utworzyć wydajne zapytania, użyj `Get-WinEvent` polecenia cmdlet z **FilterHashtable** parametru.
**FilterHashtable** jako filtr, aby uzyskać konkretne informacje z dzienników zdarzeń Windows akceptuje tabelę mieszania. Tabela skrótu używa **klucz/wartość** pary. Aby uzyskać więcej informacji o tabelach skrótów, zobacz [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Jeśli **klucz/wartość** pary znajdują się na tym samym wierszu, muszą być rozdzielone średnikami. Jeśli każda **klucz/wartość** pary znajduje się w osobnym wierszu, średnik nie jest wymagane. Na przykład, w tym artykule umieszcza **klucz/wartość** pary w osobnych wierszach, a nie Użyj średników.

W tym przykładzie użyto kilka **FilterHashtable** parametru **klucz/wartość** pary. Ukończone zapytanie zawiera **Nazwa_dziennika**, **ProviderName**, **słowa kluczowe**, **identyfikator**, i **poziom**.

Zaakceptowane **klucz/wartość** pary są wyświetlane w poniższej tabeli i znajdują się w dokumentacji dotyczącej [polecenia Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parametr.

W poniższej tabeli przedstawiono nazwy kluczy, typy danych, i czy symbole wieloznaczne są akceptowane wartości danych.

| Nazwa klucza     | Typ danych wartości    | Akceptuje symbole wieloznaczne? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Tak |
| ProviderName | `<String[]>`       | Tak |
| Ścieżka         | `<String[]>`       | Nie  |
| słowa kluczowe     | `<Long[]>`         | Nie  |
| Identyfikator           | `<Int32[]>`        | Nie  |
| Poziom        | `<Int32[]>`        | Nie  |
| Godzina rozpoczęcia    | `<DateTime>`       | Nie  |
| Czas zakończenia      | `<DateTime>`       | Nie  |
| Identyfikator użytkownika       | `<SID>`            | Nie  |
| Dane         | `<String[]>`       | Nie  |
| *            | `<String[]>`       | Nie  |

## <a name="building-a-query-with-a-hash-table"></a>Tworzenie zapytań przy użyciu tablicy skrótów

Aby zweryfikować wyniki i rozwiązywanie problemów, ułatwia tworzenie tabeli mieszania, jeden **klucz/wartość** pary w danym momencie. Zapytanie pobiera dane z **aplikacji** dziennika. Tabela skrótu jest odpowiednikiem `Get-WinEvent –LogName Application`.

Aby rozpocząć, Utwórz `Get-WinEvent` zapytania. Użyj **FilterHashtable** parametru **klucz/wartość** parowanie klucz, **Nazwa_dziennika**i wartość, **aplikacji**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Kontynuować tworzenie tabeli wyznaczania wartości skrótu z **ProviderName** klucza. **ProviderName** to nazwa, która pojawia się w **źródła** pole **Podgląd zdarzeń Windows**. Na przykład **środowiska uruchomieniowego .NET** na następującym zrzucie ekranu:

![Obraz podglądu zdarzeń Windows źródeł.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, ** ProviderName i wartość, **środowiska uruchomieniowego .NET**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Jeśli zapytanie musi pobrać dane z dzienników zdarzeń zarchiwizowanych, użyj **ścieżki** klucza. **Ścieżki** wartość określa pełną ścieżkę do pliku dziennika. Aby uzyskać więcej informacji, zobacz **Scripting Guy** wpis w blogu [Użyj programu PowerShell można przeanalizować zapisane dzienniki zdarzeń błędów](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Przy użyciu wartości wyliczane w tabeli wyznaczania wartości skrótu

**Słowa kluczowe** jest kluczowi w tabeli wyznaczania wartości skrótu. **Słowa kluczowe** — typ danych jest tablicą `[long]` typ, który przechowuje dużą liczbą wartości. Użyj następującego polecenia, aby znaleźć wartość maksymalna `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Aby uzyskać **słowa kluczowe** klucza, programu PowerShell używa wielu, nie ciąg znaków takich jak **zabezpieczeń**. **Podgląd zdarzeń Windows** Wyświetla **słowa kluczowe** jako ciągi, ale są one wartości wyliczenia. W tabeli wyznaczania wartości skrótu, jeśli używasz **słowa kluczowe** klucza z wartością ciągu, jest wyświetlany komunikat o błędzie.

Otwórz **Podgląd zdarzeń Windows** i **akcje** okienku kliknij **Filtruj bieżący dziennik**.
**Słowa kluczowe** menu rozwijane wyświetli dostępne słów kluczowych, jak pokazano na poniższym zrzucie ekranu:

![Obraz podglądu zdarzeń Windows słów kluczowych.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Użyj następującego polecenia, aby wyświetlić `StandardEventKeywords` nazwy właściwości.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Wartości wyliczane są udokumentowane w artykule **.NET Framework**. Aby uzyskać więcej informacji, zobacz [wyliczenie StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

**Słowa kluczowe** nazwy i wartości wyliczane są następujące:

| Nazwa             |  Wartość            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Brak             | 0                 |

Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, **słowa kluczowe**i **EventLogClassic** wartość wyliczenia **36028797018963968** .

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Wartość statyczna właściwość słowa kluczowe (opcjonalnie)

**Słowa kluczowe** wyliczenia klucza, ale można użyć nazwy właściwości statycznej w zapytaniu tabeli wyznaczania wartości skrótu.
Zamiast używania zwracanego ciągu, nazwa właściwości musi zostać skonwertowany do wartości z **Value__** właściwości.

Na przykład, poniższy skrypt **Value__** właściwości.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtrowanie wg identyfikatora zdarzenia

Aby uzyskać bardziej szczegółowe dane, wyniki zapytania są filtrowane według **identyfikator zdarzenia**. **Identyfikator zdarzenia** odwołuje się do tabeli mieszania jako klucz **identyfikator** , a wartość jest konkretnym **identyfikator zdarzenia**. **Podgląd zdarzeń Windows** Wyświetla **identyfikator zdarzenia**. W tym przykładzie użyto **1023 identyfikator zdarzenia**.

Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, **identyfikator** i wartości, **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtrowanie według poziomu

Aby dodatkowo doprecyzować wyniki i zawierają tylko te zdarzenia, które są błędy, należy użyć **poziom** klucza.
**Podgląd zdarzeń Windows** Wyświetla **poziom** jako wartości ciągu, ale są one wartości wyliczenia. W tabeli wyznaczania wartości skrótu, jeśli używasz **poziom** klucza z wartością ciągu, jest wyświetlany komunikat o błędzie.

**Poziom** zawiera wartości, takie jak **błąd**, **ostrzeżenie**, lub **komunikat o charakterze informacyjnym**. Użyj następującego polecenia, aby wyświetlić `StandardEventLevel` nazwy właściwości.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Wartości wyliczane są udokumentowane w artykule **.NET Framework**. Aby uzyskać więcej informacji, zobacz [wyliczenie StandardEventLevel](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

**Poziom** nazwy klucza i wartości wyliczane są następujące:

| Nazwa           | Wartość |
| -------------- | ----- |
| Pełny        |   5   |
| Informacyjny  |   4   |
| Ostrzeżenie        |   3   |
| Błąd          |   2   |
| Krytyczne       |   1   |
| LogAlways      |   0   |

W tabeli wyznaczania wartości skrótu dla ukończonych zapytania zawiera klucz, **poziom**i wartość, **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Poziom właściwość statyczna w wyliczeniu (opcjonalnie)

**Poziom** wyliczenia klucza, ale można użyć nazwy właściwości statycznej w zapytaniu tabeli wyznaczania wartości skrótu.
Zamiast używania zwracanego ciągu, nazwa właściwości musi zostać skonwertowany do wartości z **Value__** właściwości.

Na przykład, poniższy skrypt **Value__** właściwości.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```