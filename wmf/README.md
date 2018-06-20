---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Oprogramowanie Windows Management Framework (WMF)
ms.openlocfilehash: ae50e8d1495d7075163714ed873940d2d1d19b8e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221871"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) jest mechanizm dostarczania, zapewniająca interfejsu zarządzania zgodny w różnych odmian systemu Windows i Windows Server.
Instalację programu WMF klienci uzyskują swobodne współdziałanie między kombinacje systemów operacyjnych w ich środowisku.
WMF sprawia, że aktualizacje do funkcji zarządzania w danej wersji systemu Windows i Windows Server można zainstalować w niższych wersjach (zwykle 2 wersje niższe) systemu Windows i Windows Server.

Instalacja WMF dodaje i/lub aktualizuje następujące funkcje:

- Windows PowerShell
- Konfiguracja żądanego stanu programu Windows PowerShell (DSC)
- Środowisko zintegrowane skrypt programu PowerShell systemu Windows (ISE)
- Zdalne zarządzanie systemem Windows (WinRM)
- Instrumentacja zarządzania Windows (WMI)
- Usługi sieci Web programu PowerShell systemu Windows (rozszerzenie OData IIS zarządzania)
- Rejestrowanie spisu oprogramowania (SIL)
- Menedżer serwera modelu wspólnych informacji dostawcy

## <a name="wmf-release-notes"></a>Informacje o wersji platformy WMF

Aby poznać różne udoskonalenia środowiska PowerShell i inne składniki danej WMF, zapoznaj się poniższe łącza, aby przejrzeć informacje o wersji:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Dostępność WMF w systemach operacyjnych Windows

| Wersja systemu operacyjnego | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Jest dostarczany w polu |  |  |  |  |
| 10 systemu Windows | Jest dostarczany w polu | Jest dostarczany w polu  | | | |
| Windows Server 2012 R2| Tak | Tak | Jest dostarczany w polu |  |  |
| Windows 8.1 | Tak | Tak |  Jest dostarczany w polu |  |  |
| Windows Server 2012 | Tak | Tak | Tak |  Jest dostarczany w polu | |
| Windows 8 |  |  |  | Jest dostarczany w polu | |
| Windows Server 2008 R2 z dodatkiem SP1 | Tak | Tak | Tak |  Tak| Jest dostarczany w polu |
| Windows 7 z dodatkiem SP1  | Tak | Tak | Tak | Tak | Jest dostarczany w polu |
| Windows Server 2008 z dodatkiem SP2 | | | | Tak | Tak |
| Windows Vista | | | | | Tak |
| Windows Server 2003| | | |  | Tak |
| Windows XP | | | |  | Tak |

**"Jest dostarczany w polu"**: funkcje `specified WMF` zostały wysłane w wskazanych wersji systemu Windows i Windows Server.
W związku z tym `specified WMF` nie muszą być zainstalowane w wersjach systemu operacyjnego wskazane.
