---
title: Kończenie błędy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059239"
---
# <a name="terminating-errors"></a>Błędy powodujące przerwanie działania

W tym temacie omówiono metodę używaną do raportu przerywa błędy. Omówiono również sposób wywoływania metody z w ramach polecenia cmdlet, a następnie omówiono w nim wyjątki, które mogą być zwrócone przez środowisko uruchomieniowe programu Windows PowerShell, gdy wywoływana jest metoda.

Gdy kończącym wystąpi błąd, polecenia cmdlet należy zgłosić błąd przez wywołanie metody [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metody. Ta metoda umożliwia polecenia cmdlet wysłać rekord błędu, który opisuje warunek, który spowodował błąd powodujący przerwanie. Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).

Gdy [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoda jest wywoływana, środowisko wykonawcze programu Windows PowerShell trwale zatrzymuje wykonywanie potoku i generuje [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) wyjątku. Wszystkie kolejne próby wywołania [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), lub kilka innych interfejsów API powoduje, że te wywołania throw [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) wyjątku.

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) wyjątek może również wystąpić, jeśli polecenie cmdlet innego potoku zgłasza błąd powodujący zakończenie, jeśli użytkownik został poproszony o zatrzymanie potoku lub potoku została zatrzymana. przed ukończeniem jakiegokolwiek powodu. Polecenie cmdlet nie jest konieczne catch [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) wyjątek, chyba że należy wyczyścić otworzyć, zasoby lub jego stanu wewnętrznego.

Polecenia cmdlet można napisać dowolną liczbę obiektów w danych wyjściowych lub błędy niepowodujące przed zgłoszeniem błąd powodujący zakończenie. Jednak błąd powodujący zakończenie trwale zatrzymuje potoku i żadne dalsze dane wyjściowe, błędy, zakończenia lub mogą zostać zgłoszone błędy niepowodujące.

Polecenia cmdlet można wywołać [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) tylko z wątku, który wywołał [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), lub [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) przetwarzania metody wejściowej. Nie należy próbować wywołać [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) lub [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) z innego wątku. Zamiast tego błędy muszą zostać przekazane do głównego wątku.

Istnieje możliwość, dla polecenia cmdlet, aby zgłosić wyjątek w jego implementacja obiektu [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), lub [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody. Wyjątek z tych metod (z wyjątkiem kilku warunków poważny błąd, które zatrzymać hosta programu Windows PowerShell) jest interpretowany jako błąd powodujący zakończenie, które powoduje zatrzymanie potoku, ale nie środowiska Windows PowerShell jako całości. (Dotyczy to tylko wątku głównego polecenia cmdlet. Nieprzechwyconych wyjątków w wątkach, zduplikowany przy użyciu polecenia cmdlet, ogólnie rzecz biorąc, zatrzymanie hosta programu Windows PowerShell.) Firma Microsoft zaleca użycie [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) zamiast zgłaszać wyjątek, ponieważ błąd rekord zawiera dodatkowe informacje o warunku błędu, co przydaje się do użytkownik końcowy. Polecenia cmdlet powinny przestrzegać wytycznych kodu zarządzanego, przed wychwytywanie i obsługa wyjątków na wszystkich (`catch (Exception e)`). Konwertuj tylko wyjątki znane i oczekiwanych typów rekordów błędów.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell błąd rekordów](./windows-powershell-error-records.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
