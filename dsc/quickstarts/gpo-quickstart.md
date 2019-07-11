---
ms.date: 07/09/2019
keywords: DSC, obiekt zasad grupy, programu powershell, konfiguracji, ustawienia
title: Przewodnik Szybki Start — zasady grupy konwersji do DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785138"
---
> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Szybki Start: Zasady grupy konwersji do DSC

Konfiguracja DSC można wygenerować z linii bazowej, zasady grupy lub usługi Azure Security Center. [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) moduł zawiera następujące polecenia do wykonywania tego zadania.

- `ConvertFrom-GPO` — Przechowywane jako pliki grupy konwertuje zasad. Można również określić katalogu zawierającego wiele zasad, które mają zostać połączone w jedną konfigurację.
  - Aby wyeksportować zasady grupy w danym środowisku, należy użyć [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) polecenia cmdlet, lub postępować zgodnie z instrukcjami wyświetlanymi w [Wyeksportuj obiekt zasad grupy do pliku](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` — Konwertuje odniesienia Menedżera zgodności zabezpieczeń, przechowywane jako `.xml` plików.
- `ConvertFrom-ASC` — Centrum zabezpieczeń Azure konwertuje odniesienia, przechowywane jako `.json` plików.
- `Merge-GPOs` — Grupy konwertuje zasady są stosowane do komputera docelowego.

Polecenia cmdlet wymienione powyżej konwertowanie linię bazową na DSC `.mof` pliku. Możesz również dane wyjściowe skryptu konfiguracji (`.ps1`), który można edytować i ponownie skompilować. Polecenia cmdlet wykryć błędy kompilacji dla brakujących zasobów lub zasobu zduplikowanych bloków. Bloki zasobów, które mogłoby spowodować błędy kompilacji są oznaczone jako komentarz.

Poniższy przykład konwertuje [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) do skryptu konfiguracji DSC (`.ps1`) i `.mof` pliku.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Po uruchomieniu polecenia, zostaną wyświetlone dwa pliki w domyślnym katalogu "Wyjście" utworzonych w ramach Twojej bieżącej ścieżce.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Każdy węzeł zarządzanych muszą także następujące dwa moduły:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** jest rozwiązanie opracowane przez społeczność, aby dla członków społeczności pochodzą z maintainers projektu, a nie od firmy Microsoft mogą szybciej odnajdywać obsługi DSC. Można otworzyć nowego problemu dla **BaselineManagement** na [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Następne kroki

- Przekazywanie skryptu konfiguracji do usługi Azure Automation stan konfiguracji, zobacz [wprowadzenie](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Dodaj **SecurityPolicyDSC** i **AuditPolicyDSC** modułów, aby Twoje [konta usługi Automation](/azure/automation/shared-resources/modules).
- Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).
