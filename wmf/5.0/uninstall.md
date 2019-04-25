---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057529"
---
# <a name="uninstallation-instructions"></a>Instrukcje dotyczące odinstalowywania

## <a name="using-command-prompt"></a>Przy użyciu wiersza polecenia
1.  Otwórz **wiersza polecenia.**
2.  Uruchom [Windows Update autonomicznego uruchamiania](https://support.microsoft.com/en-us/kb/934307) jak pokazano poniżej:

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

## <a name="using-control-panel"></a>Za pomocą Panelu sterowania
1.  Otwórz **w Panelu sterowania.**
2.  Otwórz **programy**, a następnie otwórz **Odinstaluj program.**
3.  Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**
4.  Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji. Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*. Kliknij przycisk **odinstalować.**
