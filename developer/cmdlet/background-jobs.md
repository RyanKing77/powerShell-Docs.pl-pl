---
title: Zadania w tle | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068689"
---
# <a name="background-jobs"></a>Zadania w tle

Polecenia cmdlet akcję można wykonać ich wewnętrznie lub programu Windows PowerShell*zadania w tle*. Po uruchomieniu polecenia cmdlet jako zadanie w tle zadania są wykonywane asynchronicznie w jego własnym wątku, niezależnie od wątku potoku, która używa polecenia cmdlet. Z punktu widzenia użytkownika gdy polecenia cmdlet jest uruchamiane jako zadanie w tle, wiersza polecenia zwraca natychmiast nawet, jeśli zadanie trwa zbyt długo, a użytkownik może kontynuować bez zakłóceń, podczas gdy zadanie zostanie uruchomione.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Zadania w tle i zadań podrzędnych, repozytorium zadania

Obiekt zadania, który jest zwracany przez polecenia cmdlet używane do obsługi zadań w tle definiuje zadania. ( [Zadanie rozpoczęcia](/powershell/module/Microsoft.PowerShell.Core/Start-Job) polecenie cmdlet zwraca również wartość obiektu zadania.) Nazwa zadania, identyfikator, który jest używany do określenia zadania, informacje o stanie i zadania podrzędne znajdują się w tej definicji. Zadanie nie powoduje wykonania żadnej pracy. Każde zadanie w tle ma co najmniej jedno zadanie podrzędne, ponieważ zadanie podrzędne wykonuje rzeczywistą pracę. Po uruchomieniu polecenia cmdlet, aby praca jest wykonywana w tle, polecenia cmdlet należy dodać zadanie i zadania podrzędne do wspólnego repozytorium, nazywane *repozytorium zadania*.

Aby uzyskać więcej informacji na temat obsługi zadania w tle w wierszu polecenia zobacz następujące tematy:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Zapisywanie polecenia Cmdlet, które jest uruchamiane jako zadanie w tle

Aby zapisać polecenia cmdlet, które mogą być uruchamiane jako zadanie w tle, należy wykonać następujące zadania:

- Zdefiniuj `asJob` Przełącz parametr, dzięki czemu użytkownik może zdecydować, czy uruchomić polecenie cmdlet jako zadanie w tle.

- Utworzyć obiekt, który pochodzi od klasy [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klasy. Ten obiekt może być obiektu niestandardowego zadania lub obiektu zadania dostarczone przez program Windows PowerShell, takie jak [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) obiektu.

- W metodzie przetwarzania rekordów, Dodaj `if` instrukcję, która wykrywa, czy polecenia cmdlet powinny być uruchamiany jako zadanie w tle.

- Dla obiektów niestandardowych zadań implementacji klasy zadania.

- Zwróć odpowiednich obiektów, w zależności od tego, czy polecenie cmdlet jest uruchamiane jako zadanie w tle.

Dla przykładu kodu zobacz [sposobu obsługi zadań](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Interfejsy API związane z zadania w tle

Następujące interfejsy API są dostarczane przez programu Windows PowerShell do zarządzania zadania w tle.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) pochodzi obiektów niestandardowych zadań. Jest klasą abstrakcyjną.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) służy do zarządzania i zawiera informacje dotyczące bieżącego zadania w tle active.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definiuje stan zadania w tle. Stany to uruchomiona, uruchomione i zatrzymane.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) zawiera informacje o stanie zadania w tle, a w przypadku zmiany stanu ostatniego zostało spowodowane przez błąd, przyczyna zadania wprowadzono swojego bieżącego stanu.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) zawiera argumenty dla zdarzenia, które jest wywoływane, gdy zmieni się stan zadania w tle.

## <a name="windows-powershell-job-cmdlets"></a>Polecenia cmdlet programu Windows PowerShell zadania

Następujące polecenia cmdlet są dostarczane przez programu Windows PowerShell do zarządzania zadania w tle.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Pobiera zadania w tle programu Windows PowerShell, które są uruchomione w bieżącej sesji.

[Odbieranie — zadanie](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Pobiera wyniki zadania w tle programu Windows PowerShell w bieżącej sesji.

[Usuń zadanie](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Usuwa zadania w tle programu Windows PowerShell.

[Zadanie rozpoczęcia](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Uruchamia zadanie w tle programu Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Zatrzymuje wykonywanie zadania w tle programu Windows PowerShell.

[WAIT — zadanie](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Pomija wiersz polecenia, dopiero po zakończeniu jednego lub wszystkich zadań w tle programu Windows PowerShell, uruchomiony w sesji.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
