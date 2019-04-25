---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057251"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Tworzenie punktu końcowego usługi JEA i łączenie się z nim

Aby utworzyć punkt końcowy usługi JEA, należy utworzyć i zarejestrować specjalnie skonfigurowanym konfiguracji sesji programu PowerShell pliku, który można wygenerować za pomocą **New PSSessionConfigurationFile** polecenia cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Spowoduje to utworzenie pliku konfiguracji sesji, który wygląda w następujący sposób:

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

Podczas tworzenia punktu końcowego JEA, należy ustawić następujące parametry polecenia (i odpowiadających im kluczy w pliku):

1. SessionType to RestrictedRemoteServer
2. RunAsVirtualAccount do **$true**
3. TranscriptPath do katalogu, w którym "za pośrednictwem ramię" zapisy zostaną zapisane po każdej sesji
4. RoleDefinitions do tablicy skrótów, który definiuje, które grupy mają dostęp do których "możliwości roli." To pole określa **kto** zrobić **co** dla tego punktu końcowego. Możliwości roli to specjalne pliki, które zostaną wyjaśnione wkrótce.

Pole RoleDefinitions definiuje grupy, które ma dostęp do możliwości roli. Możliwości roli jest plikiem, który definiuje zestaw funkcji, które będą dostępne do procesu łączenia użytkowników.
Można utworzyć roli możliwości **New PSRoleCapabilityFile** polecenia.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Spowoduje to wygenerowanie szablonu możliwości roli, który wygląda w następujący sposób:

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

Ma być używana przez konfigurację sesji JEA, możliwości roli muszą być zapisane jako prawidłowy modułu programu PowerShell w katalogu o nazwie "RoleCapabilities". Moduł może zawierać wiele plików możliwości roli, jeśli to konieczne.

Aby rozpocząć, konfigurowanie, które poleceń cmdlet, funkcji, aliasy i skrypty, które użytkownik może uzyskać dostęp podczas nawiązywania połączenia z sesją usługi JEA, należy dodać własne reguły do pliku możliwości roli, zgodnie z komentarzem się z szablonami. Aby dowiedzieć się więcej, w jaki skonfigurujesz możliwości roli, zapoznaj się z pełną [środowisko przewodnik](http://aka.ms/JEA).

Na koniec, po zakończeniu dostosowanie konfigurację sesji i powiązanych możliwości roli zarejestrować tej konfiguracji sesji i utworzyć punkt końcowy, uruchamiając `Register-PSSessionConfiguration`.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Łączenie do punktu końcowego usługi JEA

Nawiązywanie połączenia z punktem końcowym usługi JEA działa tak samo, nawiązywania połączenia z innych prac do punktu końcowego programu PowerShell.
Wystarczy podać nazwę punktu końcowego usługi JEA jako parametr "ConfigurationName" **New-PSSession**, **Invoke-Command**, lub **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

Po nawiązaniu połączenia z sesją usługi JEA, będzie ograniczona do uruchamiania poleceń na liście dozwolonych w możliwości roli, który ma dostęp do. Jeśli spróbujesz uruchomić dowolne polecenie nie jest dozwolona dla roli użytkownika, wystąpi błąd.