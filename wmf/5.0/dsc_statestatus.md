---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 272843efb68c42105af6eb88ad6a95b581da47ae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="5f976-102">Ujednolicony i spójny stan oraz reprezentacja stanu</span><span class="sxs-lookup"><span data-stu-id="5f976-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="5f976-103">Szereg ulepszeń zostały wprowadzone w tej wersji dla wbudowanych LCM stan i stan usługi Konfiguracja DSC automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="5f976-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="5f976-104">Obejmują one ujednoliconego i spójny stan i stan oświadczenia, właściwości datetime można zarządzać stan obiektów zwróconych przez polecenie cmdlet Get-DscConfigurationStatus i rozszerzone właściwości szczegółów stanu LCM zwrócony przez Get DscLocalConfigurationManager polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f976-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="5f976-105">Reprezentacja LCM stan i stan operacji DSC są poprawione i ujednolicone zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="5f976-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="5f976-106">Notprocessed zasobów nie będzie mieć wpływu LCM stan i stan usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="5f976-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="5f976-107">Zatrzymaj LCM dalsze przetwarzanie zasobów po napotkaniu z zasobem, który żąda ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="5f976-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="5f976-108">Zasób, który żąda ponownego uruchomienia nie jest w żądanym stanie do momentu ponownego uruchomienia wystąpi.</span><span class="sxs-lookup"><span data-stu-id="5f976-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="5f976-109">Po napotkaniu zasobu, który zakończy się niepowodzeniem, LCM śledzi dalsze przetwarzanie zasobów tak długo, jak nie są one zależne od awarii jednego.</span><span class="sxs-lookup"><span data-stu-id="5f976-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="5f976-110">Ogólne informacje o stanie zwracanych przez polecenie cmdlet Get-DscConfigurationStatus jest superklasą zbiór stanu wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="5f976-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources’ status.</span></span>
6.  <span data-ttu-id="5f976-111">Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.</span><span class="sxs-lookup"><span data-stu-id="5f976-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="5f976-112">W poniższej tabeli pokazano wynikowe stan i stan powiązane właściwości w obszarze kilka typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="5f976-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="5f976-113">**Scenariusz**</span><span class="sxs-lookup"><span data-stu-id="5f976-113">**Scenario**</span></span>                    | <span data-ttu-id="5f976-114">**LCMState\***</span><span class="sxs-lookup"><span data-stu-id="5f976-114">**LCMState\***</span></span>       | <span data-ttu-id="5f976-115">**Stan**</span><span class="sxs-lookup"><span data-stu-id="5f976-115">**Status**</span></span> | <span data-ttu-id="5f976-116">**Wymagane ponowne uruchomienie komputera**</span><span class="sxs-lookup"><span data-stu-id="5f976-116">**Reboot Requested**</span></span>  | <span data-ttu-id="5f976-117">**ResourcesInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="5f976-117">**ResourcesInDesiredState**</span></span>  | <span data-ttu-id="5f976-118">**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="5f976-118">**ResourcesNotInDesiredState**</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="5f976-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="5f976-119">S**^**</span></span>                          | <span data-ttu-id="5f976-120">W stanie bezczynności</span><span class="sxs-lookup"><span data-stu-id="5f976-120">Idle</span></span>                 | <span data-ttu-id="5f976-121">Success</span><span class="sxs-lookup"><span data-stu-id="5f976-121">Success</span></span>    | <span data-ttu-id="5f976-122">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-122">$false</span></span>        | <span data-ttu-id="5f976-123">S</span><span class="sxs-lookup"><span data-stu-id="5f976-123">S</span></span>                            | <span data-ttu-id="5f976-124">$null</span><span class="sxs-lookup"><span data-stu-id="5f976-124">$null</span></span>                          |
| <span data-ttu-id="5f976-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="5f976-125">F**^**</span></span>                          | <span data-ttu-id="5f976-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f976-126">PendingConfiguration</span></span> | <span data-ttu-id="5f976-127">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-127">Failure</span></span>    | <span data-ttu-id="5f976-128">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-128">$false</span></span>        | <span data-ttu-id="5f976-129">$null</span><span class="sxs-lookup"><span data-stu-id="5f976-129">$null</span></span>                        | <span data-ttu-id="5f976-130">F</span><span class="sxs-lookup"><span data-stu-id="5f976-130">F</span></span>                              |
| <span data-ttu-id="5f976-131">S, F</span><span class="sxs-lookup"><span data-stu-id="5f976-131">S,F</span></span>                             | <span data-ttu-id="5f976-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f976-132">PendingConfiguration</span></span> | <span data-ttu-id="5f976-133">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-133">Failure</span></span>    | <span data-ttu-id="5f976-134">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-134">$false</span></span>        | <span data-ttu-id="5f976-135">S</span><span class="sxs-lookup"><span data-stu-id="5f976-135">S</span></span>                            | <span data-ttu-id="5f976-136">F</span><span class="sxs-lookup"><span data-stu-id="5f976-136">F</span></span>                              |
| <span data-ttu-id="5f976-137">F-S</span><span class="sxs-lookup"><span data-stu-id="5f976-137">F,S</span></span>                             | <span data-ttu-id="5f976-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f976-138">PendingConfiguration</span></span> | <span data-ttu-id="5f976-139">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-139">Failure</span></span>    | <span data-ttu-id="5f976-140">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-140">$false</span></span>        | <span data-ttu-id="5f976-141">S</span><span class="sxs-lookup"><span data-stu-id="5f976-141">S</span></span>                            | <span data-ttu-id="5f976-142">F</span><span class="sxs-lookup"><span data-stu-id="5f976-142">F</span></span>                              |
| <span data-ttu-id="5f976-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="5f976-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="5f976-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f976-144">PendingConfiguration</span></span> | <span data-ttu-id="5f976-145">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-145">Failure</span></span>    | <span data-ttu-id="5f976-146">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-146">$false</span></span>        | <span data-ttu-id="5f976-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="5f976-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="5f976-148">F</span><span class="sxs-lookup"><span data-stu-id="5f976-148">F</span></span>                              |
| <span data-ttu-id="5f976-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="5f976-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="5f976-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f976-150">PendingConfiguration</span></span> | <span data-ttu-id="5f976-151">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-151">Failure</span></span>    | <span data-ttu-id="5f976-152">$false</span><span class="sxs-lookup"><span data-stu-id="5f976-152">$false</span></span>        | <span data-ttu-id="5f976-153">S</span><span class="sxs-lookup"><span data-stu-id="5f976-153">S</span></span>                            | <span data-ttu-id="5f976-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="5f976-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="5f976-155">S, r</span><span class="sxs-lookup"><span data-stu-id="5f976-155">S, r</span></span>                            | <span data-ttu-id="5f976-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="5f976-156">PendingReboot</span></span>        | <span data-ttu-id="5f976-157">Success</span><span class="sxs-lookup"><span data-stu-id="5f976-157">Success</span></span>    | <span data-ttu-id="5f976-158">$true</span><span class="sxs-lookup"><span data-stu-id="5f976-158">$true</span></span>         | <span data-ttu-id="5f976-159">S</span><span class="sxs-lookup"><span data-stu-id="5f976-159">S</span></span>                            | <span data-ttu-id="5f976-160">r</span><span class="sxs-lookup"><span data-stu-id="5f976-160">r</span></span>                              |
| <span data-ttu-id="5f976-161">F, r</span><span class="sxs-lookup"><span data-stu-id="5f976-161">F, r</span></span>                            | <span data-ttu-id="5f976-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="5f976-162">PendingReboot</span></span>        | <span data-ttu-id="5f976-163">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="5f976-163">Failure</span></span>    | <span data-ttu-id="5f976-164">$true</span><span class="sxs-lookup"><span data-stu-id="5f976-164">$true</span></span>         | <span data-ttu-id="5f976-165">$null</span><span class="sxs-lookup"><span data-stu-id="5f976-165">$null</span></span>                        | <span data-ttu-id="5f976-166">F, r</span><span class="sxs-lookup"><span data-stu-id="5f976-166">F, r</span></span>                           |
| <span data-ttu-id="5f976-167">r, S</span><span class="sxs-lookup"><span data-stu-id="5f976-167">r, S</span></span>                            | <span data-ttu-id="5f976-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="5f976-168">PendingReboot</span></span>        | <span data-ttu-id="5f976-169">Success</span><span class="sxs-lookup"><span data-stu-id="5f976-169">Success</span></span>    | <span data-ttu-id="5f976-170">$true</span><span class="sxs-lookup"><span data-stu-id="5f976-170">$true</span></span>         | <span data-ttu-id="5f976-171">$null</span><span class="sxs-lookup"><span data-stu-id="5f976-171">$null</span></span>                        | <span data-ttu-id="5f976-172">r</span><span class="sxs-lookup"><span data-stu-id="5f976-172">r</span></span>                              |
| <span data-ttu-id="5f976-173">r, F</span><span class="sxs-lookup"><span data-stu-id="5f976-173">r, F</span></span>                            | <span data-ttu-id="5f976-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="5f976-174">PendingReboot</span></span>        | <span data-ttu-id="5f976-175">Success</span><span class="sxs-lookup"><span data-stu-id="5f976-175">Success</span></span>    | <span data-ttu-id="5f976-176">$true</span><span class="sxs-lookup"><span data-stu-id="5f976-176">$true</span></span>         | <span data-ttu-id="5f976-177">$null</span><span class="sxs-lookup"><span data-stu-id="5f976-177">$null</span></span>                        | <span data-ttu-id="5f976-178">r</span><span class="sxs-lookup"><span data-stu-id="5f976-178">r</span></span>                              |

