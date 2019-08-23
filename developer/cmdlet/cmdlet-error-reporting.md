---
title: Raportowanie błędów poleceń cmdlet | Microsoft Docs
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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986316"
---
# <a name="cmdlet-error-reporting"></a>Raportowanie błędów poleceń cmdlet

Polecenia cmdlet powinny raportować błędy w różny sposób w zależności od tego, czy błędy przerywają błędy lub błędy niepowodujące zakończenia. Przyczyną błędów są błędy powodujące przerwanie potoku natychmiast lub błędy występujące, gdy nie ma powodu do dalszego przetwarzania. Błędy niepowodujące zakończenia to te błędy, które zgłaszają bieżący warunek błędu, ale polecenie cmdlet może nadal przetwarzać obiekty wejściowe. W przypadku błędów niezakończonych użytkownik jest zazwyczaj powiadamiany o problemie, ale polecenie cmdlet kontynuuje przetwarzanie następnego obiektu wejściowego.

## <a name="terminating-and-nonterminating-errors"></a>Błędy powodujące zakończenie i niekończenie

Poniższe wskazówki mogą służyć do określenia, czy warunek błędu to błąd powodujący przerwanie lub błąd niepowodujący zakończenia.

- Czy warunek błędu uniemożliwia pomyślne przetwarzanie dalszych obiektów wejściowych przez polecenie cmdlet? Jeśli tak, jest to błąd powodujący przerwanie.

- Czy warunek błędu związany z określonym obiektem wejściowym lub podzbiorem obiektów wejściowych? Jeśli tak, jest to błąd niepowodujący zakończenia.

- Czy polecenie cmdlet akceptuje wiele obiektów wejściowych, na przykład przetwarzanie może się powieść w innym obiekcie wejściowym? Jeśli tak, jest to błąd niepowodujący zakończenia.

- Polecenia cmdlet, które mogą akceptować wiele obiektów wejściowych, powinny decydować między czym są błędy kończące się i niepowodujące zakończenia, nawet jeśli konkretna sytuacja dotyczy tylko jednego obiektu wejściowego.

- Polecenia cmdlet mogą odbierać dowolną liczbę obiektów wejściowych i wysyłać dowolną liczbę obiektów sukcesu lub błędu przed wygenerowaniem wyjątku kończącego. Nie istnieje relacja między liczbą odebranych obiektów wejściowych i liczbą wysłanych obiektów powodzeń i błędów.

- Polecenia cmdlet, które mogą akceptować tylko 0-1 obiektów wejściowych i generować tylko 0-1 obiektów wyjściowych, powinny traktować błędy jako przerywające błędy i generować wyjątki kończące się.

## <a name="reporting-nonterminating-errors"></a>Raportowanie błędów niezakończonych

Raportowanie błędu niekończącego powinno być zawsze wykonywane w implementacji polecenia cmdlet [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , metody [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) lub Metoda [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Te typy błędów są zgłaszane przez wywołanie metody [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , która z kolei wysyła rekord błędu do strumienia błędów.

## <a name="reporting-terminating-errors"></a>Raportowanie błędów kończących

Błędy powodujące przerwanie są raportowane przez wyrzucanie wyjątków lub przez wywołanie metody [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Należy pamiętać, że polecenia cmdlet mogą również wychwycić i ponownie zgłosić wyjątki, takie jak **OutOfMemory**, jednak nie są wymagane do ponownego zgłoszenia wyjątków, ponieważ środowisko uruchomieniowe programu PowerShell przechwytuje je również.

Można również zdefiniować własne wyjątki dla problemów specyficznych dla danej sytuacji lub dodać dodatkowe informacje do istniejącego wyjątku przy użyciu rekordu błędu.

## <a name="error-records"></a>Rekordy błędów

Program PowerShell opisuje niekończący warunek błędu z obiektami [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Każdy obiekt zawiera informacje o kategorii błędów, opcjonalny obiekt docelowy i szczegółowe informacje o warunku błędu.

### <a name="error-identifiers"></a>Identyfikatory błędów

Identyfikator błędu jest prostym ciągiem, który identyfikuje warunek błędu w poleceniu cmdlet.
Program PowerShell łączy ten identyfikator z identyfikatorem polecenia cmdlet, aby utworzyć w pełni kwalifikowany Identyfikator błędu, który może być później używany podczas filtrowania strumieni błędów lub błędów rejestrowania, gdy odpowiada na określone błędy lub z innymi działaniami specyficznymi dla użytkownika.

Podczas określania identyfikatorów błędów należy przestrzegać następujących wytycznych:

- Przypisuj różne, wysoce specyficzne identyfikatory błędów do różnych ścieżek kodu. Każda ścieżka kodu wywołująca [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) lub [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) powinna mieć własny identyfikator błędu.

- Identyfikatory błędów powinny być unikatowe dla typów wyjątków środowiska uruchomieniowego języka wspólnego (CLR) zarówno dla błędów kończących, jak i niezakończonych.

- Nie zmieniaj semantyki identyfikatora błędu między wersjami poleceń cmdlet lub dostawcy programu PowerShell. Po ustanowieniu semantyki identyfikatora błędu powinna ona pozostać stała w całym cyklu życia polecenia cmdlet.

- Aby można było przerywać błędy, należy użyć unikatowego identyfikatora błędu dla określonego typu wyjątku środowiska CLR. Jeśli typ wyjątku ulegnie zmianie, Użyj nowego identyfikatora błędu.

- W przypadku błędów niezakończonych Użyj określonego identyfikatora błędu dla określonego obiektu wejściowego.

- Wybierz tekst dla identyfikatora, który tersely odpowiada raportowanemu błędowi. Nie używaj białych znaków ani interpunkcji.

- Nie Generuj identyfikatorów błędów, które nie są odtwarzalne. Na przykład nie Generuj identyfikatorów, które zawierają identyfikator procesu. Identyfikatory błędów są przydatne tylko wtedy, gdy odpowiadają identyfikatorom, które są widoczne dla innych użytkowników, którzy występują tego samego problemu.

### <a name="error-categories"></a>Kategorie błędów

Kategorie błędów są używane do grupowania błędów dla użytkownika. Program PowerShell definiuje te kategorie i polecenia cmdlet, a dostawcy programu PowerShell muszą wybierać między nimi podczas generowania rekordu błędu.

Aby uzyskać opis dostępnych kategorii błędów, zobacz Wyliczenie [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Ogólnie rzecz biorąc, należy unikać używania **NOERROR**, **UndefinedError**i **błąd rodzajowy** , jeśli jest to możliwe.

Użytkownicy mogą wyświetlać Błędy w oparciu o kategorię, gdy `$ErrorView` mają ustawioną wartość **CategoryView**.

## <a name="see-also"></a>Zobacz też

[Przegląd poleceń cmdlet](./cmdlet-overview.md)

[Typy danych wyjściowych polecenia cmdlet](./types-of-cmdlet-output.md)

[Dokumentacja programu Windows PowerShell](../windows-powershell-reference.md)
