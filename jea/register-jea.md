---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie usługi JEA konfiguracji
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726600"
---
# <a name="registering-jea-configurations"></a>Rejestrowanie usługi JEA konfiguracji

Po utworzeniu usługi [możliwości roli](role-capabilities.md) i [plik konfiguracji sesji](session-configurations.md) ostatnim krokiem jest utworzone, można zarejestrować punktu końcowego JEA. Rejestrowanie punktu końcowego JEA w systemie sprawia, że punkt końcowy do użycia przez użytkowników i aparatów automatyzacji.

## <a name="single-machine-configuration"></a>Konfiguracja pojedynczego komputera

W przypadku małych środowisk można wdrożyć JEA, rejestrując się, używając pliku konfiguracji sesji [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.

Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:

- Utworzono i umieszczane w co najmniej jedną rolę **RoleCapabilities** folderu modułu programu PowerShell.
- Utworzono plik konfiguracji sesji i przetestowane.
- Użytkownik, o których rejestrowanie usługi JEA konfiguracji ma prawa administratora w systemie.
- Wybrana nazwa dla punktu końcowego usługi JEA.

Nazwa punktu końcowego usługi JEA jest wymagana, kiedy użytkownicy łączą się systemu przy użyciu technologii JEA. [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) polecenie cmdlet wyświetla listę nazw punktów końcowych w systemie. Punkty końcowe, które zaczyna się `microsoft` zwykle są dostarczane z programem Windows. `microsoft.powershell` Punkt końcowy jest domyślny punkt końcowy używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell.

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
> Poprzednie polecenie uruchamia ponownie usługę WinRM w systemie. To kończy wszystkie sesje komunikacji zdalnej programu PowerShell i wszystkie trwające operacje konfiguracji DSC. Zalecamy na komputerach produkcyjnych w trybie offline należy wykonać przed uruchomieniem polecenia, aby uniknąć zakłócenia operacji biznesowych.

Po rejestracji możesz przystąpić do [używać technologii JEA](using-jea.md). Plik konfiguracji sesji można usunąć w dowolnym momencie. Plik konfiguracyjny nie jest używana po opcji rejestracji, punktu końcowego.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguracja wielu maszyn za pomocą DSC

Podczas wdrażania usługi JEA na wielu komputerach, najprostszym modelem wdrażania korzysta z technologii JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) zasób, aby szybko i spójnie wdrażać JEA na każdym komputerze.

Aby wdrożyć JEA za pomocą DSC, upewnij się, że spełniono następujące wymagania wstępne:

- Jeden lub więcej możliwości roli zostały utworzone i dodane do modułu programu PowerShell.
- Moduł programu PowerShell zawierający role są przechowywane w udziale plików (tylko do odczytu), które jest dostępne przy każdej maszyny.
- Zostały uznane za ustawienia konfiguracji sesji. Nie musisz utworzyć plik konfiguracji sesji, korzystając z zasobów DSC JEA.
- Masz poświadczenia, które umożliwią działań administracyjnych na każdym komputerze lub dostęp do serwera ściągania DSC, które są używane do zarządzania maszynami.
- Pobrano [zasobów DSC JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Utwórz konfigurację DSC dla punktu końcowego usługi JEA na serwerze docelowym, komputera lub ściągania. W tej konfiguracji **JustEnoughAdministration** zasób DSC definiuje plik konfiguracji sesji i **pliku** zasobów kopiuje możliwości roli z udziału plików.

Można skonfigurować za pomocą zasobów DSC są następujące właściwości:

- Definicje ról
- Grupy wirtualne kont
- Nazwa konta usługi zarządzanego przez grupę
- Katalog transkrypcji
- Dysku użytkownika
- Zasady dostępu warunkowego
- Skrypty uruchamiania dla sesji usługi JEA

Składnia dla każdego z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.

Poniżej znajduje się Przykładowa konfiguracja DSC dla modułu konserwacji serwera ogólnego. Przyjęto założenie, że prawidłowy modułu programu PowerShell zawierający możliwości roli znajduje się na `\\myfileshare\JEA` udziału plików.

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

Następnie konfiguracja jest stosowana w systemie przez bezpośrednie wywołanie [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) lub aktualizowania [konfiguracji serwera ściągania](/powershell/dsc/pull-server/pullServer).

Zasób DSC umożliwia również zastąpić domyślną **Microsoft.PowerShell** punktu końcowego. Po wymianie, zasobu powoduje automatyczne zarejestrowanie punktu kopii zapasowej końcowego o nazwie **Microsoft.PowerShell.Restricted**. Punkt końcowy kopii zapasowej ma wartości domyślnej listy ACL usługi WinRM, która umożliwia użytkownicy zarządzania zdalnego i Administratorzy lokalni, członkowie grupy mogli uzyskać do niego dostęp.

## <a name="unregistering-jea-configurations"></a>Wyrejestrowywanie konfiguracje usługi JEA

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenie cmdlet usuwa punktu końcowego JEA. Wyrejestrowywanie punktu końcowego usługi JEA uniemożliwia tworzenie nowych technologii JEA sesji w systemie w nowych użytkowników. W tym obszarze pozwala również zaktualizować konfigurację usługi JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wyrejestrowywanie JEA punktu końcowego powoduje ponowne uruchomienie usługi WinRM. Przerywa to działanie najbardziej zdalnego operacji zarządzania w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania. Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas planowanej konserwacji systemu windows.

## <a name="next-steps"></a>Następne kroki

[Testowanie punktu końcowego usługi JEA](using-jea.md)
