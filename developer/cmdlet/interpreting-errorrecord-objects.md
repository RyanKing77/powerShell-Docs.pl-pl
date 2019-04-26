---
title: Interpretowanie rekord błędu obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067641"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretowanie obiektów ErrorRecord

W większości przypadków [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt reprezentuje błąd niepowodujący generowanych przez polecenia lub skryptu. Kończenie błędy można również określić dodatkowe informacje w rekord błędu za pomocą [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interfejsu.

Jeśli chcesz napisać procedurę obsługi błędów w skrypcie lub hosta, aby obsługiwać błędy, które występują podczas wykonywania polecenia lub skryptu, należy interpretować [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu, aby określić, czy go reprezentuje klasę błędu, który chcesz obsługiwać.

Gdy polecenie cmdlet napotka kończącym lub błąd niepowodujący, należy utworzyć rekord błędu, który opisuje warunku błędu. Aplikacja hosta należy zbadać te rekordy błąd i wykonać dowolną akcję ograniczą błędu. Aplikacja hosta musi również badanie rekordów błędów błędy niekończące, nie można przetworzyć rekordu, ale mogły kontynuować i należy zbadać, rekordy błąd powodujący zakończenie błędów, które spowodowało potoku zatrzymać.

> [!NOTE]
> Trwa przerywanie działania błędy wywołuje polecenie cmdlet [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody. W przypadku błędy niepowodujące wywołuje polecenie cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody.

## <a name="error-record-design"></a>Błąd projektu rekordów

Rekordy błędów są przeznaczone do zapewniają dodatkowe informacje o błędzie, który nie jest dostępna w wyjątkach przy jednoczesnym zapewnieniu, że połączone informacje we wszystkich rekordach błędu jest unikatowa. Unikatowość ten umożliwia aplikacji hosta sprawdzić różne części rekordu błędu, aby można było zidentyfikować warunek błędu i akcji host musi mieć.

## <a name="interpreting-error-records"></a>Interpretowanie rekordów błędów

Możesz przejrzeć kilka części rekordu błędu, aby zidentyfikować ten błąd. Te elementy są następujące:

- Kategoria błędu

- Wyjątek błędu

- Identyfikator błędu w pełni kwalifikowana (FQID)

- Inne informacje

### <a name="the-error-category"></a>Kategoria błędu

Kategoria błędu rekordu błędu jest jednym ze wstępnie zdefiniowanych stałych, które są dostarczane przez [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) wyliczenia. Te informacje są dostępne za pośrednictwem [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) właściwość [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu.

Polecenia cmdlet można określić kategorie CloseError OpenError, InvalidType, błąd odczytu i WriteError i innych kategorii błędów. Aplikacja hosta można użyć kategorii błędów do przechwycenia grupy błędów.

### <a name="the-exception"></a>Wyjątek

Wyjątek objęte rekordu błędu jest świadczona przez polecenie cmdlet i jest możliwy za pośrednictwem [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) właściwość [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu.

Aplikacje hosta mogą używać `is` słowo kluczowe, aby ustalić, czy wyjątek jest określonej klasy lub klasy pochodnej. Zaleca się gałęzi na typ wyjątku, jak pokazano w poniższym przykładzie.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

W ten sposób efektywnej klas pochodnych. Istnieją problemy, jeśli wyjątek jest przeprowadzona.

### <a name="the-fqid"></a>FQID

FQID jest bardziej konkretny od pozostałych informacji, których można użyć, aby zidentyfikować ten błąd. Jest to ciąg, który zawiera identyfikator zdefiniowany przez polecenie cmdlet, nazwa klasy polecenia cmdlet, a także źródła, który zgłosił błąd. Ogólnie rzecz biorąc rekord błędu jest odpowiednikiem rekord zdarzenia w dzienniku zdarzeń Windows. FQID jest odpowiednikiem następujących spójna kolekcja, która identyfikuje klasę rekord zdarzenia: (*nazwę dziennika*, *źródła*, *identyfikator zdarzenia*).

FQID powinien być kontrolowane jako pojedynczy ciąg. Jednak przypadków istnieją, w których identyfikator błędu jest przeznaczona do przeanalizowania przez aplikację hosta. Poniższy przykład jest identyfikatorem sformułowany błąd w pełni kwalifikowana.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

W poprzednim przykładzie pierwszy token jest identyfikator błędu, który następuje nazwa klasy polecenia cmdlet. Identyfikator błędu może być pojedynczy token lub może być oddzielone kropką identyfikator, umożliwiający rozgałęzianie w zakresie kontroli identyfikatora. Nie używaj biały znak lub znaki interpunkcyjne Identyfikator błędu. Jest to szczególnie ważne nie korzystała z przecinkiem na końcu; przecinek jest używany przez środowisko Windows PowerShell do oddzielenia identyfikator i nazwa klasy polecenia cmdlet.

### <a name="other-information"></a>Inne informacje

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt może być udostępniają informacje opisujące środowisko, w którym wystąpił błąd. Informacje te obejmują elementy, takie jak Szczegóły błędu, informacje wywołania i obiekt docelowy, który był przetwarzany, gdy wystąpił błąd. Mimo że te informacje mogą być przydatne do aplikacji hosta, nie zazwyczaj służy do Zidentyfikuj ten błąd. Te informacje są dostępne za pośrednictwem następujących właściwości:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Dodawanie raportów o błędach do Twojego polecenia Cmdlet do niepowodujące](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Raportowanie błędów programu Windows PowerShell](./error-reporting-concepts.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
