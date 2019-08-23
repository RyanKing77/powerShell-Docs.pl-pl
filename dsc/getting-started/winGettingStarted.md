---
ms.date: 08/15/2019
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Wprowadzenie do konfiguracji żądanego stanu (DSC) dla systemu Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988928"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Wprowadzenie do konfiguracji żądanego stanu (DSC) dla systemu Windows

W tym temacie wyjaśniono, jak rozpocząć pracę z konfiguracją żądanego stanu (DSC) programu PowerShell dla systemu Windows.
Aby uzyskać ogólne informacje na temat DSC, zobacz Wprowadzenie [do konfiguracji żądanego stanu programu Windows PowerShell](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Obsługiwane wersje systemu operacyjnego Windows

Obsługiwane są następujące wersje:

- Windows Server 2019
- Windows Server 2016
- 2012R2 systemu Windows Server
- Windows Server 2012
- Windows Server 2008 R2 z dodatkiem SP1
- Windows 10
- Windows 8.1
- Windows 7

Autonomiczna jednostka SKU produktu [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) nie zawiera implementacji żądanego stanu konfiguracją, więc nie może być zarządzana przez program PowerShell DSC lub konfigurację stanu Azure Automation.

## <a name="installing-dsc"></a>Instalowanie DSC

Konfiguracja żądanego stanu programu PowerShell jest dołączona do systemu Windows i aktualizowana przy użyciu środowiska Windows Management Framework.
Najnowsza wersja to [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> Aby zarządzać maszyną za pomocą usługi DSC, nie trzeba włączać funkcji DSC-Service w systemie Windows Server.
> Ta funkcja jest wymagana tylko w przypadku kompilowania wystąpienia serwera ściągania systemu Windows.

## <a name="using-dsc-for-windows"></a>Korzystanie z usługi DSC dla systemu Windows

W poniższych sekcjach wyjaśniono, jak tworzyć i uruchamiać konfiguracje DSC na komputerach z systemem Windows.

### <a name="creating-a-configuration-mof-document"></a>Tworzenie dokumentu MOF konfiguracji

Słowo kluczowe konfiguracji programu Windows PowerShell służy do tworzenia konfiguracji.
Poniższe kroki opisują Tworzenie dokumentu konfiguracji przy użyciu programu Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Zdefiniuj konfigurację i Wygeneruj dokument konfiguracji:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>Instalowanie modułu zawierającego zasoby DSC

Konfiguracja żądanego stanu programu Windows PowerShell obejmuje wbudowane moduły zawierające zasoby DSC.
Moduły można również ładować ze źródeł zewnętrznych, takich jak Galeria programu PowerShell, przy użyciu poleceń cmdlet PowerShellGet.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Zastosuj konfigurację do maszyny

Dokumenty konfiguracyjne (pliki MOF) można zastosować do maszyny za pomocą polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Pobierz bieżący stan konfiguracji

Polecenie cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) wykonuje zapytanie o bieżący stan maszyny i zwraca bieżące wartości konfiguracji.

`Get-DscConfiguration`

Polecenie cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) zwraca bieżącą meta-konfiguracyjną zastosowana do maszyny.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Usuń bieżącą konfigurację z komputera

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Skonfiguruj ustawienia w Configuration Manager lokalnym

Zastosuj plik MOF konfiguracji meta do maszyny przy użyciu polecenia cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .
Wymaga ścieżki do pliku MOF konfiguracji meta.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Pliki dziennika konfiguracji żądanego stanu programu Windows PowerShell

Dzienniki usługi DSC są zapisywane w dzienniku zdarzeń systemu Windows w ścieżce `Microsoft-Windows-Dsc/Operational`.
Dodatkowe dzienniki do celów debugowania można włączyć, wykonując czynności opisane w sekcji [gdzie znajdują się dzienniki zdarzeń DSC](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
