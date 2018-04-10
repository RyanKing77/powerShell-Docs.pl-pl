---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a>Instrukcje dotyczące odinstalowywania

## <a name="using-command-prompt"></a>Przy użyciu wiersza polecenia
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

## <a name="using-control-panel"></a>Za pomocą Panelu sterowania
1.  Otwórz **w Panelu sterowania.**
2.  Otwórz **programy**, następnie otwórz **Odinstaluj program.**
3.  Kliknij przycisk **Wyświetl zainstalowane aktualizacje.**
4.  Wybierz **Windows Management Framework 5.0** z listy zainstalowanych aktualizacji. Odpowiada to *KB3134758*, *KB3134759*, lub *KB3134760*. Kliknij przycisk **odinstalować.**