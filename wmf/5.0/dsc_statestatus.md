---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e8d0cb1e4afa7bc791d45bfb0b981654cb09ed5
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892573"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="b0691-102">Ujednolicony i spójny stan oraz reprezentacja stanu</span><span class="sxs-lookup"><span data-stu-id="b0691-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="b0691-103">Szereg ulepszeń zostały wprowadzone w tym wydaniu automatyzacji stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="b0691-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="b0691-104">Obejmują one ujednolicony i spójny stan i stan reprezentacje datetime w zarządzaniu własności stan obiektów zwróconych przez `Get-DscConfigurationStatus` LCM rozszerzone i polecenia cmdlet stanu szczegóły właściwości zwróconej przez `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0691-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="b0691-105">Reprezentacja stanu LCM i stan operacji dla DSC są poprawiony i ujednolicone zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="b0691-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="b0691-106">Notprocessed zasobów nie ma wpływu na stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="b0691-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="b0691-107">LCM zatrzymać dalsze zasoby przetwarzanie po napotkaniu zasobem, który żąda ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="b0691-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="b0691-108">Zasób, który żąda ponownego rozruchu nie jest w żądanym stanie do momentu ponownego uruchomienia rzeczywiście się dzieje.</span><span class="sxs-lookup"><span data-stu-id="b0691-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="b0691-109">Po napotkaniu zasobem, który zakończy się niepowodzeniem, LCM utrzymuje dalsze przetwarzanie zasobów tak długo, jak nie są zależne od awarii jednej.</span><span class="sxs-lookup"><span data-stu-id="b0691-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="b0691-110">Ogólny stan zwrócony przez `Get-DscConfigurationStatus` polecenie cmdlet jest zbiór super stanu wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="b0691-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="b0691-111">Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.</span><span class="sxs-lookup"><span data-stu-id="b0691-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="b0691-112">W poniższej tabeli przedstawiono wynikowe stanu i statusu powiązane właściwości pod kilka typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="b0691-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="b0691-113">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="b0691-113">Scenario</span></span>                    | <span data-ttu-id="b0691-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="b0691-114">LCMState</span></span>       | <span data-ttu-id="b0691-115">Stan</span><span class="sxs-lookup"><span data-stu-id="b0691-115">Status</span></span> | <span data-ttu-id="b0691-116">Wymagane ponowne uruchomienie komputera</span><span class="sxs-lookup"><span data-stu-id="b0691-116">Reboot Requested</span></span>  | <span data-ttu-id="b0691-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b0691-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="b0691-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b0691-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="b0691-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="b0691-119">S**^**</span></span>                          | <span data-ttu-id="b0691-120">W stanie bezczynności</span><span class="sxs-lookup"><span data-stu-id="b0691-120">Idle</span></span>                 | <span data-ttu-id="b0691-121">Success</span><span class="sxs-lookup"><span data-stu-id="b0691-121">Success</span></span>    | <span data-ttu-id="b0691-122">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-122">$false</span></span>        | <span data-ttu-id="b0691-123">S</span><span class="sxs-lookup"><span data-stu-id="b0691-123">S</span></span>                            | <span data-ttu-id="b0691-124">$null</span><span class="sxs-lookup"><span data-stu-id="b0691-124">$null</span></span>                          |
   | <span data-ttu-id="b0691-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="b0691-125">F**^**</span></span>                          | <span data-ttu-id="b0691-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0691-126">PendingConfiguration</span></span> | <span data-ttu-id="b0691-127">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-127">Failure</span></span>    | <span data-ttu-id="b0691-128">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-128">$false</span></span>        | <span data-ttu-id="b0691-129">$null</span><span class="sxs-lookup"><span data-stu-id="b0691-129">$null</span></span>                        | <span data-ttu-id="b0691-130">F</span><span class="sxs-lookup"><span data-stu-id="b0691-130">F</span></span>                              |
   | <span data-ttu-id="b0691-131">S, F</span><span class="sxs-lookup"><span data-stu-id="b0691-131">S,F</span></span>                             | <span data-ttu-id="b0691-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0691-132">PendingConfiguration</span></span> | <span data-ttu-id="b0691-133">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-133">Failure</span></span>    | <span data-ttu-id="b0691-134">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-134">$false</span></span>        | <span data-ttu-id="b0691-135">S</span><span class="sxs-lookup"><span data-stu-id="b0691-135">S</span></span>                            | <span data-ttu-id="b0691-136">F</span><span class="sxs-lookup"><span data-stu-id="b0691-136">F</span></span>                              |
   | <span data-ttu-id="b0691-137">F, S</span><span class="sxs-lookup"><span data-stu-id="b0691-137">F,S</span></span>                             | <span data-ttu-id="b0691-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0691-138">PendingConfiguration</span></span> | <span data-ttu-id="b0691-139">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-139">Failure</span></span>    | <span data-ttu-id="b0691-140">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-140">$false</span></span>        | <span data-ttu-id="b0691-141">S</span><span class="sxs-lookup"><span data-stu-id="b0691-141">S</span></span>                            | <span data-ttu-id="b0691-142">F</span><span class="sxs-lookup"><span data-stu-id="b0691-142">F</span></span>                              |
   | <span data-ttu-id="b0691-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b0691-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="b0691-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0691-144">PendingConfiguration</span></span> | <span data-ttu-id="b0691-145">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-145">Failure</span></span>    | <span data-ttu-id="b0691-146">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-146">$false</span></span>        | <span data-ttu-id="b0691-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b0691-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="b0691-148">F</span><span class="sxs-lookup"><span data-stu-id="b0691-148">F</span></span>                              |
   | <span data-ttu-id="b0691-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b0691-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="b0691-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0691-150">PendingConfiguration</span></span> | <span data-ttu-id="b0691-151">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-151">Failure</span></span>    | <span data-ttu-id="b0691-152">$false</span><span class="sxs-lookup"><span data-stu-id="b0691-152">$false</span></span>        | <span data-ttu-id="b0691-153">S</span><span class="sxs-lookup"><span data-stu-id="b0691-153">S</span></span>                            | <span data-ttu-id="b0691-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b0691-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="b0691-155">S, r</span><span class="sxs-lookup"><span data-stu-id="b0691-155">S, r</span></span>                            | <span data-ttu-id="b0691-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b0691-156">PendingReboot</span></span>        | <span data-ttu-id="b0691-157">Success</span><span class="sxs-lookup"><span data-stu-id="b0691-157">Success</span></span>    | <span data-ttu-id="b0691-158">$true</span><span class="sxs-lookup"><span data-stu-id="b0691-158">$true</span></span>         | <span data-ttu-id="b0691-159">S</span><span class="sxs-lookup"><span data-stu-id="b0691-159">S</span></span>                            | <span data-ttu-id="b0691-160">r</span><span class="sxs-lookup"><span data-stu-id="b0691-160">r</span></span>                              |
   | <span data-ttu-id="b0691-161">F, r</span><span class="sxs-lookup"><span data-stu-id="b0691-161">F, r</span></span>                            | <span data-ttu-id="b0691-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b0691-162">PendingReboot</span></span>        | <span data-ttu-id="b0691-163">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="b0691-163">Failure</span></span>    | <span data-ttu-id="b0691-164">$true</span><span class="sxs-lookup"><span data-stu-id="b0691-164">$true</span></span>         | <span data-ttu-id="b0691-165">$null</span><span class="sxs-lookup"><span data-stu-id="b0691-165">$null</span></span>                        | <span data-ttu-id="b0691-166">F, r</span><span class="sxs-lookup"><span data-stu-id="b0691-166">F, r</span></span>                           |
   | <span data-ttu-id="b0691-167">r, S</span><span class="sxs-lookup"><span data-stu-id="b0691-167">r, S</span></span>                            | <span data-ttu-id="b0691-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b0691-168">PendingReboot</span></span>        | <span data-ttu-id="b0691-169">Success</span><span class="sxs-lookup"><span data-stu-id="b0691-169">Success</span></span>    | <span data-ttu-id="b0691-170">$true</span><span class="sxs-lookup"><span data-stu-id="b0691-170">$true</span></span>         | <span data-ttu-id="b0691-171">$null</span><span class="sxs-lookup"><span data-stu-id="b0691-171">$null</span></span>                        | <span data-ttu-id="b0691-172">r</span><span class="sxs-lookup"><span data-stu-id="b0691-172">r</span></span>                              |
   | <span data-ttu-id="b0691-173">r, F</span><span class="sxs-lookup"><span data-stu-id="b0691-173">r, F</span></span>                            | <span data-ttu-id="b0691-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b0691-174">PendingReboot</span></span>        | <span data-ttu-id="b0691-175">Success</span><span class="sxs-lookup"><span data-stu-id="b0691-175">Success</span></span>    | <span data-ttu-id="b0691-176">$true</span><span class="sxs-lookup"><span data-stu-id="b0691-176">$true</span></span>         | <span data-ttu-id="b0691-177">$null</span><span class="sxs-lookup"><span data-stu-id="b0691-177">$null</span></span>                        | <span data-ttu-id="b0691-178">r</span><span class="sxs-lookup"><span data-stu-id="b0691-178">r</span></span>                              |

   <span data-ttu-id="b0691-179">^
   S<sub>i</sub>: szeregu zasobów, które zostały zastosowane pomyślnie F<sub>i</sub>: szeregu zasobów, które stosowane niepomyślnie zasób r: element, który wymaga ponownego uruchomienia \*</span><span class="sxs-lookup"><span data-stu-id="b0691-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="b0691-180">Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b0691-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="b0691-181">Wprowadzono kilka ulepszeń `Get-DscConfigurationStatus` polecenia cmdlet w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b0691-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="b0691-182">Wcześniej StartDate własności obiektów zwróconych przez polecenie cmdlet jest typu String.</span><span class="sxs-lookup"><span data-stu-id="b0691-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="b0691-183">Teraz jest typu Data/Godzina, co umożliwia złożonych, wybieranie i filtrowanie, łatwiej na podstawie wewnętrzne właściwości obiektu daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="b0691-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
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

