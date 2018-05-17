---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3679c13c2d28f28f3102b24f6369f1dc264d6884
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="installation-instructions"></a>Instrukcje dotyczące instalacji

Pobierz pakiet poprawne dla systemu operacyjnego i architektura:

| System operacyjny       | Architektura | Nazwa pakietu              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Systemu Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 z dodatkiem SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 z dodatkiem SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Aby zainstalować WMF 5.0 z Eksploratora Windows (lub Eksploratora plików w systemie Windows Server 2012 R2 i Windows 8.1):**

1. Przejdź do folderu, do którego został pobrany plik MSU.

2. Kliknij dwukrotnie MSU go uruchomić.

**Aby zainstalować WMF 5.0 z wiersza polecenia:**

1. Po pobraniu poprawny pakiet dla architektury komputera, Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator). W opcji instalacji Server Core systemu Windows Server 2012 R2 lub Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1 wiersz polecenia z podwyższonym poziomem uprawnień użytkownika domyślnie otwierany.

2. Przejdź do folderu, do którego została pobrana lub skopiować pakiet instalacyjny programu WMF 5.0.

3. Uruchom jedno z następujących poleceń:
    - Uruchom na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 **Win8.1AndW2K12R2-KB3134758-x64.msu/quiet**.
    - Na komputerach z systemem Windows Server 2012 Uruchom **W2K12-KB3134759-x64.msu/quiet**.
    - Na komputerach z systemem Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1 x 64, uruchom **Win7AndW2K8R2-KB3134760-x64.msu/quiet**.
    - Uruchom na komputerach z systemem Windows 8.1 x86 **systemu Win8.1-KB3134758-x86.msu/quiet**.
    - Na komputerach z systemem Windows 7 z dodatkiem SP1 x 86, uruchom **quiet Win7-KB3134760-x86.msu**.

**Uwagi dodatkowe instalacji dla systemu Windows Server 2008 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:**

Upewnij się, że zostały spełnione następujące wymagania wstępne:
- Najnowszy dodatek service pack jest zainstalowany.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) jest zainstalowany

*Usługa WinRM zależności:* Windows PowerShell Desired stan konfiguracji (DSC) jest zależna od usługi WinRM. Usługa WinRM nie jest włączona domyślnie w systemie Windows Server 2008 R2 i Windows 7. Aby włączyć usługę WinRM, w programie Windows PowerShell z podwyższonym poziomem uprawnień, uruchomienie sesji **Set-WSManQuickConfig**.
