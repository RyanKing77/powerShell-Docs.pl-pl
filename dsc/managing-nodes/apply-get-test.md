---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Stosowanie, pobieranie i testowanie konfiguracji w węźle
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684339"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Stosowanie, pobieranie i testowanie konfiguracji w węźle

Tym przewodniku pokazano sposób pracy z konfiguracjami w docelowym węźle. Ten przewodnik został podzielony na następujące czynności:

## <a name="apply-a-configuration"></a>Zastosowanie konfiguracji

Aby można było zastosować i zarządzanie konfiguracją, należy wygenerować plik "MOF". Poniższy kod przedstawia prostej konfiguracji, który będzie używany w tym przewodniku.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

Kompilowanie ta konfiguracja umożliwia uzyskanie dwóch plików "MOF".

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Aby zastosować konfigurację, użyj [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet. `-Path` Parametr określa katalog, w którym są przechowywane pliki "MOF". Jeśli nie `-Computername` jest określony, `Start-DSCConfiguration` podejmie próbę dotyczą każdej konfiguracji nazwy komputera określonego przez nazwę pliku "MOF" (\<computername\>MOF). Określ `-Verbose` do `Start-DSCConfiguration` Aby wyświetlić bardziej szczegółowe dane wyjściowe.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Jeśli `-Wait` nie zostanie określony, zostanie wyświetlony jeden zadanie zostało utworzone. Utworzono zadanie będzie mieć jeden **ChildJob** dla każdego pliku "MOF" przetwarzane przez `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Jeśli konfiguracja zajmuje dużo czasu, a chcesz ją zatrzymać, można użyć [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) można zatrzymać aplikacji w węźle lokalnym.

```powershell
Stop-DSCConfiguration -Force
```

Po wykonaniu tych czynności, można wyświetlić stan zadania przez obiekt zadania zwracany przez [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Aby wyświetlić **pełne** danych wyjściowych, użyj następujących poleceń, aby wyświetlić **pełne** strumienia dla każdego **ChildJob**. Aby uzyskać więcej informacji o zadaniach programu PowerShell, zobacz [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

Począwszy od programu PowerShell w wersji 5.0 `-UseExisting` parametr został dodany do `Start-DSCConfiguration`. Określając `-UseExisting`, wydać polecenie cmdlet, aby użyć istniejącej konfiguracji zastosowany zamiast zasady określone przez `-Path` parametru.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Testowanie konfiguracji

Możesz przetestować obecnie zastosowany przy użyciu konfiguracji [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` zwróci `True` Jeśli węzeł jest zgodne, i `False` Jeśli tak nie jest.

```powershell
Test-DSCConfiguration
```

Począwszy od programu PowerShell w wersji 5.0 `-Detailed` parametr został dodany, która zwraca obiekt z kolekcji na potrzeby **ResourcesInDesiredState** i **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Począwszy od programu PowerShell 5.0 można sprawdzić konfiguracji bez stosowania go. `-ReferenceConfiguration` Parametr przyjmuje ścieżkę do pliku "MOF", aby przetestować węzłem względem. Nie **ustaw** podejmowaniem węzła. W programie PowerShell 4.0 istnieją obejścia, aby przetestować konfigurację bez stosowania go, ale nie omówiono ich w tym miejscu.

## <a name="get-configuration-values"></a>Pobierz wartości konfiguracji

[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) polecenie cmdlet Zwraca bieżące wartości dla wszystkich skonfigurowanych zasobów w konfiguracji obecnie zastosowany.

```powershell
Get-DSCConfiguration
```

Dane wyjściowe z naszym przykładzie konfiguracji będzie wyglądała następująco, jeśli zostały zastosowane pomyślnie.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Pobierz stan konfiguracji

Począwszy od programu PowerShell w wersji 5.0 [Get DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) polecenie cmdlet pozwala wyświetlić historię konfiguracje stosowane do węzła. PowerShell DSC śledzi informacje o ostatnie konfiguracje {{N}} stosowane w **wypychania** lub **ściągnięcia** trybu. Obejmuje to dowolne *spójności* kontrole wykonywane przez LCM. Domyślnie `Get-DSCConfigurationStatus` pokazuje tylko ostatni wpis historii.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Użyj `-All` parametru, aby zobaczyć całą historię stanu konfiguracji.

> [!NOTE]
> Dane wyjściowe są obcinane w celu skrócenia programu.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Zarządzanie dokumentami konfiguracji

LCM zarządza konfiguracją węzła, pracując nad **dokumentów konfiguracji**. Te pliki "MOF" znajdują się w katalogu "C:\Windows\System32\Configuration".

Począwszy od programu PowerShell w wersji 5.0 [DSCConfigurationDocument Usuń](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) służy do usuwania plików "MOF", aby zatrzymać sprawdzania spójności w przyszłości lub usunąć konfigurację, które wystąpiły błędy podczas stosowania. `-Stage` Parametr umożliwia określenie plik "MOF", który chcesz usunąć.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> W programie PowerShell 4.0, możesz nadal usunąć te pliki "MOF" bezpośrednio przy użyciu [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Publikowanie konfiguracji

Począwszy od programu PowerShell w wersji 5.0 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) dodano polecenia cmdlet. To polecenie cmdlet umożliwia publikowanie pliku "MOF" z komputerami zdalnymi, bez stosowania go.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Zobacz też

- [GET, testowania i Set](../resources/get-test-set.md)
