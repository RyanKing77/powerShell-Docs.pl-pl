---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Rejestrowanie konfiguracji JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017867"
---
# <a name="registering-jea-configurations"></a>Rejestrowanie konfiguracji JEA

Po utworzeniu [możliwości roli](role-capabilities.md) i [pliku konfiguracji sesji](session-configurations.md) , ostatnim krokiem jest zarejestrowanie punktu końcowego jea. Zarejestrowanie punktu końcowego JEA w systemie sprawia, że punkt końcowy jest dostępny do użycia przez użytkowników i aparaty automatyzacji.

## <a name="single-machine-configuration"></a>Konfiguracja pojedynczego komputera

W przypadku małych środowisk można wdrożyć JEA, rejestrując plik konfiguracji sesji za pomocą polecenia cmdlet [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .

Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:

- Co najmniej jedna rola została utworzona i umieszczona w folderze **RoleCapabilities** modułu PowerShell.
- Plik konfiguracji sesji został utworzony i przetestowany.
- Użytkownik rejestrujący konfigurację JEA ma prawa administratora w systemie.
- Wybrano nazwę punktu końcowego JEA.

Nazwa punktu końcowego JEA jest wymagana, gdy użytkownicy łączą się z systemem przy użyciu JEA. Polecenie cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) wyświetla nazwy punktów końcowych w systemie. Punkty końcowe rozpoczynające `microsoft` się od są zwykle dostarczane z systemem Windows. `microsoft.powershell` Punkt końcowy jest domyślnym punktem końcowym używanym podczas nawiązywania połączenia z punktem końcowym zdalnego programu PowerShell.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Uruchom następujące polecenie, aby zarejestrować punkt końcowy.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Poprzednie polecenie ponownie uruchamia usługę WinRM w systemie. Kończy wszystkie sesje komunikacji zdalnej programu PowerShell i wszystkie bieżące konfiguracje DSC. Zaleca się przełączenie maszyn produkcyjnych do trybu offline przed uruchomieniem polecenia, aby uniknąć zakłócania operacji działania biznesowego.

Po zarejestrowaniu możesz przystąpić do [korzystania z jea](using-jea.md). Plik konfiguracji sesji można usunąć w dowolnym momencie. Plik konfiguracji nie jest używany po rejestracji punktu końcowego.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguracja wielomaszynowa z konfiguracją DSC

Podczas wdrażania JEA na wielu maszynach najprostszy model wdrażania używa zasobu [konfiguracji żądanego stanu (DSC)](/powershell/dsc/overview) jea, aby szybko i spójnie wdrożyć jea na każdym komputerze.

Aby wdrożyć JEA za pomocą DSC, upewnij się, że zostały spełnione następujące wymagania wstępne:

- Co najmniej jedna możliwość roli została utworzona i dodana do modułu programu PowerShell.
- Moduł programu PowerShell zawierający role jest przechowywany w udziale plików (tylko do odczytu) dostępnym na poszczególnych komputerach.
- Określono ustawienia konfiguracji sesji. Nie musisz tworzyć pliku konfiguracji sesji podczas korzystania z zasobu JEA DSC.
- Masz poświadczenia zezwalające na akcje administracyjne na każdej maszynie lub dostęp do serwera ściągania DSC używanego do zarządzania maszynami.
- Pobrano [zasób jea DSC](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Utwórz konfigurację DSC dla punktu końcowego JEA na maszynie docelowej lub serwerze ściągania. W tej konfiguracji zasób **JustEnoughAdministration** DSC definiuje plik konfiguracji sesji, a zasób **pliku** kopiuje możliwości roli z udziału plików.

Następujące właściwości można skonfigurować przy użyciu zasobu DSC:

- Definicje ról
- Grupy kont wirtualnych
- Nazwa konta usługi zarządzanego przez grupę
- Katalog transkrypcji
- Dysk użytkownika
- Reguły dostępu warunkowego
- Skrypty uruchamiania dla sesji JEA

Składnia dla każdej z tych właściwości w konfiguracji DSC jest zgodna z plikiem konfiguracji sesji programu PowerShell.

Poniżej znajduje się Przykładowa konfiguracja DSC dla ogólnego modułu konserwacji serwera. Przyjęto założenie, że prawidłowy moduł programu PowerShell zawierający możliwości roli znajduje `\\myfileshare\JEA` się w udziale plików.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Następnie konfiguracja jest stosowana w systemie przez bezpośrednie wywołanie [Configuration Manager lokalnego](/powershell/dsc/managing-nodes/metaConfig) lub zaktualizowanie [konfiguracji serwera ściągania](/powershell/dsc/pull-server/pullServer).

Zasób DSC umożliwia również zastąpienie domyślnego punktu końcowego **programu Microsoft. PowerShell** . Po zastąpieniu zasób automatycznie rejestruje punkt końcowy kopii zapasowej o nazwie **Microsoft. PowerShell.** z ograniczeniami. Punkt końcowy kopii zapasowej ma domyślną listę ACL usługi WinRM umożliwiającą użytkownikom zdalnego zarządzania i członkom lokalnej grupy administratorów dostęp do niej.

## <a name="unregistering-jea-configurations"></a>Wyrejestrowywanie konfiguracji JEA

Polecenie cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) usuwa punkt końcowy jea. Wyrejestrowanie punktu końcowego JEA uniemożliwia nowym użytkownikom tworzenie nowych sesji usługi JEA w systemie. Umożliwia również zaktualizowanie konfiguracji JEA przez ponowne zarejestrowanie zaktualizowanego pliku konfiguracji sesji przy użyciu tej samej nazwy punktu końcowego.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wyrejestrowanie punktu końcowego JEA powoduje ponowne uruchomienie usługi WinRM. Spowoduje to przerwanie większości operacji zarządzania zdalnego w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektórych narzędzi do zarządzania. Wyrejestruj punkty końcowe programu PowerShell tylko podczas planowanych okien obsługi.

## <a name="next-steps"></a>Następne kroki

[Testowanie punktu końcowego JEA](using-jea.md)
