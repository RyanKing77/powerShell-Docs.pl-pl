---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie JEA konfiguracji
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188517"
---
# <a name="registering-jea-configurations"></a>Rejestrowanie JEA konfiguracji

> Dotyczy: środowiska Windows PowerShell 5.0

Ostatnim krokiem przed użyciem JEA po utworzeniu sieci [możliwości roli](role-capabilities.md) i [pliku konfiguracji sesji](session-configurations.md) utworzony się zarejestrować punkt końcowy JEA.
Ten proces dotyczy informacje o konfiguracji sesji systemu i udostępnia punkt końcowy do użycia przez użytkowników i aparatów automatyzacji.

## <a name="single-machine-configuration"></a>Konfiguracja pojedynczego komputera

W przypadku małych środowisk można wdrożyć JEA przez zarejestrowanie sesji konfiguracji plików przy użyciu [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.

Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:
- Co najmniej jedną rolę został utworzony i umieszczane w folderze "RoleCapabilities" nieprawidłowy modułu programu PowerShell.
- Utworzono plik konfiguracji sesji i przetestowane.
- Użytkownik rejestrujący konfiguracji JEA ma prawa administratora na systemy.

Należy również wybrać nazwę punktu końcowego JEA.
Nazwa punktu końcowego JEA będzie wymagane, kiedy użytkownik chce nawiązać połączenie przy użyciu JEA systemu.
Można użyć [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet, aby sprawdzić nazwy istniejące punkty końcowe w systemie.
Punkty końcowe rozpoczynających się od 'microsoft' zwykle są dostarczane z systemem Windows.
Punkt końcowy "microsoft.powershell" jest używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell domyślny punkt końcowy.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Po określeniu odpowiednią nazwę punktu końcowego JEA, uruchom następujące polecenie, aby zarejestrować punkt końcowy.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Powyższe polecenie uruchomi usługę WinRM na komputerze.
> Spowoduje to przerwanie wszystkich sesji komunikacji zdalnej programu PowerShell, a także wszystkie trwające operacje konfiguracji DSC.
> Zaleca się wyłączeniem wszelkich maszyn produkcyjnym przed uruchomieniem polecenia, aby uniknąć zakłóceń w działalności firmy.

Jeśli rejestracja powiodła się, można przystąpić do [Użyj JEA](using-jea.md).
Plik konfiguracji sesji można usunąć w dowolnym momencie; nie jest on używany po rejestracji.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguracja obsługi wielu komputerów z usługi Konfiguracja DSC

Jeśli wdrażasz JEA na wielu komputerach, najprostszym modelem wdrożenia jest użycie JEA [konfiguracji żądanego stanu](https://msdn.microsoft.com/en-us/powershell/dsc/overview) zasób, aby szybko i spójne wdrażanie JEA na każdym komputerze.

Aby wdrożyć JEA usłudze Konfiguracja DSC, należy upewnić się, że są spełnione następujące wymagania wstępne:
- Jeden lub więcej możliwości roli zostały utworzone i dodane do prawidłowy modułu programu PowerShell.
- Moduł PowerShell zawierającego role są przechowywane w udziale plików (tylko do odczytu) dostępny przy każdej maszyny.
- Określono ustawienia konfiguracji sesji. Nie trzeba utworzyć plik konfiguracji sesji, korzystając z zasobów JEA DSC.
- Masz poświadczenia, które umożliwiają wykonywanie zadań administracyjnych na każdym komputerze, lub korzystać z serwera ściągania usługi Konfiguracja DSC używane do zarządzania na komputerach.
- Pobrano [JEA DSC zasobów](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Na docelowej maszynie (lub serwera ściągania, jeśli używasz) utworzenie konfiguracji DSC dla punktu końcowego JEA.
W tej konfiguracji użyje zasobu JustEnoughAdministration DSC pliku konfiguracji sesji i zasobu pliku kopiować możliwości roli z udziału plików.

Można konfigurować przy użyciu zasobów DSC są następujące właściwości:
- Definicje ról
- Wirtualny grup kont
- Nazwa konta usługi zarządzanego przez grupę
- Wykaz katalogu
- Stacji użytkownika
- Zasady dostępu warunkowego
- Skrypty uruchamiania dla sesji JEA

Składnia dla każdej z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.

Poniżej znajduje się Przykładowa konfiguracja DSC modułu obsługi ogólnych.

Przyjęto założenie, że prawidłowy moduł PowerShell zawierający możliwości roli w podfolderze "RoleCapabilities" znajduje się na "\\\\myfileshare\\JEA" udziału plików.


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

Tę konfigurację można zastosować w systemie przez [bezpośrednie wywoływanie lokalny program Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) lub aktualizowania [konfiguracji serwera ściągania](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

Zasobów DSC pozwala również zastąpić domyślny punkt końcowy komunikacji zdalnej Microsoft.PowerShell.
Jeśli to zrobisz, zasobu zostanie automatycznie zarejestrować punkt końcowy unconstrainted kopii zapasowej o nazwie "Microsoft.PowerShell.Restricted", którego domyślne WinRM listy kontroli dostępu (dzięki czemu użytkownicy zarządzania zdalnego i Administratorzy lokalni członków grupy dostępu do niego).

## <a name="unregistering-jea-configurations"></a>Wyrejestrowywanie konfiguracje JEA

Aby usunąć punkt końcowy JEA w systemie, użyj [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenia cmdlet.
Wyrejestrowywanie punktu końcowego JEA uniemożliwi nowych użytkowników do tworzenia nowych JEA sesji w systemie.
Umożliwia on również zaktualizować konfiguracji JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wyrejestrowywanie JEA punktu końcowego spowoduje ponowne uruchomienie usługi WinRM.
> Spowoduje to zakłóceń najbardziej zdalnego zarządzania operacji w toku, łącznie z innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania.
> Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas zaplanowanej konserwacji systemu windows.

## <a name="next-steps"></a>Następne kroki

- [Testowanie JEA punktu końcowego](using-jea.md)