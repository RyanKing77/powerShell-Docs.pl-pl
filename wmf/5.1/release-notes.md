---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.1
ms.openlocfilehash: 5c3075eda5482cc6a43bd237fe4fca0064136753
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Informacje o wersji Windows Management Framework (WMF) 5.1 #

WMF 5.1 zawiera składniki programu PowerShell, usługi WMI Usługa WinRM i rejestrowania spisu oprogramowania (SIL), które zostały wydane z systemem Windows Server 2016.
Program WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2. Oferuje on szereg ulepszeń w porównaniu z programem WMF 5.0 RTM, w tym:

- Nowe polecenia cmdlet: lokalni użytkownicy i grupy; Get-ComputerInfo
- Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA
- Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB
- Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell
- Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet
- Odpowiedzi na wiele problemów i żądań użytkowników

**Ważne informacje:**

- **WMF 5.1 wymaga programu .NET Framework 4.5.2** (lub nowszej). Instalacja zostanie wykonana pomyślnie, ale najważniejsze funkcje zakończy się niepowodzeniem, jeśli .NET 4.5.2 (lub nowszej) nie jest zainstalowany. Instrukcje są dostępne w [Instalowanie i konfigurowanie 5.1 WMF ](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tematu.
- Podgląd 5.1 WMF należy odinstalować przed zainstalowaniem WMF 5.1 RTM.
- WMF 5.1 mogą być zainstalowane bezpośrednio za pośrednictwem WMF 5.0 lub WMF 4.0.
- Jest __niewymagane__ do zainstalowania WMF 4.0 przed zainstalowaniem programu WMF 5.1 w systemie Windows 7 i Windows Server 2008 R2. Czy problem w wersji zapoznawczej 5.1 WMF i został rozwiązany.
