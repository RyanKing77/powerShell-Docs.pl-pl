---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie usługi JEA konfiguracji
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522858"
---
# <a name="registering-jea-configurations"></a>Rejestrowanie usługi JEA konfiguracji

> Dotyczy: Windows PowerShell 5.0

Ostatni krok, zanim użyjesz usługi JEA po utworzeniu usługi [możliwości roli](role-capabilities.md) i [plik konfiguracji sesji](session-configurations.md) tworzone jest zarejestrowanie punktu końcowego JEA.
Ten proces dotyczy informacje o konfiguracji sesji z systemu i sprawia, że punkt końcowy jest dostępny do użytku przez użytkowników i aparatów automatyzacji.

## <a name="single-machine-configuration"></a>Konfiguracja pojedynczego komputera

W przypadku małych środowisk można wdrożyć JEA, rejestrując się, używając pliku konfiguracji sesji [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.

Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:
- Co najmniej jednej roli został utworzony i umieszczane w folderze "RoleCapabilities" prawidłowy modułu programu PowerShell.
- Utworzono plik konfiguracji sesji i przetestowane.
- Użytkownik rejestrowanie usługi JEA konfiguracji ma prawa administratora na systemy.

Należy również wybranie nazwy dla punktu końcowego usługi JEA.
Nazwa punktu końcowego usługi JEA będzie wymagane, gdy użytkownicy chcą nawiązać połączenie z tego systemu przy użyciu technologii JEA.
Możesz użyć [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet, aby sprawdzić nazwy istniejące punkty końcowe w systemie.
Punkty końcowe, które zaczyna się "microsoft" zwykle są dostarczane z programem Windows.
Punkt końcowy "microsoft.powershell" jest domyślny punkt końcowy używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Po określeniu odpowiednią nazwę punktu końcowego usługi JEA, uruchom następujące polecenie, aby zarejestrować punkt końcowy.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Powyższe polecenie zostanie uruchomiony ponownie usługę WinRM w systemie.
> Spowoduje to zakończyć wszystkie sesje komunikacji zdalnej programu PowerShell, a także wszystkie trwające operacje konfiguracji DSC.
> Zalecane jest, należy wykonać żadnych produkcyjnych maszyn w tryb offline przed uruchomieniem polecenia, aby uniknąć zakłócenia operacji biznesowych.

Jeśli rejestracja powiodła się, można przystąpić do [używać technologii JEA](using-jea.md).
Plik konfiguracji sesji możesz usunąć w dowolnym momencie; nie jest używana po rejestracji.

## <a name="multi-machine-configuration-with-dsc"></a>Konfiguracja wielu maszyn za pomocą DSC

Jeśli wdrażasz JEA na wielu komputerach, najprostszym modelem wdrażania jest użycie usługi JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) zasób, aby szybko i spójnie wdrażać JEA na każdym komputerze.

Aby wdrożyć JEA za pomocą DSC, należy upewnić się, że spełniono następujące wymagania wstępne:
- Jeden lub więcej możliwości roli zostały utworzone i dodane do prawidłowy modułu programu PowerShell.
- Moduł programu PowerShell zawierający role są przechowywane w udziale plików (tylko do odczytu), które jest dostępne przy każdej maszyny.
- Zostały uznane za ustawienia konfiguracji sesji. Nie trzeba utworzyć plik konfiguracji sesji, korzystając z zasobów DSC JEA.
- Masz poświadczenia, które umożliwiają wykonywanie akcji administracyjnych na każdym komputerze lub mają dostęp do serwera ściągania DSC, używany do zarządzania maszynami.
- Pobrano [zasobów DSC usługi JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Na docelowym komputerze (lub serwerze ściągania, jeśli używana jest jedna) należy utworzyć konfigurację DSC dla punktu końcowego usługi JEA.
W tej konfiguracji użyje zasobu DSC JustEnoughAdministration do tworzenia pliku konfiguracji sesji i zasób plików do skopiowania możliwości roli z udziału plików.

Można skonfigurować za pomocą zasobów DSC są następujące właściwości:
- Definicje ról
- Grupy wirtualne konta
- Nazwa konta usługi zarządzanego przez grupę
- Katalog transkrypcji
- Dysku użytkownika
- Zasady dostępu warunkowego
- Skrypty uruchamiania dla sesji usługi JEA

Składnia dla każdego z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.

Poniżej znajduje się Przykładowa konfiguracja DSC dla modułu konserwacji serwera ogólnego.

Przyjęto założenie, że prawidłowy modułu programu PowerShell zawierający możliwości roli w podfolderze "RoleCapabilities" znajduje się na "\\\\myfileshare\\JEA" udziału plików.


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

Tę konfigurację można następnie zastosować funkcje w systemie przez [bezpośrednie wywołanie programu Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) lub aktualizowania [konfiguracji serwera ściągania](https://msdn.microsoft.com/powershell/dsc/pullserver).

Zasób DSC pozwala również zastąpić domyślny punkt końcowy komunikacji zdalnej Microsoft.PowerShell.
Jeśli to zrobisz, zasobu są automatycznie rejestrowane backup unconstrainted punktu końcowego, o nazwie "Microsoft.PowerShell.Restricted", który ma wartości domyślnej listy ACL usługi WinRM (dzięki czemu użytkownicy zarządzania zdalnego i Administratorzy lokalni członkowie grupy mogli uzyskać do niego dostęp).

## <a name="unregistering-jea-configurations"></a>Wyrejestrowywanie konfiguracje usługi JEA

Aby usunąć punkt końcowy usługi JEA w systemie, użyj [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenia cmdlet.
Wyrejestrowywanie punktu końcowego usługi JEA uniemożliwi nowym użytkownikom tworzenie nowych technologii JEA sesji w systemie.
W tym obszarze pozwala również zaktualizować konfigurację usługi JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Wyrejestrowywanie JEA punktu końcowego spowoduje ponowne uruchomienie usługi WinRM.
> Spowoduje to przerwanie operacji zarządzania najbardziej zdalnych w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania.
> Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas planowanej konserwacji systemu windows.

## <a name="next-steps"></a>Następne kroki

- [Testowanie punktu końcowego usługi JEA](using-jea.md)