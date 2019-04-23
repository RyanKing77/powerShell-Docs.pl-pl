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
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="8816e-102">Tworzenie zapytań polecenia Get-WinEvent za pomocą parametru FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="8816e-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="8816e-103">Do odczytu, oryginalnym czerwca 3 2014 r. **Scripting Guy** blog post, zobacz [FilterHashTable korzystanie w dzienniku zdarzeń filtr przy użyciu programu PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="8816e-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="8816e-104">W tym artykule znajduje się fragment, oryginalnym wpisu w blogu i wyjaśnia, jak używać `Get-WinEvent` polecenia cmdlet **FilterHashtable** parametru, aby filtrować dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8816e-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="8816e-105">W programie PowerShell `Get-WinEvent` polecenie cmdlet jest zaawansowaną metodą do filtrowania zdarzeń Windows i dzienniki diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="8816e-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="8816e-106">Zwiększa wydajność, kiedy `Get-WinEvent` zapytanie używa **FilterHashtable** parametru.</span><span class="sxs-lookup"><span data-stu-id="8816e-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="8816e-107">Podczas pracy z dziennikami zdarzeń dużych, nie jest efektywne wysyłanie obiektów w dół potoku w celu `Where-Object` polecenia.</span><span class="sxs-lookup"><span data-stu-id="8816e-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="8816e-108">Przed program PowerShell 6 `Get-EventLog` polecenia cmdlet została inną opcję, aby pobrać dane dziennika.</span><span class="sxs-lookup"><span data-stu-id="8816e-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="8816e-109">Na przykład poniższe polecenia są nieefektywne filtru **Microsoft-Windows-defragmentowania** dzienników:</span><span class="sxs-lookup"><span data-stu-id="8816e-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="8816e-110">Następujące polecenie używa tablicy skrótów, które poprawia wydajność:</span><span class="sxs-lookup"><span data-stu-id="8816e-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="8816e-111">Wpisy na blogu dotyczące wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8816e-111">Blog posts about enumeration</span></span>

