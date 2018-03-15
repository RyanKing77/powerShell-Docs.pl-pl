---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galerii programu powershell, polecenia cmdlet, psgallery, psget
title: Galerii programu PowerShell
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a>Galerii programu PowerShell

Galerii programu PowerShell jest centralnym repozytorium zawartości programu PowerShell. Nowe polecenia programu PowerShell lub zasobów konfiguracji żądanego stanu (DSC) można znaleźć w galerii.

## <a name="powershellget-overview"></a>Omówienie PowerShellGet

Moduł PowerShellGet zawiera polecenia cmdlet do wykrywania, instalowania, aktualizowanie i publikowanie programu PowerShell artefaktów, takich jak moduły, zasobów usługi Konfiguracja DSC, możliwości roli i skrypty z [galerii programu PowerShell](https://www.PowerShellGallery.com) i innych prywatnej repozytoriów.

## <a name="getting-started-with-the-gallery"></a>Wprowadzenie do korzystania z galerii

Instalowanie elementów z galerii wymaga najnowszej wersji modułu PowerShellGet, która jest dostępna w systemie Windows 10, w Windows Management Framework (WMF) w wersji 5.0 lub na podstawie pliku MSI Instalatora (PowerShell 3 i 4).

- [**Pobierz system Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Pobierz WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), lub
- [**Pobierz instalatora MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Przy użyciu najnowszych [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modułu, można wykonywać następujące czynności:

-   Wyszukiwanie za pomocą elementów galerii z [Znajdź moduł](https://go.microsoft.com/fwlink/?LinkId=821658) i [Znajdź skryptu](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Zapisuje elementy do systemu z galerii [moduł zapisywania](https://go.microsoft.com/fwlink/?LinkId=821669) i [zapisywania skryptu](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Instalacji elementów z galerii [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663) i [skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Przekaż elementów galerii z [modułu publikowania](https://go.microsoft.com/fwlink/?LinkId=821666) i [publikowania skryptu](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Dodawanie niestandardowego repozytorium z [PSRepository rejestru](https://go.microsoft.com/fwlink/?LinkId=821668)

Zapoznaj się z [wprowadzenie](psgallery/psgallery_gettingstarted.md) strony, aby uzyskać więcej informacji na temat korzystania z galerii PowerShellGet poleceń. Można również uruchomić *Update-Help — moduł PowerShellGet* instalacji lokalnej pomocy dla polecenia.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

**PowerShellGet** module wymaga **programu PowerShell 3.0 lub nowszej**.

W związku z tym **PowerShellGet** wymaga jednego z następujących systemów operacyjnych:

- 10 systemu Windows
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 z dodatkiem SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 z dodatkiem SP1

**PowerShellGet** również wymaga programu .NET Framework 4.5 lub nowszej. Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Masz pytania? Masz opinię?

Więcej informacji o galerii programu PowerShell i PowerShellGet znajdują się w [wprowadzenie](psgallery/psgallery_gettingstarted.md) strony. Podaj opinii i raportu problemów przy użyciu [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

