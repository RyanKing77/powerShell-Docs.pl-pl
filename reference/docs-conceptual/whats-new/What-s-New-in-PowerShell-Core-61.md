---
title: Co nowego w programie PowerShell Core 6.1
description: Nowe funkcje i zmiany w programie PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: fe1e892d4a13a7758f5405867fdd7488c059f5cc
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293320"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="f3092-103">Co nowego w programie PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="f3092-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="f3092-104">Poniżej przedstawiono niektóre główne nowe funkcje i zmiany, które zostały wprowadzone w programie PowerShell Core 6.1 wyboru.</span><span class="sxs-lookup"><span data-stu-id="f3092-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="f3092-105">Istnieje również **tonach** "nudnych dostępu", które ułatwiają programu PowerShell, szybsze i bardziej stabilne (plus partii i wiele poprawek)!</span><span class="sxs-lookup"><span data-stu-id="f3092-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="f3092-106">Aby uzyskać pełną listę zmian, zapoznaj się z naszym [dziennika zmian w witrynie GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="f3092-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="f3092-107">I gdy czy powinniśmy zwołać kilka nazw poniżej, aby [wszystkie uczestnicy społeczności](https://github.com/PowerShell/PowerShell/graphs/contributors) , wprowadzonych w tej wersji możliwe.</span><span class="sxs-lookup"><span data-stu-id="f3092-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="f3092-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f3092-108">.NET Core 2.1</span></span>

<span data-ttu-id="f3092-109">PowerShell Core 6.1 przeniesione do platformy .NET Core 2.1, po [wydane w maju](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), dając w efekcie w szereg ulepszeń w programie PowerShell, w tym:</span><span class="sxs-lookup"><span data-stu-id="f3092-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="f3092-110">ulepszenia wydajności (zobacz [poniżej](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="f3092-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="f3092-111">Firma Alpine pomoc techniczna Linux support (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="f3092-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="f3092-112">[Obsługa narzędzia globalnej platformy .NET](/dotnet/core/tools/global-tools) — najbliższych wkrótce do programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3092-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="f3092-113">Windows Compatibility Pack dla programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f3092-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="f3092-114">W Windows, dostarczane przez zespół .NET [systemie Windows Compatibility Pack dla platformy .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), zbiór zestawów, które dodać szereg usunięte interfejsów API do platformy .NET Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="f3092-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="f3092-115">Dodaliśmy pakiet Windows do wersji programu PowerShell Core 6.1, aby wszystkie moduły lub skrypty, które używają tych interfejsów API można polegać na nich dostępne.</span><span class="sxs-lookup"><span data-stu-id="f3092-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="f3092-116">Pakiet Windows umożliwia programu PowerShell Core do użycia **więcej niż 1900 poleceń cmdlet, które są dostarczane z systemem Windows 10 października 2018 Update i Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="f3092-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="f3092-117">Obsługa listy dozwolonych aplikacji</span><span class="sxs-lookup"><span data-stu-id="f3092-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="f3092-118">PowerShell Core 6.1 ma parzystości przy użyciu programu Windows PowerShell 5.1 obsługi [funkcji AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) i [funkcji Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) listy dozwolonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3092-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="f3092-119">Listy dozwolonych aplikacji umożliwia szczegółową kontrolę, z których plików binarnych mogą być wykonywane używany przy użyciu programu PowerShell [Tryb ograniczonego języka](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="f3092-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="f3092-120">Ulepszenia wydajności</span><span class="sxs-lookup"><span data-stu-id="f3092-120">Performance improvements</span></span>

<span data-ttu-id="f3092-121">PowerShell Core 6.0 wprowadzone pewne znaczne ulepszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="f3092-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="f3092-122">PowerShell Core 6.1 w dalszym ciągu przyspieszyć niektóre operacje.</span><span class="sxs-lookup"><span data-stu-id="f3092-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="f3092-123">Na przykład `Group-Object` przyspieszyło o 66%:</span><span class="sxs-lookup"><span data-stu-id="f3092-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="f3092-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f3092-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="f3092-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="f3092-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="f3092-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="f3092-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="f3092-127">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="f3092-127">Time (sec)</span></span>   | <span data-ttu-id="f3092-128">25.178</span><span class="sxs-lookup"><span data-stu-id="f3092-128">25.178</span></span>                 | <span data-ttu-id="f3092-129">19.653</span><span class="sxs-lookup"><span data-stu-id="f3092-129">19.653</span></span>              | <span data-ttu-id="f3092-130">6.641</span><span class="sxs-lookup"><span data-stu-id="f3092-130">6.641</span></span>               |
| <span data-ttu-id="f3092-131">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="f3092-131">Speed-up (%)</span></span> | <span data-ttu-id="f3092-132">Brak</span><span class="sxs-lookup"><span data-stu-id="f3092-132">N/A</span></span>                    | <span data-ttu-id="f3092-133">21.9%</span><span class="sxs-lookup"><span data-stu-id="f3092-133">21.9%</span></span>               | <span data-ttu-id="f3092-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="f3092-134">66.2%</span></span>               |

<span data-ttu-id="f3092-135">Podobnie przez więcej niż 15% ulepszyła scenariusze sortowania podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="f3092-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="f3092-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f3092-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="f3092-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="f3092-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="f3092-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="f3092-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="f3092-139">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="f3092-139">Time (sec)</span></span>   | <span data-ttu-id="f3092-140">12.170</span><span class="sxs-lookup"><span data-stu-id="f3092-140">12.170</span></span>                 | <span data-ttu-id="f3092-141">8.493</span><span class="sxs-lookup"><span data-stu-id="f3092-141">8.493</span></span>               | <span data-ttu-id="f3092-142">7.08</span><span class="sxs-lookup"><span data-stu-id="f3092-142">7.08</span></span>                |
| <span data-ttu-id="f3092-143">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="f3092-143">Speed-up (%)</span></span> | <span data-ttu-id="f3092-144">Brak</span><span class="sxs-lookup"><span data-stu-id="f3092-144">N/A</span></span>                    | <span data-ttu-id="f3092-145">30.2%</span><span class="sxs-lookup"><span data-stu-id="f3092-145">30.2%</span></span>               | <span data-ttu-id="f3092-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="f3092-146">16.6%</span></span>               |

`Import-Csv` <span data-ttu-id="f3092-147">ma również zostały przyspieszyło znacznie po regresji za pomocą programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3092-147">has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="f3092-148">W poniższym przykładzie użyto testu CSV z 26,616 wierszami i kolumnami sześć:</span><span class="sxs-lookup"><span data-stu-id="f3092-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="f3092-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f3092-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="f3092-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="f3092-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="f3092-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="f3092-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="f3092-152">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="f3092-152">Time (sec)</span></span>   | <span data-ttu-id="f3092-153">0.441</span><span class="sxs-lookup"><span data-stu-id="f3092-153">0.441</span></span>                  | <span data-ttu-id="f3092-154">1.069</span><span class="sxs-lookup"><span data-stu-id="f3092-154">1.069</span></span>               | <span data-ttu-id="f3092-155">0.268</span><span class="sxs-lookup"><span data-stu-id="f3092-155">0.268</span></span>                  |
| <span data-ttu-id="f3092-156">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="f3092-156">Speed-up (%)</span></span> | <span data-ttu-id="f3092-157">Brak</span><span class="sxs-lookup"><span data-stu-id="f3092-157">N/A</span></span>                    | <span data-ttu-id="f3092-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="f3092-158">-142.4%</span></span>             | <span data-ttu-id="f3092-159">74.9% (% 39.2 z WPS)</span><span class="sxs-lookup"><span data-stu-id="f3092-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="f3092-160">Na koniec konwersji z formatu JSON do `PSObject` ma zostały przyspieszyło przez więcej niż 50% od środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3092-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="f3092-161">W poniższym przykładzie użyto pliku JSON testu ~ 2MB:</span><span class="sxs-lookup"><span data-stu-id="f3092-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="f3092-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f3092-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="f3092-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="f3092-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="f3092-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="f3092-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="f3092-165">Czas (s)</span><span class="sxs-lookup"><span data-stu-id="f3092-165">Time (sec)</span></span>   | <span data-ttu-id="f3092-166">0.259</span><span class="sxs-lookup"><span data-stu-id="f3092-166">0.259</span></span>                  | <span data-ttu-id="f3092-167">0.577</span><span class="sxs-lookup"><span data-stu-id="f3092-167">0.577</span></span>               | <span data-ttu-id="f3092-168">0.125</span><span class="sxs-lookup"><span data-stu-id="f3092-168">0.125</span></span>                  |
| <span data-ttu-id="f3092-169">Przyspiesz (%)</span><span class="sxs-lookup"><span data-stu-id="f3092-169">Speed-up (%)</span></span> | <span data-ttu-id="f3092-170">Brak</span><span class="sxs-lookup"><span data-stu-id="f3092-170">N/A</span></span>                    | <span data-ttu-id="f3092-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="f3092-171">-122.8%</span></span>             | <span data-ttu-id="f3092-172">78.3% (% 51.7 z WPS)</span><span class="sxs-lookup"><span data-stu-id="f3092-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="f3092-173">Sprawdź `system32` zgodne modułów skrzynkach odbiorczych na Windows</span><span class="sxs-lookup"><span data-stu-id="f3092-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="f3092-174">W Windows Server 2019 i aktualizacji systemu Windows 10 1809 Zaktualizowaliśmy liczbę w polu modułów programu PowerShell, aby oznaczyć je jako niezgodne z programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f3092-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="f3092-175">Podczas uruchamiania programu PowerShell Core 6.1, automatycznie zostanie dołączony `$windir\System32` jako część `PSModulePath` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="f3092-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="f3092-176">Jednak tylko udostępnia ona moduły `Get-Module` i `Import-Module` jeśli jego `CompatiblePSEdition` jest oznaczona jako zgodna z `Core`.</span><span class="sxs-lookup"><span data-stu-id="f3092-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="f3092-177">Może zostać wyświetlony różnych dostępnych modułów, w zależności od tego, jakie role i funkcje są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="f3092-177">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="f3092-178">Można zastąpić to zachowanie, aby pokazać wszystkie moduły przy użyciu `-SkipEditionCheck` parametr przełącznika.</span><span class="sxs-lookup"><span data-stu-id="f3092-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="f3092-179">Dodaliśmy także `PSEdition` właściwości do danych wyjściowych tabeli.</span><span class="sxs-lookup"><span data-stu-id="f3092-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="f3092-180">Aby uzyskać więcej informacji na temat tego zachowania, zapoznaj się z [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="f3092-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="f3092-181">Polecenia cmdlet języka znaczników markdown i renderowanie</span><span class="sxs-lookup"><span data-stu-id="f3092-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="f3092-182">Markdown to standardowe rozwiązanie dla tworzenia dokumentów zwykłego podstawowe formatowanie może być renderowany w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="f3092-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="f3092-183">Dodaliśmy niektórych poleceń cmdlet w 6.1, pozwalających konwersji i renderowania dokumentów języka znaczników Markdown w konsoli, w tym:</span><span class="sxs-lookup"><span data-stu-id="f3092-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="f3092-184">Na przykład `Show-Markdown` renderuje plik języka znaczników Markdown, w konsoli:</span><span class="sxs-lookup"><span data-stu-id="f3092-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Przykład kodu Markdown show](./images/markdown_example.png)

<span data-ttu-id="f3092-186">Aby uzyskać więcej informacji na temat działania tych poleceń cmdlet zapoznaj się z [tej specyfikacji RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="f3092-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="f3092-187">Flagi funkcji eksperymentalnych</span><span class="sxs-lookup"><span data-stu-id="f3092-187">Experimental feature flags</span></span>

<span data-ttu-id="f3092-188">Flagi funkcji eksperymentalnych pozwalają użytkownikom na włączanie funkcji, które jeszcze nie został sfinalizowany.</span><span class="sxs-lookup"><span data-stu-id="f3092-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="f3092-189">Funkcje eksperymentalne nie są obsługiwane i mogą mieć usterek.</span><span class="sxs-lookup"><span data-stu-id="f3092-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="f3092-190">Dowiedz się więcej na temat tej funkcji w [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="f3092-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="f3092-191">Ulepszenia dotyczące polecenia cmdlet w sieci Web</span><span class="sxs-lookup"><span data-stu-id="f3092-191">Web cmdlet improvements</span></span>

<span data-ttu-id="f3092-192">Dzięki [ @markekraus ](https://github.com/markekraus), całe slew ulepszeń zostały wprowadzone do naszych poleceń cmdlet w sieci web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="f3092-192">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="f3092-193">i [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="f3092-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="f3092-194">[6109 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6109) — domyślny zestaw kodowania na UTF-8 dla `application-json` odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="f3092-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="f3092-195">[Żądania Ściągnięcia #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parametru, aby umożliwić `Content-Type` nagłówki, które nie są zgodne z normami</span><span class="sxs-lookup"><span data-stu-id="f3092-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="f3092-196">[Żądania Ściągnięcia #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` uproszczony parametr w celu obsługi `multipart/form-data` pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="f3092-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="f3092-197">[Żądania Ściągnięcia #6338](https://github.com/PowerShell/PowerShell/pull/6338) — zgodne, bez uwzględniania wielkości liter Obsługa kluczy relacji</span><span class="sxs-lookup"><span data-stu-id="f3092-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="f3092-198">[Żądania Ściągnięcia #6447](https://github.com/PowerShell/PowerShell/pull/6447) — Dodaj `-Resume` parametr dla polecenia cmdlet sieci web</span><span class="sxs-lookup"><span data-stu-id="f3092-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="f3092-199">Ulepszenia usług zdalnych</span><span class="sxs-lookup"><span data-stu-id="f3092-199">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="f3092-200">Bezpośrednie PowerShell for Containers spróbuje najpierw użyć programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f3092-200">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="f3092-201">[Bezpośrednie PowerShell](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) jest funkcją programu PowerShell i funkcji Hyper-V, który umożliwia nawiązywanie połączenia z maszyną Wirtualną funkcji Hyper-V lub kontenera bez łączności sieciowej lub innych usług zarządzania zdalnego.</span><span class="sxs-lookup"><span data-stu-id="f3092-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="f3092-202">W przeszłości połączone bezpośrednio z programu PowerShell jest używane wystąpienie programu Windows PowerShell skrzynki odbiorczej w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="f3092-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="f3092-203">Teraz, programu PowerShell Direct najpierw próbuje nawiązać połączenie przy użyciu wszystkie dostępne `pwsh.exe` na `PATH` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="f3092-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="f3092-204">Jeśli `pwsh.exe` nie jest dostępna, programu PowerShell Direct powraca do użycia `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="f3092-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="f3092-205">`Enable-PSRemoting` utworzy teraz punkty końcowe komunikacji zdalnej w oddzielnych wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="f3092-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

`Enable-PSRemoting` <span data-ttu-id="f3092-206">teraz tworzy dwie konfiguracje sesji komunikacji zdalnej:</span><span class="sxs-lookup"><span data-stu-id="f3092-206">now creates two remoting session configurations:</span></span>

- <span data-ttu-id="f3092-207">Jeden dla wersji głównej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3092-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="f3092-208">Na przykład `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="f3092-208">For example, `PowerShell.6`.</span></span> <span data-ttu-id="f3092-209">Ten punkt końcowy, które mogą być powoływane między aktualizacjami wersji pomocniczej konfiguracji sesji programu PowerShell 6 "systemowe"</span><span class="sxs-lookup"><span data-stu-id="f3092-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="f3092-210">Jedna konfiguracja sesji specyficzny dla wersji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="f3092-210">One version-specific session configuration, for example:</span></span> `PowerShell.6.1.0`

<span data-ttu-id="f3092-211">To zachowanie jest przydatne, jeśli chcesz mieć wiele wersji programu PowerShell 6 zainstalowana i jest dostępna na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f3092-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="f3092-212">Ponadto wersji zapoznawczych programu PowerShell teraz uzyskać własnych usług zdalnych konfiguracjami sesji po uruchomieniu `Enable-PSRemoting` polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f3092-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="f3092-213">Dane wyjściowe mogą się różnić, jeśli nie skonfigurowano usługi WinRM przed.</span><span class="sxs-lookup"><span data-stu-id="f3092-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="f3092-214">Następnie możesz zobaczyć oddzielne konfiguracje sesji programu PowerShell w wersji zapoznawczej i stabilny kompilacje z programu PowerShell 6 i dla każdej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="f3092-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="f3092-215">`user@host:port` Składnia obsługiwanych przez protokół SSH</span><span class="sxs-lookup"><span data-stu-id="f3092-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="f3092-216">SSH klientów zwykle obsługują parametry połączenia w formacie `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="f3092-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="f3092-217">Z dodatkiem SSH jako protokół dla niego komunikacji zdalnej programu PowerShell Dodaliśmy obsługę tego formatu ciągu połączenia:</span><span class="sxs-lookup"><span data-stu-id="f3092-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="f3092-218">Opcja MSI można dodać menu kontekstowego powłoki Eksploratora Windows</span><span class="sxs-lookup"><span data-stu-id="f3092-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="f3092-219">Dzięki [ @bergmeister ](https://github.com/bergmeister), teraz można włączyć menu kontekstowego na Windows.</span><span class="sxs-lookup"><span data-stu-id="f3092-219">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="f3092-220">Teraz można otworzyć instalacja systemowe 6.1 programu PowerShell z dowolnego folderu w Eksploratorze Windows:</span><span class="sxs-lookup"><span data-stu-id="f3092-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu kontekstowe powłoki PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="f3092-222">Dodatki</span><span class="sxs-lookup"><span data-stu-id="f3092-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="f3092-223">"Uruchom jako Administrator", w skrócie Windows przejdź do listy</span><span class="sxs-lookup"><span data-stu-id="f3092-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="f3092-224">Dzięki [ @bergmeister ](https://github.com/bergmeister), listy szybkiego dostępu skrótu programu PowerShell Core zawiera teraz "Uruchom jako Administrator":</span><span class="sxs-lookup"><span data-stu-id="f3092-224">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Uruchom jako administrator program PowerShell 6 listy szybkiego dostępu](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="f3092-226">`cd -` Powrót do poprzedniego katalogu</span><span class="sxs-lookup"><span data-stu-id="f3092-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="f3092-227">Lub w systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="f3092-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="f3092-228">Ponadto `cd` i `cd --` Zmień `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="f3092-228">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="f3092-229">Dzięki [ @iSazonov ](https://github.com/iSazonov), [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) ma wydajnej polecenia cmdlet programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f3092-229">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="f3092-230">`Update-Help` jako bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="f3092-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="f3092-231">Popularne popytem `Update-Help` nie musi już być uruchomiony z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="f3092-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
`Update-Help` <span data-ttu-id="f3092-232">teraz domyślnie zapisywania pomocy do folderu o określonym zakresie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f3092-232">now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="f3092-233">Nowe metody/właściwości na `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="f3092-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="f3092-234">Dzięki [ @iSazonov ](https://github.com/iSazonov), dodaliśmy nowe metody i właściwości w celu `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="f3092-234">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
`PSCustomObject` <span data-ttu-id="f3092-235">zawiera teraz `Count` / `Length` właściwości, takich jak inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="f3092-235">now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="f3092-236">Praca ta obejmuje również `ForEach` i `Where` metody, które umożliwiają działanie i przefiltruj `PSCustomObject` elementy:</span><span class="sxs-lookup"><span data-stu-id="f3092-236">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="f3092-237">Dzięki @SimonWahlin, dodaliśmy `-Not` parametr `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="f3092-237">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="f3092-238">Teraz można filtrować obiekt w potoku, który nie istnieje właściwość lub wartość właściwości o wartości null lub być pusty.</span><span class="sxs-lookup"><span data-stu-id="f3092-238">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="f3092-239">Na przykład to polecenie zwraca wszystkie usługi, które nie mają zdefiniowanych żadnych usług zależnych:</span><span class="sxs-lookup"><span data-stu-id="f3092-239">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="f3092-240">`New-ModuleManifest` Tworzy dokument bez BOM UTF-8</span><span class="sxs-lookup"><span data-stu-id="f3092-240">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="f3092-241">Zaktualizowaliśmy udzielone naszego przejścia bez BOM UTF-8 w programie PowerShell w wersji 6.0, `New-ModuleManifest` polecenia cmdlet, aby utworzyć dokument bez BOM UTF-8 zamiast UTF-16, jeden.</span><span class="sxs-lookup"><span data-stu-id="f3092-241">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="f3092-242">Konwersje z PSMethod delegata</span><span class="sxs-lookup"><span data-stu-id="f3092-242">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="f3092-243">Dzięki [ @powercode ](https://github.com/powercode), zapewniamy obecnie obsługę konwersji `PSMethod` do delegata.</span><span class="sxs-lookup"><span data-stu-id="f3092-243">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="f3092-244">Dzięki temu można wykonywać następujące czynności przekazywanie `PSMethod` `[M]::DoubleStrLen` jako wartość delegata do `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="f3092-244">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="f3092-245">Aby uzyskać więcej informacji na temat tej zmiany, zapoznaj się z [5287 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="f3092-245">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="f3092-246">Odchylenie standardowe `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="f3092-246">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="f3092-247">Dzięki [ @CloudyDino ](https://github.com/CloudyDino), dodaliśmy `StandardDeviation` właściwości `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="f3092-247">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="f3092-248">Dzięki [ @maybe-hello-world ](https://github.com/maybe-hello-world), `Get-PfxCertificate` ma teraz `Password` parametr, który przyjmuje `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="f3092-248">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="f3092-249">Dzięki temu można używać go w trybie nieinteraktywnym:</span><span class="sxs-lookup"><span data-stu-id="f3092-249">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="f3092-250">Usuwanie `more` — funkcja</span><span class="sxs-lookup"><span data-stu-id="f3092-250">Removal of the `more` function</span></span>

<span data-ttu-id="f3092-251">W przeszłości, programu PowerShell dostarczanych funkcja na Windows o nazwie `more` który opakowany `more.com`.</span><span class="sxs-lookup"><span data-stu-id="f3092-251">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="f3092-252">Ta funkcja została usunięta.</span><span class="sxs-lookup"><span data-stu-id="f3092-252">That function has now been removed.</span></span>

<span data-ttu-id="f3092-253">Ponadto `help` zmienione, aby używać funkcji `more.com` Windows lub systemu domyślne pagera, określony przez `$env:PAGER` na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="f3092-253">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="f3092-254">`cd DriveName:` teraz zwraca użytkowników do bieżącego katalogu roboczego na tym dysku</span><span class="sxs-lookup"><span data-stu-id="f3092-254">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="f3092-255">Wcześniej przy użyciu `Set-Location` lub `cd` aby powrócić do PSDrive, wysyłane użytkowników do domyślnej lokalizacji dla tego dysku.</span><span class="sxs-lookup"><span data-stu-id="f3092-255">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="f3092-256">Dzięki [ @mcbobke ](https://github.com/mcbobke), użytkownicy są teraz wysyłane do ostatniej znanej bieżący katalog roboczy dla tej sesji.</span><span class="sxs-lookup"><span data-stu-id="f3092-256">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="f3092-257">Akceleratory typu środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3092-257">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="f3092-258">W programie Windows PowerShell dodaliśmy następujące akceleratorów typu w celu ułatwienia pracy z ich odpowiednich typów:</span><span class="sxs-lookup"><span data-stu-id="f3092-258">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- `[adsi]`<span data-ttu-id="f3092-259">:</span><span class="sxs-lookup"><span data-stu-id="f3092-259">:</span></span> `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`<span data-ttu-id="f3092-260">:</span><span class="sxs-lookup"><span data-stu-id="f3092-260">:</span></span> `System.DirectoryServices.DirectorySearcher`
- `[wmi]`<span data-ttu-id="f3092-261">:</span><span class="sxs-lookup"><span data-stu-id="f3092-261">:</span></span> `System.Management.ManagementObject`
- `[wmiclass]`<span data-ttu-id="f3092-262">:</span><span class="sxs-lookup"><span data-stu-id="f3092-262">:</span></span> `System.Management.ManagementClass`
- `[wmisearcher]`<span data-ttu-id="f3092-263">:</span><span class="sxs-lookup"><span data-stu-id="f3092-263">:</span></span> `System.Management.ManagementObjectSearcher`

<span data-ttu-id="f3092-264">Te skróty klawiaturowe typu nie zostały uwzględnione w programie PowerShell 6, ale zostały dodane do 6.1 programu PowerShell w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f3092-264">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="f3092-265">Te typy są przydatne w prosty sposób tworzenia usługi AD i obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="f3092-265">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="f3092-266">Można na przykład zapytania przy użyciu protokołu LDAP:</span><span class="sxs-lookup"><span data-stu-id="f3092-266">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="f3092-267">Poniższy przykład tworzy obiekt Win32_OperatingSystem CIM:</span><span class="sxs-lookup"><span data-stu-id="f3092-267">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="f3092-268">W tym przykładzie zwraca obiekt ManagementClass dla klasy Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="f3092-268">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="f3092-269">`-lp` alias dla wszystkich `-LiteralPath` parametrów</span><span class="sxs-lookup"><span data-stu-id="f3092-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="f3092-270">Dzięki [ @kvprasoon ](https://github.com/kvprasoon), mamy teraz aliasu parametru `-lp` dla wszystkich wbudowanych poleceń cmdlet programu PowerShell, które mają `-LiteralPath` parametru.</span><span class="sxs-lookup"><span data-stu-id="f3092-270">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="f3092-271">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="f3092-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="f3092-272">Instalacja wykonywana przy użyciu pliku MSI ścieżek na Windows</span><span class="sxs-lookup"><span data-stu-id="f3092-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="f3092-273">Na Windows pakiet MSI instaluje teraz w następującej ścieżce:</span><span class="sxs-lookup"><span data-stu-id="f3092-273">On Windows, the MSI package now installs to the following path:</span></span>

- `$env:ProgramFiles\PowerShell\6\` <span data-ttu-id="f3092-274">stabilna instalacji w wersji 6.x</span><span class="sxs-lookup"><span data-stu-id="f3092-274">for the stable installation of 6.x</span></span>
- `$env:ProgramFiles\PowerShell\6-preview\` <span data-ttu-id="f3092-275">dla instalacji w wersji 6.x (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="f3092-275">for the preview installation of 6.x</span></span>

<span data-ttu-id="f3092-276">Ta zmiana zapewnia program PowerShell Core można zaktualizować/obsługiwanych przez usługi Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="f3092-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="f3092-277">Aby uzyskać więcej informacji, zapoznaj się z [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="f3092-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="f3092-278">Telemetrię można wyłączyć tylko za pomocą zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="f3092-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="f3092-279">Program PowerShell Core wysyła dane telemetryczne podstawowe do firmy Microsoft, po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="f3092-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="f3092-280">Dane obejmują nazwę systemu operacyjnego, wersji systemu operacyjnego i wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3092-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="f3092-281">Te dane, pozwala lepiej zrozumieć środowisk, w których program PowerShell jest używany i pozwala nam określić priorytety nowe funkcje i poprawki.</span><span class="sxs-lookup"><span data-stu-id="f3092-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="f3092-282">Aby zrezygnować z tych danych telemetrycznych, ustaw zmienną środowiskową `POWERSHELL_TELEMETRY_OPTOUT` do `true`, `yes`, lub `1`.</span><span class="sxs-lookup"><span data-stu-id="f3092-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="f3092-283">Nie obsługujemy już usunięcia pliku `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` można wyłączyć na telemetrię.</span><span class="sxs-lookup"><span data-stu-id="f3092-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="f3092-284">Niedozwolone uwierzytelniania podstawowego, za pośrednictwem protokołu HTTP w komunikacji zdalnej programu PowerShell na platformach Unix</span><span class="sxs-lookup"><span data-stu-id="f3092-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="f3092-285">Aby uniknąć użycia nieszyfrowanego ruchu, komunikacji zdalnej programu PowerShell na platformach Unix wymaga użycia uwierzytelniania NTLM/Negotiate lub HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f3092-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="f3092-286">Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6779 # problem](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="f3092-286">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="f3092-287">Usunięte `VisualBasic` jako obsługiwanego języka w Add-Type</span><span class="sxs-lookup"><span data-stu-id="f3092-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="f3092-288">W przeszłości można skompilować przy użyciu kodu języka Visual Basic `Add-Type` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3092-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="f3092-289">Rzadko używany Visual Basic z `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="f3092-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="f3092-290">Firma Microsoft usunęła tę funkcję, aby zmniejszyć rozmiar środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3092-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="f3092-291">Wyczyszczone zastosowań `CommandTypes.Workflow` i `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="f3092-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="f3092-292">Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6708 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="f3092-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="f3092-293">Obiekt grupy teraz sortuje grupy</span><span class="sxs-lookup"><span data-stu-id="f3092-293">Group-Object now sorts the groups</span></span>

<span data-ttu-id="f3092-294">Zwiększenie wydajności w ramach `Group-Object` teraz zwraca posortowaną listę grup.</span><span class="sxs-lookup"><span data-stu-id="f3092-294">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="f3092-295">Mimo że nie należy polegać na kolejności, należy można zaburzyć przez tę zmianę jeśli chce się pierwszą grupę.</span><span class="sxs-lookup"><span data-stu-id="f3092-295">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="f3092-296">Jednak firma Microsoft uznała, że ta poprawa wydajności było warte zmiany, ponieważ brakuje wpływ zależne od poprzedniego zachowania.</span><span class="sxs-lookup"><span data-stu-id="f3092-296">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="f3092-297">Aby uzyskać więcej informacji na temat tej zmiany, zobacz [7409 # problem](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="f3092-297">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>