<span data-ttu-id="8816e-112">W tym artykule przedstawiono informacje o sposobie używania wartości wyliczane w tabeli wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="8816e-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="8816e-113">Aby uzyskać więcej informacji na temat wyliczania przeczytaj **Scripting Guy** wpisów w blogu.</span><span class="sxs-lookup"><span data-stu-id="8816e-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="8816e-114">Aby utworzyć funkcję, która zwraca wartości wyliczenia, zobacz [wyliczeń i wartości](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="8816e-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="8816e-115">Aby uzyskać więcej informacji, zobacz [Scripting Guy szeregu blogu wpisy dotyczące wyliczenia](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="8816e-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="8816e-116">Hash, pary klucz/wartość tabeli</span><span class="sxs-lookup"><span data-stu-id="8816e-116">Hash table key/value pairs</span></span>

<span data-ttu-id="8816e-117">Aby utworzyć wydajne zapytania, użyj `Get-WinEvent` polecenia cmdlet z **FilterHashtable** parametru.</span><span class="sxs-lookup"><span data-stu-id="8816e-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="8816e-118">**FilterHashtable** jako filtr, aby uzyskać konkretne informacje z dzienników zdarzeń Windows akceptuje tabelę mieszania.</span><span class="sxs-lookup"><span data-stu-id="8816e-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="8816e-119">Tabela skrótu używa **klucz/wartość** pary.</span><span class="sxs-lookup"><span data-stu-id="8816e-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="8816e-120">Aby uzyskać więcej informacji o tabelach skrótów, zobacz [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="8816e-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="8816e-121">Jeśli **klucz/wartość** pary znajdują się na tym samym wierszu, muszą być rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="8816e-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="8816e-122">Jeśli każda **klucz/wartość** pary znajduje się w osobnym wierszu, średnik nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="8816e-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="8816e-123">Na przykład, w tym artykule umieszcza **klucz/wartość** pary w osobnych wierszach, a nie Użyj średników.</span><span class="sxs-lookup"><span data-stu-id="8816e-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="8816e-124">W tym przykładzie użyto kilka **FilterHashtable** parametru **klucz/wartość** pary.</span><span class="sxs-lookup"><span data-stu-id="8816e-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="8816e-125">Ukończone zapytanie zawiera **Nazwa_dziennika**, **ProviderName**, **słowa kluczowe**, **identyfikator**, i **poziom**.</span><span class="sxs-lookup"><span data-stu-id="8816e-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="8816e-126">Zaakceptowane **klucz/wartość** pary są wyświetlane w poniższej tabeli i znajdują się w dokumentacji dotyczącej [polecenia Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parametr.</span><span class="sxs-lookup"><span data-stu-id="8816e-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="8816e-127">W poniższej tabeli przedstawiono nazwy kluczy, typy danych, i czy symbole wieloznaczne są akceptowane wartości danych.</span><span class="sxs-lookup"><span data-stu-id="8816e-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="8816e-128">Nazwa klucza</span><span class="sxs-lookup"><span data-stu-id="8816e-128">Key name</span></span>     | <span data-ttu-id="8816e-129">Typ danych wartości</span><span class="sxs-lookup"><span data-stu-id="8816e-129">Value data type</span></span>    | <span data-ttu-id="8816e-130">Akceptuje symbole wieloznaczne?</span><span class="sxs-lookup"><span data-stu-id="8816e-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="8816e-131">LogName</span><span class="sxs-lookup"><span data-stu-id="8816e-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="8816e-132">Tak</span><span class="sxs-lookup"><span data-stu-id="8816e-132">Yes</span></span> |
| <span data-ttu-id="8816e-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="8816e-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="8816e-134">Tak</span><span class="sxs-lookup"><span data-stu-id="8816e-134">Yes</span></span> |
| <span data-ttu-id="8816e-135">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="8816e-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="8816e-136">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-136">No</span></span>  |
| <span data-ttu-id="8816e-137">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8816e-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="8816e-138">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-138">No</span></span>  |
| <span data-ttu-id="8816e-139">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8816e-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="8816e-140">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-140">No</span></span>  |
| <span data-ttu-id="8816e-141">Poziom</span><span class="sxs-lookup"><span data-stu-id="8816e-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="8816e-142">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-142">No</span></span>  |
| <span data-ttu-id="8816e-143">Godzina rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="8816e-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="8816e-144">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-144">No</span></span>  |
| <span data-ttu-id="8816e-145">Czas zakończenia</span><span class="sxs-lookup"><span data-stu-id="8816e-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="8816e-146">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-146">No</span></span>  |
| <span data-ttu-id="8816e-147">Identyfikator użytkownika</span><span class="sxs-lookup"><span data-stu-id="8816e-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="8816e-148">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-148">No</span></span>  |
| <span data-ttu-id="8816e-149">Dane</span><span class="sxs-lookup"><span data-stu-id="8816e-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="8816e-150">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="8816e-151">Nie</span><span class="sxs-lookup"><span data-stu-id="8816e-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="8816e-152">Tworzenie zapytań przy użyciu tablicy skrótów</span><span class="sxs-lookup"><span data-stu-id="8816e-152">Building a query with a hash table</span></span>

<span data-ttu-id="8816e-153">Aby zweryfikować wyniki i rozwiązywanie problemów, ułatwia tworzenie tabeli mieszania, jeden **klucz/wartość** pary w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="8816e-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="8816e-154">Zapytanie pobiera dane z **aplikacji** dziennika.</span><span class="sxs-lookup"><span data-stu-id="8816e-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="8816e-155">Tabela skrótu jest odpowiednikiem `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="8816e-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="8816e-156">Aby rozpocząć, Utwórz `Get-WinEvent` zapytania.</span><span class="sxs-lookup"><span data-stu-id="8816e-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="8816e-157">Użyj **FilterHashtable** parametru **klucz/wartość** parowanie klucz, **Nazwa_dziennika**i wartość, **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="8816e-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="8816e-158">Kontynuować tworzenie tabeli wyznaczania wartości skrótu z **ProviderName** klucza.</span><span class="sxs-lookup"><span data-stu-id="8816e-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="8816e-159">**ProviderName** to nazwa, która pojawia się w **źródła** pole **Podgląd zdarzeń Windows**.</span><span class="sxs-lookup"><span data-stu-id="8816e-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="8816e-160">Na przykład **środowiska uruchomieniowego .NET** na następującym zrzucie ekranu:</span><span class="sxs-lookup"><span data-stu-id="8816e-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Obraz podglądu zdarzeń Windows źródeł.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="8816e-162">Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, \*\* ProviderName i wartość, **środowiska uruchomieniowego .NET**.</span><span class="sxs-lookup"><span data-stu-id="8816e-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="8816e-163">Jeśli zapytanie musi pobrać dane z dzienników zdarzeń zarchiwizowanych, użyj **ścieżki** klucza.</span><span class="sxs-lookup"><span data-stu-id="8816e-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="8816e-164">**Ścieżki** wartość określa pełną ścieżkę do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="8816e-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="8816e-165">Aby uzyskać więcej informacji, zobacz **Scripting Guy** wpis w blogu [Użyj programu PowerShell można przeanalizować zapisane dzienniki zdarzeń błędów](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="8816e-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="8816e-166">Przy użyciu wartości wyliczane w tabeli wyznaczania wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="8816e-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="8816e-167">**Słowa kluczowe** jest kluczowi w tabeli wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="8816e-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="8816e-168">**Słowa kluczowe** — typ danych jest tablicą `[long]` typ, który przechowuje dużą liczbą wartości.</span><span class="sxs-lookup"><span data-stu-id="8816e-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="8816e-169">Użyj następującego polecenia, aby znaleźć wartość maksymalna `[long]`:</span><span class="sxs-lookup"><span data-stu-id="8816e-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="8816e-170">Aby uzyskać **słowa kluczowe** klucza, programu PowerShell używa wielu, nie ciąg znaków takich jak **zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="8816e-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="8816e-171">**Podgląd zdarzeń Windows** Wyświetla **słowa kluczowe** jako ciągi, ale są one wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8816e-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="8816e-172">W tabeli wyznaczania wartości skrótu, jeśli używasz **słowa kluczowe** klucza z wartością ciągu, jest wyświetlany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8816e-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="8816e-173">Otwórz **Podgląd zdarzeń Windows** i **akcje** okienku kliknij **Filtruj bieżący dziennik**.</span><span class="sxs-lookup"><span data-stu-id="8816e-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="8816e-174">**Słowa kluczowe** menu rozwijane wyświetli dostępne słów kluczowych, jak pokazano na poniższym zrzucie ekranu:</span><span class="sxs-lookup"><span data-stu-id="8816e-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Obraz podglądu zdarzeń Windows słów kluczowych.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="8816e-176">Użyj następującego polecenia, aby wyświetlić `StandardEventKeywords` nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="8816e-177">Wartości wyliczane są udokumentowane w artykule **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="8816e-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="8816e-178">Aby uzyskać więcej informacji, zobacz [wyliczenie StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="8816e-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="8816e-179">**Słowa kluczowe** nazwy i wartości wyliczane są następujące:</span><span class="sxs-lookup"><span data-stu-id="8816e-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="8816e-180">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8816e-180">Name</span></span>             |  <span data-ttu-id="8816e-181">Wartość</span><span class="sxs-lookup"><span data-stu-id="8816e-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="8816e-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="8816e-182">AuditFailure</span></span>     | <span data-ttu-id="8816e-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="8816e-183">4503599627370496</span></span>  |
| <span data-ttu-id="8816e-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="8816e-184">AuditSuccess</span></span>     | <span data-ttu-id="8816e-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="8816e-185">9007199254740992</span></span>  |
| <span data-ttu-id="8816e-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="8816e-186">CorrelationHint2</span></span> | <span data-ttu-id="8816e-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="8816e-187">18014398509481984</span></span> |
| <span data-ttu-id="8816e-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="8816e-188">EventLogClassic</span></span>  | <span data-ttu-id="8816e-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="8816e-189">36028797018963968</span></span> |
| <span data-ttu-id="8816e-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="8816e-190">Sqm</span></span>              | <span data-ttu-id="8816e-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="8816e-191">2251799813685248</span></span>  |
| <span data-ttu-id="8816e-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="8816e-192">WdiDiagnostic</span></span>    | <span data-ttu-id="8816e-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="8816e-193">1125899906842624</span></span>  |
| <span data-ttu-id="8816e-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="8816e-194">WdiContext</span></span>       | <span data-ttu-id="8816e-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="8816e-195">562949953421312</span></span>   |
| <span data-ttu-id="8816e-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="8816e-196">ResponseTime</span></span>     | <span data-ttu-id="8816e-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="8816e-197">281474976710656</span></span>   |
| <span data-ttu-id="8816e-198">Brak</span><span class="sxs-lookup"><span data-stu-id="8816e-198">None</span></span>             | <span data-ttu-id="8816e-199">0</span><span class="sxs-lookup"><span data-stu-id="8816e-199">0</span></span>                 |

<span data-ttu-id="8816e-200">Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, **słowa kluczowe**i **EventLogClassic** wartość wyliczenia **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="8816e-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="8816e-201">Wartość statyczna właściwość słowa kluczowe (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="8816e-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="8816e-202">**Słowa kluczowe** wyliczenia klucza, ale można użyć nazwy właściwości statycznej w zapytaniu tabeli wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="8816e-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="8816e-203">Zamiast używania zwracanego ciągu, nazwa właściwości musi zostać skonwertowany do wartości z **Value__** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="8816e-204">Na przykład, poniższy skrypt **Value__** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="8816e-205">Filtrowanie wg identyfikatora zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8816e-205">Filtering by Event Id</span></span>

<span data-ttu-id="8816e-206">Aby uzyskać bardziej szczegółowe dane, wyniki zapytania są filtrowane według **identyfikator zdarzenia**. **Identyfikator zdarzenia** odwołuje się do tabeli mieszania jako klucz **identyfikator** , a wartość jest konkretnym **identyfikator zdarzenia**. **Podgląd zdarzeń Windows** Wyświetla **identyfikator zdarzenia**. W tym przykładzie użyto **1023 identyfikator zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="8816e-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="8816e-207">Aktualizuj tabelę mieszania i obejmują **klucz/wartość** parowanie klucz, **identyfikator** i wartości, **1023**.</span><span class="sxs-lookup"><span data-stu-id="8816e-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="8816e-208">Filtrowanie według poziomu</span><span class="sxs-lookup"><span data-stu-id="8816e-208">Filtering by Level</span></span>

<span data-ttu-id="8816e-209">Aby dodatkowo doprecyzować wyniki i zawierają tylko te zdarzenia, które są błędy, należy użyć **poziom** klucza.</span><span class="sxs-lookup"><span data-stu-id="8816e-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="8816e-210">**Podgląd zdarzeń Windows** Wyświetla **poziom** jako wartości ciągu, ale są one wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8816e-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="8816e-211">W tabeli wyznaczania wartości skrótu, jeśli używasz **poziom** klucza z wartością ciągu, jest wyświetlany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8816e-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="8816e-212">**Poziom** zawiera wartości, takie jak **błąd**, **ostrzeżenie**, lub **komunikat o charakterze informacyjnym**.</span><span class="sxs-lookup"><span data-stu-id="8816e-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="8816e-213">Użyj następującego polecenia, aby wyświetlić `StandardEventLevel` nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="8816e-214">Wartości wyliczane są udokumentowane w artykule **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="8816e-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="8816e-215">Aby uzyskać więcej informacji, zobacz [wyliczenie StandardEventLevel](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="8816e-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="8816e-216">**Poziom** nazwy klucza i wartości wyliczane są następujące:</span><span class="sxs-lookup"><span data-stu-id="8816e-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="8816e-217">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8816e-217">Name</span></span>           | <span data-ttu-id="8816e-218">Wartość</span><span class="sxs-lookup"><span data-stu-id="8816e-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="8816e-219">Pełny</span><span class="sxs-lookup"><span data-stu-id="8816e-219">Verbose</span></span>        |   <span data-ttu-id="8816e-220">5</span><span class="sxs-lookup"><span data-stu-id="8816e-220">5</span></span>   |
| <span data-ttu-id="8816e-221">Informacyjny</span><span class="sxs-lookup"><span data-stu-id="8816e-221">Informational</span></span>  |   <span data-ttu-id="8816e-222">4</span><span class="sxs-lookup"><span data-stu-id="8816e-222">4</span></span>   |
| <span data-ttu-id="8816e-223">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="8816e-223">Warning</span></span>        |   <span data-ttu-id="8816e-224">3</span><span class="sxs-lookup"><span data-stu-id="8816e-224">3</span></span>   |
| <span data-ttu-id="8816e-225">Błąd</span><span class="sxs-lookup"><span data-stu-id="8816e-225">Error</span></span>          |   <span data-ttu-id="8816e-226">2</span><span class="sxs-lookup"><span data-stu-id="8816e-226">2</span></span>   |
| <span data-ttu-id="8816e-227">Krytyczne</span><span class="sxs-lookup"><span data-stu-id="8816e-227">Critical</span></span>       |   <span data-ttu-id="8816e-228">1</span><span class="sxs-lookup"><span data-stu-id="8816e-228">1</span></span>   |
| <span data-ttu-id="8816e-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="8816e-229">LogAlways</span></span>      |   <span data-ttu-id="8816e-230">0</span><span class="sxs-lookup"><span data-stu-id="8816e-230">0</span></span>   |

<span data-ttu-id="8816e-231">W tabeli wyznaczania wartości skrótu dla ukończonych zapytania zawiera klucz, **poziom**i wartość, **2**.</span><span class="sxs-lookup"><span data-stu-id="8816e-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="8816e-232">Poziom właściwość statyczna w wyliczeniu (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="8816e-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="8816e-233">**Poziom** wyliczenia klucza, ale można użyć nazwy właściwości statycznej w zapytaniu tabeli wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="8816e-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="8816e-234">Zamiast używania zwracanego ciągu, nazwa właściwości musi zostać skonwertowany do wartości z **Value__** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="8816e-235">Na przykład, poniższy skrypt **Value__** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8816e-235">For example, the following script uses the **Value__** property.</span></span>

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