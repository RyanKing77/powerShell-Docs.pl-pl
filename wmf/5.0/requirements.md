---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 510e1baa2933932cfd4c3bcb4e0973f3eb8095f3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="system-requirements"></a>Wymagania systemowe

- Zainstaluj najnowsze aktualizacje systemu Windows przed zainstalowaniem WMF 5.0 RTM.
- WMF 5.0 RTM, można zainstalować tylko w następujących systemach operacyjnych:

    | System operacyjny       | Wersje         | Wymagania wstępne        |  Łącza pakietu |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 z dodatkiem SP1 | Wszystkie oprócz IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) i [.NET Framework 4.5 lub nowszej](https://msdn.microsoft.com/library/5a4x27ek.aspx) są zainstalowane| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 z dodatkiem SP1 | Wszystko | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) i [.NET Framework 4.5 lub nowszej](https://msdn.microsoft.com/library/5a4x27ek.aspx) są zainstalowane | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Instrukcje dotyczące instalacji

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Aby zainstalować WMF 5.0 z Eksploratora Windows (lub Eksploratora plików):

1. Przejdź do folderu, do którego został pobrany plik MSU.

2. Kliknij dwukrotnie MSU go uruchomić.

### <a name="to-install-wmf-50-from-command-prompt"></a>Aby zainstalować WMF 5.0 z wiersza polecenia:

1. Po pobraniu poprawny pakiet dla architektury komputera, Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator). W opcji instalacji Server Core systemu Windows Server 2012 R2 lub Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1 wiersz polecenia z podwyższonym poziomem uprawnień użytkownika domyślnie otwierany.

2. Przejdź do folderu, do którego została pobrana lub skopiować pakiet instalacyjny programu WMF 5.0.

3. Uruchom jedno z następujących poleceń:
    - Uruchom na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 **Win8.1AndW2K12R2-KB3134758-x64.msu/quiet**.
    - Na komputerach z systemem Windows Server 2012 Uruchom **W2K12-KB3134759-x64.msu/quiet**.
    - Na komputerach z systemem Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1 x 64, uruchom **Win7AndW2K8R2-KB3134760-x64.msu/quiet**.
    - Uruchom na komputerach z systemem Windows 8.1 x86 **systemu Win8.1-KB3134758-x86.msu/quiet**.
    - Na komputerach z systemem Windows 7 z dodatkiem SP1 x 86, uruchom **quiet Win7-KB3134760-x86.msu**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Uwagi dodatkowe instalacji dla systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:

Upewnij się, że zostały spełnione następujące wymagania wstępne:
- Najnowszy dodatek service pack jest zainstalowany.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) jest zainstalowany.
- [.NET framework 4.5 lub nowszej](https://msdn.microsoft.com/library/5a4x27ek.aspx) jest zainstalowany.

**WMF 4.0 zależności**

Systemy Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1 ma wbudowane PowerShell 2.0, WinRM i WMI. Pakiety WMF 3.0 i programu WMF 4.0, które aktualizacje tych składników wbudowanych, zostały wydane po wydaniu systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1. Pakiety Instalowanie/Odinstalowywanie WMF 3.0 i programu WMF 4.0 nie wykryte problemy, w następującej ścieżce uaktualniania:

- Wbudowane--> WMF 4.0
- Wbudowane--> WMF 3.0--> WMF4.0. 

Usunięto wszystkie te problemy w pakietach WMF 4.0. W związku z tym Brak wstępnie wymaganego programu WMF 4.0 do instalowania WMF 5.0 w systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1. Poniżej przedstawiono określonych problemów, które mogą wystąpić, jeśli nie zainstalujesz WMF 4.0 przed uaktualnieniem do wersji WMF 5.0:

- Dziennik zdarzeń przekazany dalej jest niedostępny, a EventCollector dziennika nie jest wyświetlany w Podglądzie zdarzeń po odinstalowaniu WMF 3.0 lub WMF 5.0 (bez wymagań wstępnych WMF 4.0 zainstalowany) w systemie Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 z dodatkiem SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- Dostosowanie *PSModulePath* zmiennej środowiskowej pobiera zresetowana do wartości domyślnej, po uaktualnieniu bezpośrednio z wbudowanych PowerShell 2.0 do WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) lub WMF 3.0 WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) w systemie Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 z dodatkiem SP1.

**Zależności usługi WinRM**

Windows PowerShell Desired stan konfiguracji (DSC) zależy od usługi WinRM. Usługa WinRM nie jest włączona domyślnie w systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1. Aby włączyć usługę WinRM, w programie Windows PowerShell z podwyższonym poziomem uprawnień, uruchomienie sesji **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Instrukcje dotyczące odinstalowywania

### <a name="using-command-prompt"></a>Przy użyciu wiersza polecenia

1.  Otwórz **wiersza polecenia.**

2.  Uruchom [uruchamianie autonomicznej usługi Windows Update](https://support.microsoft.com/en-us/kb/934307) w sposób przedstawiony poniżej:

W systemie Windows Server 2012 R2 i Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
W systemie Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
W systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1:
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Za pomocą Panelu sterowania

1.  Otwórz **w Panelu sterowania.**

2.  Otwórz **programy**, następnie otwórz **Odinstaluj program.**

3.  Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**

4.  Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji. Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*. Kliknij przycisk **odinstalować.**