<span data-ttu-id="b0691-184">Poniżej znajduje się przykład, która zwraca wszystkie rekordy operacji DSC stało się tego samego dnia, tygodnia, jak już dziś.</span><span class="sxs-lookup"><span data-stu-id="b0691-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="b0691-185">Rejestruje operacje, które należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacji odczytu) są eliminowane.</span><span class="sxs-lookup"><span data-stu-id="b0691-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="b0691-186">W związku z tym `Test-DscConfiguration`, `Get-DscConfiguration` operacje są już zafałszowane za w zwracanych obiektów z `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0691-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="b0691-187">Rekordy operacja ustawienie konfiguracji metadanych jest dodawana do powrotu `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0691-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="b0691-188">Poniżej znajduje się przykład wyniku zwracanego z `Get-DscConfigurationStatus` — wszystkie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0691-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="b0691-189">Rozszerzenie w poleceniu cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b0691-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="b0691-190">Nowe pole LCMStateDetail zostanie dodany do obiektu zwróconego z `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0691-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="b0691-191">To pole jest wypełniane podczas LCMState jest "Zajęty".</span><span class="sxs-lookup"><span data-stu-id="b0691-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="b0691-192">Mogą być pobierane przez następujące polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="b0691-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="b0691-193">Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.</span><span class="sxs-lookup"><span data-stu-id="b0691-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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