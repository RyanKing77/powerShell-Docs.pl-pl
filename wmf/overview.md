---
ms.date: 04/19/2019
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 6d25b4025bbc86f6be0e5c74db9f1fbe6705d816
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055449"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) udostępnia interfejs spójne środowisko zarządzania dla Windows. Program WMF umożliwia bezproblemowe zarządzanie różnymi wersjami klienta Windows i Windows Server. Pakiety instalacyjne WMF zawierają aktualizacje funkcji zarządzania i są dostępne dla starszych wersji systemu Windows.

Instalacja programu WMF dodaje i/lub aktualizuje następujące funkcje:

- Windows PowerShell
- Program Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell zintegrowane skryptów środowiska (ISE)
- Usługa Windows Remote Management (WinRM)
- Instrumentacja zarządzania Windows (WMI)
- Windows PowerShell Web Services (rozszerzenie OData IIS zarządzania)
- Rejestrowanie spisu oprogramowania (SIL)
- Dostawcy interfejsu CIM Menedżera serwera

## <a name="wmf-release-notes"></a>Informacje o wersji programu WMF

Aby poznać różne ulepszenia w programie PowerShell i inne składniki danej platformy WMF, zapoznaj się poniższe łącza, aby zapoznać się z informacjami o wersji:

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>WMF dostępność w różnych systemach operacyjnych Windows

|        Wersja systemu operacyjnego         | [WMF 5.1][]  | WMF 5.0<br>*Okres wsparcia technicznego upływa* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Dostarczany skrzynkach odbiorczych |                             |              |              |              |
| Windows Server 2016                     | Dostarczany skrzynkach odbiorczych |                             |              |              |              |
| Windows 10                              | Dostarczany skrzynkach odbiorczych | Dostarczany skrzynkach odbiorczych                |              |              |              |
| Windows Server 2012 R2                  | Tak          | Tak                         | Dostarczany skrzynkach odbiorczych |              |              |
| Windows 8.1                             | Tak          | Tak                         | Dostarczany skrzynkach odbiorczych |              |              |
| Windows Server 2012                     | Tak          | Yes                         | Tak          | Dostarczany skrzynkach odbiorczych |              |
| Windows 8<br>*Okres wsparcia technicznego upływa*           |              |                             |              | Dostarczany skrzynkach odbiorczych |              |
| Windows Server 2008 R2 z dodatkiem SP1              | Tak          | Yes                         | Yes          | Tak          | Dostarczany skrzynkach odbiorczych |
| Windows 7 SP1                           | Tak          | Yes                         | Yes          | Tak          | Dostarczany skrzynkach odbiorczych |
| Windows Server 2008 SP2                 |              |                             |              | Tak          | Tak          |
| Windows Vista<br>*Okres wsparcia technicznego upływa*       |              |                             |              |              | Tak          |
| Windows Server 2003<br>*Okres wsparcia technicznego upływa* |              |                             |              |              | Tak          |
| Windows XP<br>*Okres wsparcia technicznego upływa*          |              |                             |              | Tak          | Tak          |

- **Jest dostarczany w polu**: Funkcje określonej wersji programu WMF zostały wysłane przez wskazanego wersję klienta Windows lub Windows Server.
- **Okres wsparcia technicznego upływa**: Te produkty nie są już obsługiwane przez firmę Microsoft. Należy uaktualnić do nowej wersji, która jest obsługiwana. Aby uzyskać więcej informacji, zobacz [Zasady cyklu pomocy firmy Microsoft][] strony.

> [!NOTE]
> Instalator programu WMF 5.0 nie jest już dostępne lub nie jest obsługiwany. Została zastąpiona przez program WMF 5.1.

[Zasady cyklu pomocy firmy Microsoft]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
