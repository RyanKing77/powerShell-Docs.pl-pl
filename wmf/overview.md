---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Oprogramowanie Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940394"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) udostępnia interfejs spójnego sposobu zarządzania dla systemu Windows. WMF umożliwia bezproblemowe zarządzanie różne wersje klienta systemu Windows i Windows Server. Pakietów Instalatora WMF zawierają aktualizacje funkcje zarządzania i są dostępne w starszych wersjach systemu Windows.

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

|Wersja systemu operacyjnego  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |Jest dostarczany w polu|            |            |             |            |
|10 systemu Windows                |Jest dostarczany w polu|Jest dostarczany w polu|            |             |            |
|Windows Server 2012 R2    |Tak         |Tak         |Jest dostarczany w polu|             |            |
|Windows 8.1               |Tak         |Tak         |Jest dostarczany w polu|             |            |
|Windows Server 2012       |Tak         |Tak         |Tak         |Jest dostarczany w polu |            |
|Windows 8                 |            |            |            |Jest dostarczany w polu |            |
|Windows Server 2008 R2 z dodatkiem SP1|Tak         |Tak         |Tak         |Tak          |Jest dostarczany w polu|
|Windows 7 z dodatkiem SP1             |Tak         |Tak         |Tak         |Tak          |Jest dostarczany w polu|
|Windows Server 2008 z dodatkiem SP2   |            |            |            |Tak          |Tak         |
|Windows Vista             |            |            |            |             |Tak         |
|Windows Server 2003       |            |            |            |             |Tak         |
|Windows XP                |            |            |            |Tak          |            |

**W polu jest dostarczany**: funkcje określonej wersji programu WMF zostały wysłane w wskazanych wersja klienta systemu Windows lub Windows Server.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
