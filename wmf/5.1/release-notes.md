---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055585"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Windows Management Framework (WMF) 5.1 — informacje o wersji

Program WMF 5.1 obejmuje składniki programu PowerShell, usługi WMI, usługi WinRM i rejestrowania spisu oprogramowania (SIL), które zostały wydane z systemem Windows Server 2016.
Program WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2. Oferuje on szereg ulepszeń w porównaniu z programem WMF 5.0 RTM, w tym:

- Nowe polecenia cmdlet: lokalni użytkownicy i grupy; Get-ComputerInfo
- Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA
- Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB
- Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell
- Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet
- Odpowiedzi na wiele problemów i żądań użytkowników

**Ważne uwagi:**

- **Program WMF 5.1 wymaga programu .NET Framework 4.5.2** (lub nowszy). Instalacja się powiedzie, ale najważniejsze funkcje zakończy się niepowodzeniem, jeśli .NET 4.5.2 (lub nowszej) nie jest zainstalowany. Instrukcje są dostępne w [Zainstaluj i skonfiguruj program WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tematu.
- WMF 5.1 w wersji zapoznawczej, należy odinstalować przed zainstalowaniem programu WMF 5.1 RTM.
- Program WMF 5.1 można zainstalować bezpośrednio przez program WMF 5.0 lub WMF 4.0.
- Jest __niewymagane__ instalacji programu WMF 4.0 przed zainstalowaniem programu WMF 5.1 na Windows 7 i Windows Server 2008 R2. Który problem w wersji programu WMF 5.1 w wersji zapoznawczej i zostanie rozwiązany.
