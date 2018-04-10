---
ms.date: 08/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.1
ms.openlocfilehash: 9df21afe52e79dc248871b999afead21f8678d52
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51"></a>Windows Management Framework (WMF) 5.1 #

Program WMF umożliwia użytkownikom aktualizowanie istniejących systemów Windows do wersji składników programu PowerShell, usługi WMI, usługi WinRM i funkcji Rejestrowanie spisu oprogramowania (SIL, Software Inventory Logging), które zostały wydane z systemem Windows Server 2016.

Program WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2. Oferuje on szereg ulepszeń w porównaniu z programem WMF 5.0 RTM, w tym:

- Nowe polecenia cmdlet: lokalni użytkownicy i grupy; Get-ComputerInfo
- Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA
- Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB
- Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell
- Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet
- Odpowiedzi na wiele problemów i żądań użytkowników

Aby dowiedzieć się więcej na temat nowości w tej wersji, przejrzyj tematy w artykule dotyczącym [nowych scenariuszy i funkcji](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).

W temacie dotyczącym [instalowania i konfigurowania](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) podano listę wymagań i instrukcje dotyczące instalacji programu WMF.

W temacie dotyczącym [zgodności](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) znajduje się lista wersji programu WMF, które można zainstalować w poszczególnych wydaniach systemu Windows.

W temacie dotyczącym [zgodności produktów](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) znajduje się lista aplikacji firmy Microsoft, które do tego momentu nie zostały zatwierdzone do użycia z programem WMF 5.1.

Szczegóły dotyczące składników WMF można znaleźć w dokumentacji MSDN:

- [PowerShell 5.1](https://docs.microsoft.com/en-us/powershell/)
- [WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)
- [WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)
- [Rejestrowanie spisu oprogramowania](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)