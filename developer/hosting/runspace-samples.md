---
title: Przykłady obszarem działania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082740"
---
# <a name="runspace-samples"></a>Przykłady obszarów działania

Ta sekcja zawiera przykładowy kod, który ilustruje sposób używania różnych rodzajów obszary działania do uruchamiania poleceń, synchronicznie i asynchronicznie. Microsoft Visual Studio umożliwia tworzenie aplikacji konsolowej, a następnie skopiować kod z tematy w tej sekcji, w aplikacji hosta.

## <a name="in-this-section"></a>W tej sekcji

> [!NOTE]
> Aby uzyskać przykłady aplikacji hosta, które tworzą interfejsy niestandardowego hosta, zobacz [niestandardowego hosta przykłady](./custom-host-samples.md).

 [Przykładowe Runspace01](./runspace01-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet synchronicznie i wyświetlić dane wyjściowe w konsoli programu okno.

 [Przykładowe Runspace02](./runspace02-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) polecenia cmdlet synchronicznie. Wyniki tych poleceń jest wyświetlana przy użyciu [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroli.

 [Przykładowe Runspace03](./runspace03-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić skrypt synchronicznie i sposób obsługi błędy niepowodujące. Skrypt otrzymuje listę nazw procesu, a następnie pobierze te procesy. Wyniki skryptu, między innymi niepowodujące błędy, które zostały wygenerowane podczas uruchamiania skryptu, są wyświetlane w oknie konsoli.

 [Przykładowe Runspace04](./runspace04-sample.md) w tym przykładzie pokazano, jak [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy do uruchamiania poleceń oraz jak catch kończący błędów, które są zgłaszane w przypadku uruchamiania polecenia. Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy. W rezultacie obiekty nie są zwracane i generowany jest błąd powodujący zakończenie.

 [Przykładowe Runspace05](./runspace05-sample.md) w tym przykładzie przedstawiono sposób dodawania przystawki do [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt cmdlet przystawki jest dostępne po otwarciu obszaru działania. Ta przystawka udostępnia polecenia cmdlet Get-Proc (zdefiniowane przez [przykładowe GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) uruchamiane synchronicznie przy użyciu [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

 [Przykładowe Runspace06](./runspace06-sample.md) w tym przykładzie przedstawiono sposób dodawania modułu, aby [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt moduł jest załadowany po otwarciu obszaru działania. Moduł zawiera polecenia cmdlet Get-Proc (zdefiniowany przez [przykładowe GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) uruchamiane synchronicznie przy użyciu [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

 [Przykładowe Runspace07](./runspace07-sample.md) w tym przykładzie pokazano, jak utworzyć obszar działania, a następnie użyj tego obszaru działania na dwa polecenia cmdlet były uruchamiane synchronicznie przy użyciu [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

 [Przykładowe Runspace08](./runspace08-sample.md) w tym przykładzie przedstawiono sposób dodawania polecenia i argumentów do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu i jak polecenia były uruchamiane synchronicznie.

 [Przykładowe Runspace09](./runspace09-sample.md) w tym przykładzie pokazano, jak dodać skrypt do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu oraz sposobu uruchamiania skryptu asynchronicznie. Zdarzenia są używane do obsługi danych wyjściowych skryptu.

 [Przykładowe Runspace10](./runspace10-sample.md) w tym przykładzie pokazano, jak utworzyć domyślny początkowy stan sesji, jak dodać polecenia cmdlet, aby [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), jak utworzyć obszar działania, który używa Stan sesji początkowej oraz sposobu uruchamiania polecenia przy użyciu [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

 [Przykładowe Runspace11](./runspace11-sample.md) to pokazuje, jak używać [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) klasy, aby utworzyć polecenie proxy, który wywołuje istniejące polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów. Polecenie proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania. Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.

## <a name="see-also"></a>Zobacz też
