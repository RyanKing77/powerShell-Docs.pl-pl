---
title: Polecenia cmdlet raportów o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057947"
---
# <a name="cmdlet-error-reporting"></a>Raportowanie błędów poleceń cmdlet

Polecenia cmdlet należy zgłaszać błędy inaczej w zależności od tego, czy błędy są Kończenie błędów lub błędy niekończące. Trwa przerywanie działania błędy są błędy powodujące potoku, który ma zostać zakończony natychmiast lub błędy, które występują, gdy nie ma powodu kontynuować przetwarzanie. Błędy niekończące błędów tych, którzy raportują bieżącego warunek błędu, ale dalsze przetwarzanie danych wejściowych obiektów cmdlet. Błędy niekończące użytkownik zwykle jest powiadamiany o problemie, ale polecenia cmdlet kontynuuje przetwarzanie następny obiekt danych wejściowych.

## <a name="terminating-and-nonterminating-errors"></a>Trwa przerywanie działania i niekończące błędy

Poniższe wskazówki może służyć do określenia, czy warunek błędu jest błąd powodujący przerwanie lub niekończące błędu.

- Warunek błędu uniemożliwia Twojego polecenia cmdlet pomyślnie przetwarzania wszelkich dalszych danych wejściowych obiektów? Jeśli tak, to jest błąd powodujący zakończenie.

- Warunek błędu dotyczy określonego obiektu wejściowego lub podzbiór obiektów danych wejściowych? Jeśli tak, jest to błąd niekończące.

- Polecenie cmdlet są dozwolone wielu obiektów danych wejściowych, takie, przetwarzanie może się powieść, na innym obiekcie wejściowych? Jeśli tak, jest to błąd niekończące.

- Polecenia cmdlet, który może akceptować wielu danych wejściowych obiektów należy podjąć decyzję dotyczącą między co to są Kończenie i błędy niekończące, nawet wtedy, gdy w danej sytuacji dotyczy tylko jednego obiektu wejściowego.

- Polecenia cmdlet może odbierać dowolną liczbę obiektów w danych wejściowych i wysłać dowolną liczbę obiektów powodzenia lub błędu, zanim zostanie zgłoszony wyjątek powodujący przerwanie. Nie ma relacji między liczba odebranych danych wejściowych obiektów i liczbę obiektów sukcesach i błędach wysyłane.

- Polecenia cmdlet, który może akceptować tylko 0 – 1 obiekty wejściowe i generować tylko 0 – 1 danych wyjściowych, obiekty powinny traktować błędy jako błędy powodujący zakończenie i generują wyjątki kończącego.

## <a name="reporting-nonterminating-errors"></a>Błędy niekończące raportowania

Raportowania błędów niekończące, zawsze należy wykonać w ramach wykonania polecenia cmdlet [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody lub [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody. Tego rodzaju błędy są zgłaszane przez wywołanie metody [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, która z kolei wysyła rekord błędu do strumienia błędów.

## <a name="reporting-terminating-errors"></a>Raportowanie błędów kończący

Trwa przerywanie działania błędy są zgłaszane przez zgłaszanie wyjątków lub przez wywołanie [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody. Należy pamiętać, że polecenia cmdlet można też przechwytywać i ponowne generowanie wyjątków, takie jak zdarzeń OutOfMemory, jednak nie są wymagane do ponownego zgłaszają wyjątki, ponieważ środowisko wykonawcze programu Windows PowerShell będzie przechwytywać także.

Można także zdefiniować własne wyjątki w przypadku problemów dotyczących tylko do swojej sytuacji lub dodania dodatkowych informacji do istniejących wyjątek przy użyciu swój rekord błędu.

## <a name="error-records"></a>Rejestruje błąd

Program Windows PowerShell w tym artykule opisano niekończące błąd za pośrednictwem [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektów. Każdy [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiekt zawiera informacje o błędzie kategorii, obiekt docelowy opcjonalne i szczegółowe informacje o warunku błędu.

### <a name="error-identifiers"></a>Identyfikatory błąd

Identyfikator błędu jest prosty ciąg, który identyfikuje błąd w ramach polecenia cmdlet. Program Windows PowerShell łączy tego identyfikatora, identyfikatorem polecenia cmdlet, można utworzyć identyfikatora pełną błąd, którego można później podczas filtrowania strumienie błąd lub rejestrowanie błędów podczas odpowiadania na określone błędy lub z innymi działaniami specyficzne dla użytkownika.

Należy przestrzegać następujących wytycznych podczas określania identyfikatorów błąd.

- Identyfikatory różny, wysoce określony błąd można przypisać różne ścieżki. Każda ścieżka kodu, który wywołuje [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) lub [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) powinny mieć własny identyfikator błędu.

- Błąd identyfikatory powinny być unikatowe dla typów wyjątków CLR błędy niekończące i kończący.

- Nie należy zmieniać semantyki Identyfikator błędu między wersjami, dostawca programu Windows PowerShell lub polecenia cmdlet. Po nawiązaniu semantykę odpowiadającym błędzie pozostają stałe w całym cyklu życia Twojego polecenia cmdlet.

- Trwa przerywanie działania błędów za pomocą identyfikatora błąd unikatowy dla określonego typu wyjątek CLR. Jeśli zmieni się typ wyjątku, należy użyć nowy identyfikator błędu.

- Błędy niekończące należy użyć identyfikatora wystąpienia określonego błędu dla konkretnego obiektu wejściowego.

- Wybierz tekst dla identyfikatora, odpowiadający lapidarnie błąd raportowany. Nie należy używać biały znak lub znaki interpunkcyjne.

- Generuje błąd identyfikatory, których nie do odtworzenia. Na przykład nie generują identyfikatorów, które zawierają identyfikator procesu. Błąd identyfikatory są przydatne tylko wtedy, gdy odnoszą się do identyfikatorów, które są widoczne dla innych użytkowników, którzy napotykają ten sam problem.

### <a name="error-categories"></a>Kategorii błędów

Błąd kategorie są używane do grupowania błędów dla użytkownika końcowego. Program Windows PowerShell definiuje te kategorie i poleceń cmdlet i dostawcy środowiska Windows PowerShell, należy wybrać opcję je podczas generowania rekordu błędu.

Aby uzyskać opis kategorii błędów, które są dostępne, zobacz [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) wyliczenia. Ogólnie rzecz biorąc należy unikać używania brak błędu, UndefinedError i błąd rodzajowy, jeśli to możliwe.

Użytkownicy mogą wyświetlać błędy na podstawie kategorii podczas instalacji "`$ErrorView`" do "CategoryView".

## <a name="see-also"></a>Zobacz też

[Polecenia cmdlet programu Windows PowerShell](./cmdlet-overview.md)

[Dane wyjściowe polecenia cmdlet](./types-of-cmdlet-output.md)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
