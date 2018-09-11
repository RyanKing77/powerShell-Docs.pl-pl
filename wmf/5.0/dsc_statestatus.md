---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339875"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="944b6-102">Ujednolicony i spójny stan oraz reprezentacja stanu</span><span class="sxs-lookup"><span data-stu-id="944b6-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="944b6-103">Szereg ulepszeń zostały wprowadzone w tym wydaniu automatyzacji stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="944b6-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="944b6-104">Obejmują one ujednolicony i spójny stan i stan reprezentacje datetime w zarządzaniu własności stan obiektów zwróconych przez `Get-DscConfigurationStatus` LCM rozszerzone i polecenia cmdlet stanu szczegóły właściwości zwróconej przez `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="944b6-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="944b6-105">Reprezentacja stanu LCM i stan operacji dla DSC są poprawiony i ujednolicone zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="944b6-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="944b6-106">Notprocessed zasobów nie ma wpływu na stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="944b6-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="944b6-107">LCM zatrzymać dalsze zasoby przetwarzanie po napotkaniu zasobem, który żąda ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="944b6-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="944b6-108">Zasób, który żąda ponownego rozruchu nie jest w żądanym stanie do momentu ponownego uruchomienia rzeczywiście się dzieje.</span><span class="sxs-lookup"><span data-stu-id="944b6-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="944b6-109">Po napotkaniu zasobem, który zakończy się niepowodzeniem, LCM utrzymuje dalsze przetwarzanie zasobów tak długo, jak nie są zależne od awarii jednej.</span><span class="sxs-lookup"><span data-stu-id="944b6-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="944b6-110">Ogólny stan zwrócony przez `Get-DscConfigurationStatus` polecenie cmdlet jest zbiór super stanu wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="944b6-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="944b6-111">Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.</span><span class="sxs-lookup"><span data-stu-id="944b6-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="944b6-112">W poniższej tabeli przedstawiono wynikowe stanu i statusu powiązane właściwości pod kilka typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="944b6-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="944b6-113">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="944b6-113">Scenario</span></span>                        | <span data-ttu-id="944b6-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="944b6-114">LCMState</span></span>             | <span data-ttu-id="944b6-115">Stan</span><span class="sxs-lookup"><span data-stu-id="944b6-115">Status</span></span>     | <span data-ttu-id="944b6-116">Wymagane ponowne uruchomienie komputera</span><span class="sxs-lookup"><span data-stu-id="944b6-116">Reboot Requested</span></span> | <span data-ttu-id="944b6-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="944b6-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="944b6-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="944b6-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="944b6-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="944b6-120">W stanie bezczynności</span><span class="sxs-lookup"><span data-stu-id="944b6-120">Idle</span></span>                 | <span data-ttu-id="944b6-121">Success</span><span class="sxs-lookup"><span data-stu-id="944b6-121">Success</span></span>    | <span data-ttu-id="944b6-122">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-122">$false</span></span>        | <span data-ttu-id="944b6-123">S</span><span class="sxs-lookup"><span data-stu-id="944b6-123">S</span></span>                            | <span data-ttu-id="944b6-124">$null</span><span class="sxs-lookup"><span data-stu-id="944b6-124">$null</span></span>                          |
| <span data-ttu-id="944b6-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="944b6-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="944b6-126">PendingConfiguration</span></span> | <span data-ttu-id="944b6-127">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-127">Failure</span></span>    | <span data-ttu-id="944b6-128">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-128">$false</span></span>        | <span data-ttu-id="944b6-129">$null</span><span class="sxs-lookup"><span data-stu-id="944b6-129">$null</span></span>                        | <span data-ttu-id="944b6-130">F</span><span class="sxs-lookup"><span data-stu-id="944b6-130">F</span></span>                              |
| <span data-ttu-id="944b6-131">S, F</span><span class="sxs-lookup"><span data-stu-id="944b6-131">S,F</span></span>                             | <span data-ttu-id="944b6-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="944b6-132">PendingConfiguration</span></span> | <span data-ttu-id="944b6-133">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-133">Failure</span></span>    | <span data-ttu-id="944b6-134">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-134">$false</span></span>        | <span data-ttu-id="944b6-135">S</span><span class="sxs-lookup"><span data-stu-id="944b6-135">S</span></span>                            | <span data-ttu-id="944b6-136">F</span><span class="sxs-lookup"><span data-stu-id="944b6-136">F</span></span>                              |
| <span data-ttu-id="944b6-137">F, S</span><span class="sxs-lookup"><span data-stu-id="944b6-137">F,S</span></span>                             | <span data-ttu-id="944b6-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="944b6-138">PendingConfiguration</span></span> | <span data-ttu-id="944b6-139">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-139">Failure</span></span>    | <span data-ttu-id="944b6-140">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-140">$false</span></span>        | <span data-ttu-id="944b6-141">S</span><span class="sxs-lookup"><span data-stu-id="944b6-141">S</span></span>                            | <span data-ttu-id="944b6-142">F</span><span class="sxs-lookup"><span data-stu-id="944b6-142">F</span></span>                              |
| <span data-ttu-id="944b6-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="944b6-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="944b6-144">PendingConfiguration</span></span> | <span data-ttu-id="944b6-145">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-145">Failure</span></span>    | <span data-ttu-id="944b6-146">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-146">$false</span></span>        | <span data-ttu-id="944b6-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="944b6-148">F</span><span class="sxs-lookup"><span data-stu-id="944b6-148">F</span></span>                              |
| <span data-ttu-id="944b6-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="944b6-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="944b6-150">PendingConfiguration</span></span> | <span data-ttu-id="944b6-151">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-151">Failure</span></span>    | <span data-ttu-id="944b6-152">$false</span><span class="sxs-lookup"><span data-stu-id="944b6-152">$false</span></span>        | <span data-ttu-id="944b6-153">S</span><span class="sxs-lookup"><span data-stu-id="944b6-153">S</span></span>                            | <span data-ttu-id="944b6-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="944b6-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="944b6-155">S, r</span><span class="sxs-lookup"><span data-stu-id="944b6-155">S, r</span></span>                            | <span data-ttu-id="944b6-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="944b6-156">PendingReboot</span></span>        | <span data-ttu-id="944b6-157">Success</span><span class="sxs-lookup"><span data-stu-id="944b6-157">Success</span></span>    | <span data-ttu-id="944b6-158">$true</span><span class="sxs-lookup"><span data-stu-id="944b6-158">$true</span></span>         | <span data-ttu-id="944b6-159">S</span><span class="sxs-lookup"><span data-stu-id="944b6-159">S</span></span>                            | <span data-ttu-id="944b6-160">r</span><span class="sxs-lookup"><span data-stu-id="944b6-160">r</span></span>                              |
| <span data-ttu-id="944b6-161">F, r</span><span class="sxs-lookup"><span data-stu-id="944b6-161">F, r</span></span>                            | <span data-ttu-id="944b6-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="944b6-162">PendingReboot</span></span>        | <span data-ttu-id="944b6-163">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="944b6-163">Failure</span></span>    | <span data-ttu-id="944b6-164">$true</span><span class="sxs-lookup"><span data-stu-id="944b6-164">$true</span></span>         | <span data-ttu-id="944b6-165">$null</span><span class="sxs-lookup"><span data-stu-id="944b6-165">$null</span></span>                        | <span data-ttu-id="944b6-166">F, r</span><span class="sxs-lookup"><span data-stu-id="944b6-166">F, r</span></span>                           |
| <span data-ttu-id="944b6-167">r, S</span><span class="sxs-lookup"><span data-stu-id="944b6-167">r, S</span></span>                            | <span data-ttu-id="944b6-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="944b6-168">PendingReboot</span></span>        | <span data-ttu-id="944b6-169">Success</span><span class="sxs-lookup"><span data-stu-id="944b6-169">Success</span></span>    | <span data-ttu-id="944b6-170">$true</span><span class="sxs-lookup"><span data-stu-id="944b6-170">$true</span></span>         | <span data-ttu-id="944b6-171">$null</span><span class="sxs-lookup"><span data-stu-id="944b6-171">$null</span></span>                        | <span data-ttu-id="944b6-172">r</span><span class="sxs-lookup"><span data-stu-id="944b6-172">r</span></span>                              |
| <span data-ttu-id="944b6-173">r, F</span><span class="sxs-lookup"><span data-stu-id="944b6-173">r, F</span></span>                            | <span data-ttu-id="944b6-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="944b6-174">PendingReboot</span></span>        | <span data-ttu-id="944b6-175">Success</span><span class="sxs-lookup"><span data-stu-id="944b6-175">Success</span></span>    | <span data-ttu-id="944b6-176">$true</span><span class="sxs-lookup"><span data-stu-id="944b6-176">$true</span></span>         | <span data-ttu-id="944b6-177">$null</span><span class="sxs-lookup"><span data-stu-id="944b6-177">$null</span></span>                        | <span data-ttu-id="944b6-178">r</span><span class="sxs-lookup"><span data-stu-id="944b6-178">r</span></span>                              |

