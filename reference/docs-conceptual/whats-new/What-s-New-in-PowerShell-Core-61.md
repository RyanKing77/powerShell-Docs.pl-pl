---
title: Co nowego w programie PowerShell Core 6.1
description: Nowe funkcje i zmiany w programie PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: b95b9dd504ea2a165a4689a3b28d2298644e5e68
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611526"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="45386-103">Co nowego w programie PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="45386-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="45386-104">Poniżej przedstawiono niektóre główne nowe funkcje i zmiany, które zostały wprowadzone w programie PowerShell Core 6.1 wyboru.</span><span class="sxs-lookup"><span data-stu-id="45386-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="45386-105">Istnieje również **tonach** "nudnych dostępu", które ułatwiają programu PowerShell, szybsze i bardziej stabilne (plus partii i wiele poprawek)!</span><span class="sxs-lookup"><span data-stu-id="45386-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="45386-106">Aby uzyskać pełną listę zmian, zapoznaj się z naszym [dziennika zmian w witrynie GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="45386-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="45386-107">I gdy czy powinniśmy zwołać kilka nazw poniżej, aby [wszystkie uczestnicy społeczności](https://github.com/PowerShell/PowerShell/graphs/contributors) , wprowadzonych w tej wersji możliwe.</span><span class="sxs-lookup"><span data-stu-id="45386-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="45386-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="45386-108">.NET Core 2.1</span></span>

<span data-ttu-id="45386-109">PowerShell Core 6.1 przeniesione do platformy .NET Core 2.1, po [wydane w maju](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), dając w efekcie w szereg ulepszeń w programie PowerShell, w tym:</span><span class="sxs-lookup"><span data-stu-id="45386-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="45386-110">ulepszenia wydajności (zobacz [poniżej](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="45386-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="45386-111">Firma Alpine pomoc techniczna Linux support (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="45386-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="45386-112">[Obsługa narzędzia globalnej platformy .NET](/dotnet/core/tools/global-tools) — najbliższych wkrótce do programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="45386-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="45386-113">Windows Compatibility Pack dla programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="45386-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="45386-114">W Windows, dostarczane przez zespół .NET [systemie Windows Compatibility Pack dla platformy .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), zbiór zestawów, które dodać szereg usunięte interfejsów API do platformy .NET Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="45386-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="45386-115">Dodaliśmy pakiet Windows do wersji programu PowerShell Core 6.1, aby wszystkie moduły lub skrypty, które używają tych interfejsów API można polegać na nich dostępne.</span><span class="sxs-lookup"><span data-stu-id="45386-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="45386-116">Pakiet Windows umożliwia programu PowerShell Core do użycia **więcej niż 1900 poleceń cmdlet, które są dostarczane z systemem Windows 10 października 2018 Update i Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="45386-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="45386-117">Obsługa listy dozwolonych aplikacji</span><span class="sxs-lookup"><span data-stu-id="45386-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="45386-118">PowerShell Core 6.1 ma parzystości przy użyciu programu Windows PowerShell 5.1 obsługi [funkcji AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) i [funkcji Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) listy dozwolonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45386-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="45386-119">Listy dozwolonych aplikacji umożliwia szczegółową kontrolę, z których plików binarnych mogą być wykonywane używany przy użyciu programu PowerShell [Tryb ograniczonego języka](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="45386-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="45386-120">Ulepszenia wydajności</span><span class="sxs-lookup"><span data-stu-id="45386-120">Performance improvements</span></span>

<span data-ttu-id="45386-121">PowerShell Core 6.0 wprowadzone pewne znaczne ulepszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="45386-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="45386-122">PowerShell Core 6.1 w dalszym ciągu przyspieszyć niektóre operacje.</span><span class="sxs-lookup"><span data-stu-id="45386-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="45386-123">Na przykład `Group-Object` przyspieszyło o 66%:</span><span class="sxs-lookup"><span data-stu-id="45386-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="45386-124">Program Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="45386-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="45386-125">Program PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="45386-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="45386-126">Program PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="45386-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="45386-127">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="45386-127">Time (sec)</span></span>   | <span data-ttu-id="45386-128">25.178</span><span class="sxs-lookup"><span data-stu-id="45386-128">25.178</span></span>                 | <span data-ttu-id="45386-129">19.653</span><span class="sxs-lookup"><span data-stu-id="45386-129">19.653</span></span>              | <span data-ttu-id="45386-130">6.641</span><span class="sxs-lookup"><span data-stu-id="45386-130">6.641</span></span>               |
| <span data-ttu-id="45386-131">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="45386-131">Speed-up (%)</span></span> | <span data-ttu-id="45386-132">Brak</span><span class="sxs-lookup"><span data-stu-id="45386-132">N/A</span></span>                    | <span data-ttu-id="45386-133">21.9%</span><span class="sxs-lookup"><span data-stu-id="45386-133">21.9%</span></span>               | <span data-ttu-id="45386-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="45386-134">66.2%</span></span>               |

<span data-ttu-id="45386-135">Podobnie przez więcej niż 15% ulepszyła scenariusze sortowania podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="45386-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="45386-136">Program Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="45386-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="45386-137">Program PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="45386-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="45386-138">Program PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="45386-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="45386-139">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="45386-139">Time (sec)</span></span>   | <span data-ttu-id="45386-140">12.170</span><span class="sxs-lookup"><span data-stu-id="45386-140">12.170</span></span>                 | <span data-ttu-id="45386-141">8.493</span><span class="sxs-lookup"><span data-stu-id="45386-141">8.493</span></span>               | <span data-ttu-id="45386-142">7.08</span><span class="sxs-lookup"><span data-stu-id="45386-142">7.08</span></span>                |
| <span data-ttu-id="45386-143">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="45386-143">Speed-up (%)</span></span> | <span data-ttu-id="45386-144">Brak</span><span class="sxs-lookup"><span data-stu-id="45386-144">N/A</span></span>                    | <span data-ttu-id="45386-145">30.2%</span><span class="sxs-lookup"><span data-stu-id="45386-145">30.2%</span></span>               | <span data-ttu-id="45386-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="45386-146">16.6%</span></span>               |

<span data-ttu-id="45386-147">`Import-Csv` ma również zostały przyspieszyło znacznie po regresji za pomocą programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45386-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="45386-148">W poniższym przykładzie użyto testu CSV z 26,616 wierszami i kolumnami sześć:</span><span class="sxs-lookup"><span data-stu-id="45386-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="45386-149">Program Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="45386-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="45386-150">Program PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="45386-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="45386-151">Program PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="45386-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="45386-152">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="45386-152">Time (sec)</span></span>   | <span data-ttu-id="45386-153">0.441</span><span class="sxs-lookup"><span data-stu-id="45386-153">0.441</span></span>                  | <span data-ttu-id="45386-154">1.069</span><span class="sxs-lookup"><span data-stu-id="45386-154">1.069</span></span>               | <span data-ttu-id="45386-155">0.268</span><span class="sxs-lookup"><span data-stu-id="45386-155">0.268</span></span>                  |
| <span data-ttu-id="45386-156">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="45386-156">Speed-up (%)</span></span> | <span data-ttu-id="45386-157">Brak</span><span class="sxs-lookup"><span data-stu-id="45386-157">N/A</span></span>                    | <span data-ttu-id="45386-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="45386-158">-142.4%</span></span>             | <span data-ttu-id="45386-159">74.9% (% 39.2 z WPS)</span><span class="sxs-lookup"><span data-stu-id="45386-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="45386-160">Na koniec konwersji z formatu JSON do `PSObject` ma zostały przyspieszyło przez więcej niż 50% od środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45386-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="45386-161">W poniższym przykładzie użyto pliku JSON testu ~ 2MB:</span><span class="sxs-lookup"><span data-stu-id="45386-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="45386-162">Program Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="45386-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="45386-163">Program PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="45386-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="45386-164">Program PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="45386-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="45386-165">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="45386-165">Time (sec)</span></span>   | <span data-ttu-id="45386-166">0.259</span><span class="sxs-lookup"><span data-stu-id="45386-166">0.259</span></span>                  | <span data-ttu-id="45386-167">0.577</span><span class="sxs-lookup"><span data-stu-id="45386-167">0.577</span></span>               | <span data-ttu-id="45386-168">0,125</span><span class="sxs-lookup"><span data-stu-id="45386-168">0.125</span></span>                  |
| <span data-ttu-id="45386-169">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="45386-169">Speed-up (%)</span></span> | <span data-ttu-id="45386-170">Brak</span><span class="sxs-lookup"><span data-stu-id="45386-170">N/A</span></span>                    | <span data-ttu-id="45386-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="45386-171">-122.8%</span></span>             | <span data-ttu-id="45386-172">78.3% (% 51.7 z WPS)</span><span class="sxs-lookup"><span data-stu-id="45386-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a><span data-ttu-id="45386-173">Sprawdź `system32` dla modułów zgodne skrzynki odbiorczej w Windows</span><span class="sxs-lookup"><span data-stu-id="45386-173">Check `system32` for compatible inbox modules on Windows</span></span>

<span data-ttu-id="45386-174">W Windows Server 2019 i aktualizacji systemu Windows 10 1809 Zaktualizowaliśmy liczbę modułów programu PowerShell skrzynki odbiorczej, aby oznaczyć je jako niezgodne z programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="45386-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of inbox PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="45386-175">Podczas uruchamiania programu PowerShell Core 6.1, automatycznie zostanie dołączony `$windir\System32` jako część `PSModulePath` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="45386-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="45386-176">Jednak tylko udostępnia ona moduły `Get-Module` i `Import-Module` jeśli jego `CompatiblePSEdition` jest oznaczona jako zgodna z `Core`.</span><span class="sxs-lookup"><span data-stu-id="45386-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="45386-177">Może zostać wyświetlony różnych dostępnych modułów, w zależności od tego, jakie role i funkcje są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="45386-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="45386-178">Można zastąpić to zachowanie, aby pokazać wszystkie moduły przy użyciu `-SkipEditionCheck` parametr przełącznika.</span><span class="sxs-lookup"><span data-stu-id="45386-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="45386-179">Dodaliśmy także `PSEdition` właściwości do danych wyjściowych tabeli.</span><span class="sxs-lookup"><span data-stu-id="45386-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="45386-180">Aby uzyskać więcej informacji na temat tego zachowania, zapoznaj się z [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="45386-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="45386-181">Polecenia cmdlet języka znaczników markdown i renderowanie</span><span class="sxs-lookup"><span data-stu-id="45386-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="45386-182">Markdown to standardowe rozwiązanie dla tworzenia dokumentów zwykłego podstawowe formatowanie może być renderowany w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="45386-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="45386-183">Dodaliśmy niektórych poleceń cmdlet w 6.1, pozwalających konwersji i renderowania dokumentów języka znaczników Markdown w konsoli, w tym:</span><span class="sxs-lookup"><span data-stu-id="45386-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="45386-184">Na przykład `Show-Markdown` renderuje plik języka znaczników Markdown, w konsoli:</span><span class="sxs-lookup"><span data-stu-id="45386-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Przykład kodu Markdown show](./images/markdown_example.png)

<span data-ttu-id="45386-186">Aby uzyskać więcej informacji na temat działania tych poleceń cmdlet zapoznaj się z [tej specyfikacji RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="45386-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="45386-187">Flagi funkcji eksperymentalnych</span><span class="sxs-lookup"><span data-stu-id="45386-187">Experimental feature flags</span></span>

<span data-ttu-id="45386-188">Flagi funkcji eksperymentalnych pozwalają użytkownikom na włączanie funkcji, które jeszcze nie został sfinalizowany.</span><span class="sxs-lookup"><span data-stu-id="45386-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="45386-189">Funkcje eksperymentalne nie są obsługiwane i mogą mieć usterek.</span><span class="sxs-lookup"><span data-stu-id="45386-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="45386-190">Dowiedz się więcej na temat tej funkcji w [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="45386-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="45386-191">Ulepszenia dotyczące polecenia cmdlet w sieci Web</span><span class="sxs-lookup"><span data-stu-id="45386-191">Web cmdlet improvements</span></span>

<span data-ttu-id="45386-192">Dzięki @markekraus, całe slew ulepszeń zostały wprowadzone do naszych poleceń cmdlet w sieci web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="45386-192">Thanks to @markekraus, a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="45386-193">i [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="45386-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="45386-194">[6109 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6109) — domyślny zestaw kodowania na UTF-8 dla `application-json` odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="45386-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="45386-195">[Żądania Ściągnięcia #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parametru, aby umożliwić `Content-Type` nagłówki, które nie są zgodne z normami</span><span class="sxs-lookup"><span data-stu-id="45386-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="45386-196">[Żądania Ściągnięcia #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` uproszczony parametr w celu obsługi `multipart/form-data` pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="45386-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="45386-197">[Żądania Ściągnięcia #6338](https://github.com/PowerShell/PowerShell/pull/6338) — zgodne, bez uwzględniania wielkości liter Obsługa kluczy relacji</span><span class="sxs-lookup"><span data-stu-id="45386-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="45386-198">[Żądania Ściągnięcia #6447](https://github.com/PowerShell/PowerShell/pull/6447) — Dodaj `-Resume` parametr dla polecenia cmdlet sieci web</span><span class="sxs-lookup"><span data-stu-id="45386-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="45386-199">Ulepszenia usług zdalnych</span><span class="sxs-lookup"><span data-stu-id="45386-199">Remoting improvements</span></span>

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a><span data-ttu-id="45386-200">Bezpośrednie PowerShell spróbuje najpierw użyć programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="45386-200">PowerShell Direct tries to use PowerShell Core first</span></span>

<span data-ttu-id="45386-201">[Bezpośrednie PowerShell](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) jest funkcją programu PowerShell i funkcji Hyper-V, która umożliwia łączenie z maszyną Wirtualną funkcji Hyper-V, bez łączności sieciowej lub innych usług zarządzania zdalnego.</span><span class="sxs-lookup"><span data-stu-id="45386-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM without network connectivity or other remote management services.</span></span>

<span data-ttu-id="45386-202">W przeszłości połączone bezpośrednio z programu PowerShell jest używane wystąpienie skrzynki odbiorczej programu Windows PowerShell na maszynie Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="45386-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the VM.</span></span>
<span data-ttu-id="45386-203">Teraz, programu PowerShell Direct najpierw próbuje nawiązać połączenie przy użyciu wszystkie dostępne `pwsh.exe` na `PATH` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="45386-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="45386-204">Jeśli `pwsh.exe` nie jest dostępna, programu PowerShell Direct powraca do użycia `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="45386-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="45386-205">`Enable-PSRemoting` utworzy teraz punkty końcowe komunikacji zdalnej w oddzielnych wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="45386-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="45386-206">`Enable-PSRemoting` teraz tworzy dwie konfiguracje sesji komunikacji zdalnej:</span><span class="sxs-lookup"><span data-stu-id="45386-206">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="45386-207">Jeden dla wersji głównej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45386-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="45386-208">Na przykład`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="45386-208">For example,`PowerShell.6`.</span></span> <span data-ttu-id="45386-209">Ten punkt końcowy, które mogą być powoływane między aktualizacjami wersji pomocniczej konfiguracji sesji programu PowerShell 6 "systemowe"</span><span class="sxs-lookup"><span data-stu-id="45386-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="45386-210">Jedna konfiguracja sesji specyficzny dla wersji, na przykład: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="45386-210">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="45386-211">To zachowanie jest przydatne, jeśli chcesz mieć wiele wersji programu PowerShell 6 zainstalowana i jest dostępna na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="45386-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="45386-212">Ponadto wersji zapoznawczych programu PowerShell teraz uzyskać własnych usług zdalnych konfiguracjami sesji po uruchomieniu `Enable-PSRemoting` polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="45386-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="45386-213">Dane wyjściowe mogą się różnić, jeśli nie skonfigurowano usługi WinRM przed.</span><span class="sxs-lookup"><span data-stu-id="45386-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="45386-214">Następnie możesz zobaczyć oddzielne konfiguracje sesji programu PowerShell w wersji zapoznawczej i stabilny kompilacje z programu PowerShell 6 i dla każdej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="45386-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="45386-215">`user@host:port` Składnia obsługiwanych przez protokół SSH</span><span class="sxs-lookup"><span data-stu-id="45386-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="45386-216">SSH klientów zwykle obsługują parametry połączenia w formacie `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="45386-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="45386-217">Z dodatkiem SSH jako protokół dla niego komunikacji zdalnej programu PowerShell Dodaliśmy obsługę tego formatu ciągu połączenia:</span><span class="sxs-lookup"><span data-stu-id="45386-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="45386-218">Opcja MSI można dodać menu kontekstowego powłoki Eksploratora Windows</span><span class="sxs-lookup"><span data-stu-id="45386-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="45386-219">Dzięki @bergmeister, teraz można włączyć menu kontekstowego na Windows.</span><span class="sxs-lookup"><span data-stu-id="45386-219">Thanks to @bergmeister, now you can enable a context menu on Windows.</span></span> <span data-ttu-id="45386-220">Teraz można otworzyć instalacja systemowe 6.1 programu PowerShell z dowolnego folderu w Eksploratorze Windows:</span><span class="sxs-lookup"><span data-stu-id="45386-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu kontekstowe powłoki PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="45386-222">Dodatki</span><span class="sxs-lookup"><span data-stu-id="45386-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="45386-223">"Uruchom jako Administrator", w skrócie Windows przejdź do listy</span><span class="sxs-lookup"><span data-stu-id="45386-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="45386-224">Dzięki @bergmeister, listy szybkiego dostępu skrótu programu PowerShell Core zawiera teraz "Uruchom jako Administrator":</span><span class="sxs-lookup"><span data-stu-id="45386-224">Thanks to @bergmeister, the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Uruchom jako administrator program PowerShell 6 listy szybkiego dostępu](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="45386-226">`cd -` Powrót do poprzedniego katalogu</span><span class="sxs-lookup"><span data-stu-id="45386-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="45386-227">Lub w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="45386-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="45386-228">Ponadto `cd --` zmieni się na `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="45386-228">Also, `cd --` changes to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="45386-229">Dzięki @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) ma wydajnej polecenia cmdlet programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="45386-229">Thanks to @iSazonov, the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="45386-230">`Update-Help` jako bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="45386-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="45386-231">Popularne popytem `Update-Help` nie musi już być uruchomiony z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="45386-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="45386-232">`Update-Help` teraz domyślnie zapisywania pomocy do folderu o określonym zakresie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="45386-232">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="45386-233">Nowe metody/właściwości na `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="45386-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="45386-234">Dzięki @iSazonov, dodaliśmy nowe metody i właściwości w celu `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="45386-234">Thanks to @iSazonov, we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="45386-235">`PSCustomObject` zawiera teraz `Count` / `Length` właściwość, która podaje liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="45386-235">`PSCustomObject` now includes a `Count`/`Length` property that gives the number of items.</span></span>

<span data-ttu-id="45386-236">Oba te przykłady zwracają `2` jako liczba `PSCustomObjects` w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="45386-236">Both of these examples return `2` as the number of `PSCustomObjects` in the collection.</span></span>

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

<span data-ttu-id="45386-237">Praca ta obejmuje również `ForEach` i `Where` metody, które umożliwiają działanie i przefiltruj `PSCustomObject` elementy:</span><span class="sxs-lookup"><span data-stu-id="45386-237">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

<span data-ttu-id="45386-238">Dzięki @SimonWahlin, dodaliśmy `-Not` parametr `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="45386-238">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="45386-239">Teraz można filtrować obiekt w potoku, który nie istnieje właściwość lub wartość właściwości o wartości null lub być pusty.</span><span class="sxs-lookup"><span data-stu-id="45386-239">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="45386-240">Na przykład to polecenie zwraca wszystkie usługi, które nie mają zdefiniowanych żadnych usług zależnych:</span><span class="sxs-lookup"><span data-stu-id="45386-240">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="45386-241">`New-ModuleManifest` Tworzy dokument bez BOM UTF-8</span><span class="sxs-lookup"><span data-stu-id="45386-241">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="45386-242">Zaktualizowaliśmy udzielone naszego przejścia bez BOM UTF-8 w programie PowerShell w wersji 6.0, `New-ModuleManifest` polecenia cmdlet, aby utworzyć dokument bez BOM UTF-8 zamiast UTF-16, jeden.</span><span class="sxs-lookup"><span data-stu-id="45386-242">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="45386-243">Konwersje z PSMethod delegata</span><span class="sxs-lookup"><span data-stu-id="45386-243">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="45386-244">Dzięki @powercode, zapewniamy obecnie obsługę konwersji `PSMethod` do delegata.</span><span class="sxs-lookup"><span data-stu-id="45386-244">Thanks to @powercode, we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="45386-245">Dzięki temu można wykonywać następujące czynności przekazywanie `PSMethod` `[M]::DoubleStrLen` jako wartość delegata do `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="45386-245">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="45386-246">Aby uzyskać więcej informacji na temat tej zmiany, zapoznaj się z [5287 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="45386-246">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="45386-247">Odchylenie standardowe `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="45386-247">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="45386-248">Dzięki @CloudyDino, dodaliśmy `StandardDeviation` właściwości `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="45386-248">Thanks to @CloudyDino, we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="45386-249">Dzięki @maybe-hello-world, `Get-PfxCertificate` ma teraz `Password` parametr, który przyjmuje `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="45386-249">Thanks to @maybe-hello-world, `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="45386-250">Dzięki temu można używać go w trybie nieinteraktywnym:</span><span class="sxs-lookup"><span data-stu-id="45386-250">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="45386-251">Usuwanie `more` — funkcja</span><span class="sxs-lookup"><span data-stu-id="45386-251">Removal of the `more` function</span></span>

<span data-ttu-id="45386-252">W przeszłości, programu PowerShell dostarczanych funkcja na Windows o nazwie `more` który opakowany `more.com`.</span><span class="sxs-lookup"><span data-stu-id="45386-252">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="45386-253">Ta funkcja została usunięta.</span><span class="sxs-lookup"><span data-stu-id="45386-253">That function has now been removed.</span></span>

<span data-ttu-id="45386-254">Również `help` zmienione, aby używać funkcji `more.com` Windows lub systemu domyślne pagera, określony przez `$env:PAGER` na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="45386-254">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="45386-255">`cd DriveName:` teraz zwraca użytkowników do bieżącego katalogu roboczego na tym dysku</span><span class="sxs-lookup"><span data-stu-id="45386-255">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="45386-256">Wcześniej przy użyciu `Set-Location` lub `cd` aby powrócić do PSDrive, wysyłane użytkowników do domyślnej lokalizacji dla tego dysku.</span><span class="sxs-lookup"><span data-stu-id="45386-256">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="45386-257">Dzięki @mcbobke, użytkownicy są teraz wysyłane do ostatniej znanej bieżący katalog roboczy dla tej sesji.</span><span class="sxs-lookup"><span data-stu-id="45386-257">Thanks to @mcbobke, users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="45386-258">Akceleratory typu środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="45386-258">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="45386-259">W programie Windows PowerShell dodaliśmy następujące akceleratorów typu w celu ułatwienia pracy z ich odpowiednich typów:</span><span class="sxs-lookup"><span data-stu-id="45386-259">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="45386-260">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="45386-260">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="45386-261">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="45386-261">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="45386-262">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="45386-262">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="45386-263">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="45386-263">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="45386-264">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="45386-264">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="45386-265">Te skróty klawiaturowe typu nie zostały uwzględnione w programie PowerShell 6, ale zostały dodane do 6.1 programu PowerShell w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="45386-265">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="45386-266">Te typy są przydatne w prosty sposób tworzenia usługi AD i obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="45386-266">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="45386-267">Można na przykład zapytania przy użyciu protokołu LDAP:</span><span class="sxs-lookup"><span data-stu-id="45386-267">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="45386-268">Obu tych przykładach Utwórz obiekt Win32_OperatingSystem CIM:</span><span class="sxs-lookup"><span data-stu-id="45386-268">Both of these examples create a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="45386-269">`-lp` alias dla wszystkich `-LiteralPath` parametrów</span><span class="sxs-lookup"><span data-stu-id="45386-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="45386-270">Dzięki @kvprasoon, mamy teraz aliasu parametru `-lp` dla wszystkich wbudowanych poleceń cmdlet programu PowerShell, które mają `-LiteralPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="45386-270">Thanks to @kvprasoon, we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="45386-271">Fundamentalne zmiany</span><span class="sxs-lookup"><span data-stu-id="45386-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="45386-272">Instalacja wykonywana przy użyciu pliku MSI ścieżek na Windows</span><span class="sxs-lookup"><span data-stu-id="45386-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="45386-273">Na Windows pakiet MSI instaluje teraz w następującej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="45386-273">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="45386-274">`$env:ProgramFiles\PowerShell\6\` stabilna instalacji w wersji 6.x</span><span class="sxs-lookup"><span data-stu-id="45386-274">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="45386-275">`$env:ProgramFiles\PowerShell\6-preview\` dla instalacji w wersji 6.x (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="45386-275">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="45386-276">Ta zmiana zapewnia program PowerShell Core można zaktualizować/obsługiwanych przez usługi Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="45386-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="45386-277">Aby uzyskać więcej informacji, zapoznaj się z [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="45386-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="45386-278">Telemetrię można wyłączyć tylko za pomocą zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="45386-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="45386-279">Program PowerShell Core wysyła dane telemetryczne podstawowe do firmy Microsoft, po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="45386-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="45386-280">Dane obejmują nazwę systemu operacyjnego, wersji systemu operacyjnego i wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45386-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="45386-281">Te dane, pozwala lepiej zrozumieć środowisk, w których program PowerShell jest używany i pozwala nam określić priorytety nowe funkcje i poprawki.</span><span class="sxs-lookup"><span data-stu-id="45386-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="45386-282">Aby zrezygnować z tych danych telemetrycznych, ustaw zmienną środowiskową `POWERSHELL_TELEMETRY_OPTOUT` do `true`, `yes`, lub `1`.</span><span class="sxs-lookup"><span data-stu-id="45386-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="45386-283">Nie obsługujemy już usunięcia pliku `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` można wyłączyć na telemetrię.</span><span class="sxs-lookup"><span data-stu-id="45386-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="45386-284">Niedozwolone uwierzytelniania podstawowego, za pośrednictwem protokołu HTTP w komunikacji zdalnej programu PowerShell na platformach Unix</span><span class="sxs-lookup"><span data-stu-id="45386-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="45386-285">Aby uniknąć użycia nieszyfrowanego ruchu, komunikacji zdalnej programu PowerShell na platformach Unix wymaga użycia uwierzytelniania NTLM/Negotiate lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="45386-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="45386-286">Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6799 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6799).</span><span class="sxs-lookup"><span data-stu-id="45386-286">For more information on these changes, check out [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="45386-287">Usunięte `VisualBasic` jako obsługiwanego języka w Add-Type</span><span class="sxs-lookup"><span data-stu-id="45386-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="45386-288">W przeszłości można skompilować przy użyciu kodu języka Visual Basic `Add-Type` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45386-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="45386-289">Rzadko używany Visual Basic z `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="45386-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="45386-290">Firma Microsoft usunęła tę funkcję, aby zmniejszyć rozmiar środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45386-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="45386-291">Wyczyszczone zastosowań `CommandTypes.Workflow` i `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="45386-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="45386-292">Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6708 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="45386-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>
