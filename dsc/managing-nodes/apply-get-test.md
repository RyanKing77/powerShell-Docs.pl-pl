---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zastosuj Get i konfiguracje w węźle testów
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405245"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="286f4-103">Zastosuj Get i konfiguracje w węźle testów</span><span class="sxs-lookup"><span data-stu-id="286f4-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="286f4-104">Tym przewodniku pokazano sposób pracy z konfiguracjami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="286f4-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="286f4-105">Ten przewodnik został podzielony na następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="286f4-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="286f4-106">Zastosowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-106">Apply a Configuration</span></span>

<span data-ttu-id="286f4-107">Aby można było zastosować i zarządzanie konfiguracją, należy wygenerować plik "MOF".</span><span class="sxs-lookup"><span data-stu-id="286f4-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="286f4-108">Poniższy kod przedstawia prostej konfiguracji, który będzie używany w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="286f4-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="286f4-109">Kompilowanie ta konfiguracja umożliwia uzyskanie dwóch plików "MOF".</span><span class="sxs-lookup"><span data-stu-id="286f4-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="286f4-110">Aby zastosować konfigurację, użyj [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="286f4-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="286f4-111">`-Path` Parametr określa katalog, w którym są przechowywane pliki "MOF".</span><span class="sxs-lookup"><span data-stu-id="286f4-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="286f4-112">Jeśli nie `-Computername` jest określony, `Start-DSCConfiguration` podejmie próbę dotyczą każdej konfiguracji nazwy komputera określonego przez nazwę pliku "MOF" (\<computername\>MOF).</span><span class="sxs-lookup"><span data-stu-id="286f4-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="286f4-113">Określ `-Verbose` do `Start-DSCConfiguration` Aby wyświetlić bardziej szczegółowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="286f4-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="286f4-114">Jeśli `-Wait` nie zostanie określony, zostanie wyświetlony jeden zadanie zostało utworzone.</span><span class="sxs-lookup"><span data-stu-id="286f4-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="286f4-115">Utworzono zadanie będzie mieć jeden **ChildJob** dla każdego pliku "MOF" przetwarzane przez `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="286f4-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="286f4-116">Jeśli konfiguracja zajmuje dużo czasu, a chcesz ją zatrzymać, można użyć [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) można zatrzymać aplikacji w węźle lokalnym.</span><span class="sxs-lookup"><span data-stu-id="286f4-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="286f4-117">Po wykonaniu tych czynności, można wyświetlić stan zadania przez obiekt zadania zwracany przez [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="286f4-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="286f4-118">Aby wyświetlić **pełne** danych wyjściowych, użyj następujących poleceń, aby wyświetlić **pełne** strumienia dla każdego **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="286f4-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="286f4-119">Aby uzyskać więcej informacji o zadaniach programu PowerShell, zobacz [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="286f4-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="286f4-120">Począwszy od programu PowerShell w wersji 5.0 `-UseExisting` parametr został dodany do `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="286f4-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="286f4-121">Określając `-UseExisting`, wydać polecenie cmdlet, aby użyć istniejącej konfiguracji zastosowany zamiast zasady określone przez `-Path` parametru.</span><span class="sxs-lookup"><span data-stu-id="286f4-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="286f4-122">Testowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-122">Test a Configuration</span></span>

<span data-ttu-id="286f4-123">Możesz przetestować obecnie zastosowany przy użyciu konfiguracji [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="286f4-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="286f4-124">`Test-DSCConfiguration` zwróci `True` Jeśli węzeł jest zgodne, i `False` Jeśli tak nie jest.</span><span class="sxs-lookup"><span data-stu-id="286f4-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="286f4-125">Począwszy od programu PowerShell w wersji 5.0 `-Detailed` parametr został dodany, która zwraca obiekt z kolekcji na potrzeby **ResourcesInDesiredState** i **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="286f4-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="286f4-126">Począwszy od programu PowerShell 5.0 można sprawdzić konfiguracji bez stosowania go.</span><span class="sxs-lookup"><span data-stu-id="286f4-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="286f4-127">`-ReferenceConfiguration` Parametr przyjmuje ścieżkę do pliku "MOF", aby przetestować węzłem względem.</span><span class="sxs-lookup"><span data-stu-id="286f4-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="286f4-128">Nie **ustaw** podejmowaniem węzła.</span><span class="sxs-lookup"><span data-stu-id="286f4-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="286f4-129">W programie PowerShell 4.0 istnieją obejścia, aby przetestować konfigurację bez stosowania go, ale nie omówiono ich w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="286f4-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="286f4-130">Pobierz wartości konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-130">Get Configuration Values</span></span>

<span data-ttu-id="286f4-131">[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) polecenie cmdlet Zwraca bieżące wartości dla wszystkich skonfigurowanych zasobów w konfiguracji obecnie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="286f4-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="286f4-132">Dane wyjściowe z naszym przykładzie konfiguracji będzie wyglądała następująco, jeśli zostały zastosowane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="286f4-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="286f4-133">Pobierz stan konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-133">Get Configuration Status</span></span>

<span data-ttu-id="286f4-134">Począwszy od programu PowerShell w wersji 5.0 [Get DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) polecenie cmdlet pozwala wyświetlić historię konfiguracje stosowane do węzła.</span><span class="sxs-lookup"><span data-stu-id="286f4-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="286f4-135">PowerShell DSC śledzi informacje o ostatnie konfiguracje {{N}} stosowane w **wypychania** lub **ściągnięcia** trybu.</span><span class="sxs-lookup"><span data-stu-id="286f4-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="286f4-136">Obejmuje to dowolne *spójności* kontrole wykonywane przez LCM.</span><span class="sxs-lookup"><span data-stu-id="286f4-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="286f4-137">Domyślnie `Get-DSCConfigurationStatus` pokazuje tylko ostatni wpis historii.</span><span class="sxs-lookup"><span data-stu-id="286f4-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="286f4-138">Użyj `-All` parametru, aby zobaczyć całą historię stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="286f4-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="286f4-139">Dane wyjściowe są obcinane w celu skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="286f4-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="286f4-140">Zarządzanie dokumentami konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-140">Manage Configuration Documents</span></span>

<span data-ttu-id="286f4-141">LCM zarządza konfiguracją węzła, pracując nad **dokumentów konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="286f4-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="286f4-142">Te pliki "MOF" znajdują się w katalogu "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="286f4-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="286f4-143">Począwszy od programu PowerShell w wersji 5.0 [DSCConfigurationDocument Usuń](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) służy do usuwania plików "MOF", aby zatrzymać sprawdzania spójności w przyszłości lub usunąć konfigurację, które wystąpiły błędy podczas stosowania.</span><span class="sxs-lookup"><span data-stu-id="286f4-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="286f4-144">`-Stage` Parametr umożliwia określenie plik "MOF", który chcesz usunąć.</span><span class="sxs-lookup"><span data-stu-id="286f4-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="286f4-145">W programie PowerShell 4.0, możesz nadal usunąć te pliki "MOF" bezpośrednio przy użyciu [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="286f4-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="286f4-146">Publikowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="286f4-146">Publish Configurations</span></span>

<span data-ttu-id="286f4-147">Począwszy od programu PowerShell w wersji 5.0 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) dodano polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="286f4-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="286f4-148">To polecenie cmdlet umożliwia publikowanie pliku "MOF" z komputerami zdalnymi, bez stosowania go.</span><span class="sxs-lookup"><span data-stu-id="286f4-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="286f4-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="286f4-149">See also</span></span>

- [<span data-ttu-id="286f4-150">GET, testowania i Set</span><span class="sxs-lookup"><span data-stu-id="286f4-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