- <span data-ttu-id="944b6-179">S<sub>i</sub>: szeregu zasobów, które zostały zastosowane pomyślnie</span><span class="sxs-lookup"><span data-stu-id="944b6-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="944b6-180">F<sub>i</sub>: szeregu zasobów, które stosowane niepomyślnie</span><span class="sxs-lookup"><span data-stu-id="944b6-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="944b6-181">r: z zasobem, który wymaga ponownego uruchomienia</span><span class="sxs-lookup"><span data-stu-id="944b6-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="944b6-182">Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="944b6-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="944b6-183">Wprowadzono kilka ulepszeń `Get-DscConfigurationStatus` polecenia cmdlet w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="944b6-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="944b6-184">Wcześniej StartDate własności obiektów zwróconych przez polecenie cmdlet jest typu String.</span><span class="sxs-lookup"><span data-stu-id="944b6-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="944b6-185">Teraz jest typu Data/Godzina, co umożliwia złożonych, wybieranie i filtrowanie, łatwiej na podstawie wewnętrzne właściwości obiektu daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="944b6-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="944b6-186">Poniższy przykład zwraca wszystkie rekordy operacji DSC, które miały miejsce tego samego dnia, tygodnia jako bieżący dzień.</span><span class="sxs-lookup"><span data-stu-id="944b6-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="944b6-187">Rejestruje operacje, które należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacji odczytu) są eliminowane.</span><span class="sxs-lookup"><span data-stu-id="944b6-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="944b6-188">W związku z tym `Test-DscConfiguration`, `Get-DscConfiguration` operacje są już zafałszowane za w zwracanych obiektów z `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="944b6-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="944b6-189">Rekordy operacja ustawienie konfiguracji metadanych jest dodawana do powrotu `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="944b6-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="944b6-190">Poniżej znajduje się przykład wyniku zwracanego z `Get-DscConfigurationStatus –All` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="944b6-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="944b6-191">Rozszerzenie w poleceniu cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="944b6-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="944b6-192">Nowe pole LCMStateDetail zostanie dodany do obiektu zwróconego z `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="944b6-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="944b6-193">To pole jest wypełniane podczas LCMState jest "Zajęty".</span><span class="sxs-lookup"><span data-stu-id="944b6-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="944b6-194">Mogą być pobierane przez następujące polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="944b6-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="944b6-195">Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.</span><span class="sxs-lookup"><span data-stu-id="944b6-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