<span data-ttu-id="5f976-179">^ S<sub>i</sub>: szeregu zasobów, które zostały zastosowane F<sub>i</sub>: szeregu zasobów, które są stosowane niepomyślnie r: A zasobem, który wymaga ponownego uruchomienia \*</span><span class="sxs-lookup"><span data-stu-id="5f976-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="5f976-180">Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5f976-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="5f976-181">Polecenie cmdlet Get-DscConfigurationStatus w tej wersji wprowadzono kilka ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="5f976-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="5f976-182">Wcześniej właściwość data_rozpoczęcia obiektów zwróconych przez polecenie cmdlet jest typu String.</span><span class="sxs-lookup"><span data-stu-id="5f976-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="5f976-183">Teraz jest typu Data/Godzina, dzięki czemu złożonych, wybierając i filtrowanie łatwiej na podstawie wewnętrznych właściwości obiektu Datetime.</span><span class="sxs-lookup"><span data-stu-id="5f976-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="5f976-184">Poniżej przedstawiono przykład zwraca wszystkie rekordy operacji DSC się stało z tego samego dnia, tygodnia, w obecnie.</span><span class="sxs-lookup"><span data-stu-id="5f976-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="5f976-185">Rejestruje operacje, które nie należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacje odczytu) są eliminowane.</span><span class="sxs-lookup"><span data-stu-id="5f976-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="5f976-186">W związku z tym Test-DscConfiguration operacji Get-DscConfiguration są już zafałszowane za w zwróciło obiektów z polecenia cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="5f976-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="5f976-187">Rekordy operacji określania ustawień konfiguracji metadanych jest dodawana do powrotu polecenia cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="5f976-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="5f976-188">Poniżej przedstawiono przykładowy wynik zwracany z Get-DscConfigurationStatus — wszystkie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f976-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="5f976-189">Rozszerzenie w poleceniu cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5f976-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>
<span data-ttu-id="5f976-190">Nowe pole LCMStateDetail jest dodawany do obiektu zwróconego z polecenia cmdlet Get-DscLocalConfigurationManager.</span><span class="sxs-lookup"><span data-stu-id="5f976-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="5f976-191">To pole jest wypełniane podczas LCMState jest "Zajęty".</span><span class="sxs-lookup"><span data-stu-id="5f976-191">This field is populated when LCMState is “Busy”.</span></span> <span data-ttu-id="5f976-192">Mogą być pobierane przez następujące polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5f976-192">It can be retrieved by following cmdlet:</span></span>
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="5f976-193">Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.</span><span class="sxs-lookup"><span data-stu-id="5f976-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>
```powershell
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
