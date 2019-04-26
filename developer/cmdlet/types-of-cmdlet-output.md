---
title: Typy danych wyjściowych polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067230"
---
# <a name="types-of-cmdlet-output"></a>Typy danych wyjściowych polecenia cmdlet

PowerShell udostępnia kilka metod, które można wywoływać za pomocą poleceń cmdlet w celu generowania danych wyjściowych. Te metody umożliwiają określoną operację zapisują swoje dane wyjściowe do strumienia określone dane, takie jak strumienia danych powodzenia lub błędu strumienia danych. W tym artykule opisano typy danych wyjściowych i metody używane do generowania ich.

## <a name="types-of-output"></a>Typy danych wyjściowych

### <a name="success-output"></a>Pomyślne dane wyjściowe

Polecenia cmdlet można raportują Powodzenie, zwracając obiekt, który może być przetwarzany przez następne polecenie w potoku. Wykonane polecenia cmdlet została pomyślnie jej działaniem, wywołuje polecenie cmdlet [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody. Zaleca się, że wywołanie tej metody, zamiast [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) lub [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) metody.

Możesz podać **PassThru** Przełącz parametr dla polecenia cmdlet, które nie zwracają zazwyczaj obiektów.
Gdy **PassThru** przełącznika parametr jest określony w wierszu polecenia, polecenie cmdlet jest proszony o zwracają obiekt. Na przykład polecenia cmdlet, które ma **PassThru** parametrów, zobacz [historii Dodaj](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Dane wyjściowe błędu

Polecenia cmdlet mogą raportować błędy. Gdy wystąpi błąd powodujący zakończenie, polecenie cmdlet zgłasza wyjątek. Gdy wystąpi błąd niepowodujący, wywołuje polecenie cmdlet [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodę, aby wysłać rekord błędu do strumienia danych błędu. Aby uzyskać więcej informacji na temat raportowania błędów, zobacz [pojęcia zgłoszenie błędu](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Pełne dane wyjściowe

Polecenia cmdlet można zawierają przydatne informacje dla Ciebie, podczas gdy polecenia cmdlet jest poprawnie przetwarza rekordy przez wywołanie metody [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody. Z nich metoda generuje komunikaty pełne, które wskazują, jak akcja jest w toku.

Domyślnie komunikaty pełne nie są wyświetlane. Można określić **pełne** parametru po uruchomieniu polecenia cmdlet, aby wyświetlić te komunikaty. **Pełne** jest typowy parametr, który jest dostępny dla wszystkich poleceń cmdlet.

### <a name="progress-output"></a>Dane wyjściowe w toku

Polecenia cmdlet można udostępnić informacje o postępie można gdy polecenia cmdlet wykonuje zadania, które zająć dużo czasu, taką jak kopiowanie rekursywnie katalogu. Aby wyświetlić informacje o postępie polecenia cmdlet wywołuje [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metody.

### <a name="debug-output"></a>Dane wyjściowe debugowania

Polecenia cmdlet można podać komunikatów debugowania, które są przydatne podczas rozwiązywania problemów z kodem polecenia cmdlet. Aby wyświetlić informacje o debugowaniu polecenia cmdlet wywołuje [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody.

Domyślnie komunikaty debugowania nie są wyświetlane. Można określić **debugowania** parametru po uruchomieniu polecenia cmdlet, aby wyświetlić te komunikaty. **Debugowanie** jest typowy parametr, który jest dostępny dla wszystkich poleceń cmdlet.

### <a name="warning-output"></a>Ostrzeżenie w danych wyjściowych

Polecenia cmdlet można wyświetlić komunikaty ostrzegawcze, wywołując [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody.

Domyślnie komunikaty ostrzegawcze są wyświetlane. Jednak należy skonfigurować przy użyciu komunikaty ostrzegawcze `$WarningPreference` zmiennej lub za pomocą **pełne** i **debugowania** parametrów podczas wywoływania polecenia cmdlet.

## <a name="displaying-output"></a>Wyświetlanie danych wyjściowych

Dla wszystkich wywołań metody zapisu wyświetlanie zawartości jest określany przez zmienne określonego środowiska uruchomieniowego. Wyjątek stanowi [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody. Korzystając z tymi zmiennymi, można wprowadzić odpowiednie zapisu wywołanie w odpowiednim miejscu w kodzie i nie martw się o, gdy lub jeśli dane wyjściowe powinny być wyświetlane.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Uzyskiwanie dostępu do funkcjonalności dane wyjściowe aplikacji hosta

Istnieje również możliwość projektowania polecenia cmdlet, aby uzyskać bezpośredni dostęp do funkcjonalności dane wyjściowe aplikacji hosta za pośrednictwem środowiska uruchomieniowego programu PowerShell. Za pomocą interfejsów API dostarczonych przez program PowerShell zamiast hosta [System.Console](/dotnet/api/System.Console) lub [System.Windows.Forms](/dotnet/api/System.Windows.Forms) gwarantuje, że Twojego polecenia cmdlet będzie współdziałać z wielu różnych hostów. Na przykład: **powershell.exe** hosta konsoli **powershell_ise.exe** graficznego hosta, host komunikacji zdalnej programu PowerShell i innych hostów.

## <a name="see-also"></a>Zobacz też

[Pojęcia raportowania błędów](./error-reporting-concepts.md)

[Polecenia cmdlet — omówienie](./cmdlet-overview.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)