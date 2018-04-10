---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Przygotowanie do korzystania z programu Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getting-ready-to-use-windows-powershell"></a>Przygotowanie do korzystania z programu Windows PowerShell
Podczas instalowania i uruchamiania programu Windows PowerShell, należy wziąć pod uwagę następujące opcje konfiguracji. Te zadania można wykonać w dowolnym momencie.

- **Zainstalowania plików pomocy.** Polecenia cmdlet, które znajdują się w środowisku Windows PowerShell 3.0 nie są dostarczane z plików pomocy. Można jednak użyć [Update-Help](/powershell/module/microsoft.powershell.core/update-help) polecenia cmdlet, aby pobrać i zainstalować najnowszych plików pomocy na komputerze. Jeśli pliki są już zainstalowane, możesz użyć [Get-Help](/powershell/module/microsoft.powershell.core/get-help) polecenia cmdlet, aby je wyświetlić w prawo w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Jeśli nie chcesz zainstalować pliki pomocy, można nadal odczytywać tematy Pomocy online. Aby znaleźć wersję online każdego tematu pomocy polecenia cmdlet, wpisz: `Get-Help <CmdletName> -Online`. Aby przeglądać zobacz Tematy Pomocy programu Windows PowerShell [dokumentacji programu PowerShell](/powershell/scripting).

- **Uruchom skrypty.** Aby zabezpieczyć środowiska Windows PowerShell, domyślne zasady wykonywania na programie Windows PowerShell jest **Restricted**. Ta zasada umożliwia uruchamianie poleceń cmdlet, ale nie skryptów. Aby uruchamiać skrypty, należy użyć [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) polecenia cmdlet, aby zmienić zasady wykonywania **AllSigned** lub **RemoteSigned**. Tylko członkowie grupy Administratorzy na komputerze można uruchomić tego polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Włączenie komunikacji zdalnej.** System jest już skonfigurowana do uruchomienia poleceń zdalnych na innych komputerach. W systemie Windows Server 2012 R2 i Windows Server 2012 system został również skonfigurowany do odbierania poleceń zdalnych, oznacza to, aby zezwolić innych komputerów do uruchamiania poleceń zdalnych na komputerze lokalnym. Aby umożliwić komputerom z innymi wersjami systemu Windows do odbierania poleceń zdalnych, uruchom [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) polecenia cmdlet na komputerze, na którym chcesz zarządzać zdalnie. Tylko członkowie grupy Administratorzy na komputerze można uruchomić tego polecenia cmdlet. Aby uzyskać więcej informacji, zobacz [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    Uwaga: Jeśli zdalnych jest włączona na komputerze, na którym działa program Windows PowerShell 2.0, usług zdalnych jest nadal włączone po zainstalowaniu systemu Windows Management Framework 3.0. Jednak w systemie Windows Server 2008 (nie systemu Windows Server 2008 R2), należy ponownie włączyć komunikację zdalną po zainstalowaniu systemu Windows Management Framework 3.0.

## <a name="see-also"></a>Zobacz też
- [Instalowanie programu Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Uruchamianie środowiska Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)