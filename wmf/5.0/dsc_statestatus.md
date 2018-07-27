---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: bed1186c10082bbdac7249503bf623678f13fccd
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267943"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="24623-102">Ujednolicony i spójny stan oraz reprezentacja stanu</span><span class="sxs-lookup"><span data-stu-id="24623-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="24623-103">Szereg ulepszeń zostały wprowadzone w tym wydaniu automatyzacji stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="24623-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="24623-104">Obejmują one ujednolicony i spójny stan i stan reprezentacje datetime w zarządzaniu własności stan obiektów zwróconych przez `Get-DscConfigurationStatus` LCM rozszerzone i polecenia cmdlet stanu szczegóły właściwości zwróconej przez `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24623-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="24623-105">Reprezentacja stanu LCM i stan operacji dla DSC są poprawiony i ujednolicone zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="24623-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="24623-106">Notprocessed zasobów nie ma wpływu na stanu LCM i stan DSC.</span><span class="sxs-lookup"><span data-stu-id="24623-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="24623-107">LCM zatrzymać dalsze zasoby przetwarzanie po napotkaniu zasobem, który żąda ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="24623-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="24623-108">Zasób, który żąda ponownego rozruchu nie jest w żądanym stanie do momentu ponownego uruchomienia rzeczywiście się dzieje.</span><span class="sxs-lookup"><span data-stu-id="24623-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="24623-109">Po napotkaniu zasobem, który zakończy się niepowodzeniem, LCM utrzymuje dalsze przetwarzanie zasobów tak długo, jak nie są zależne od awarii jednej.</span><span class="sxs-lookup"><span data-stu-id="24623-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="24623-110">Ogólny stan zwrócony przez `Get-DscConfigurationStatus` polecenie cmdlet jest zbiór super stanu wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="24623-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="24623-111">Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.</span><span class="sxs-lookup"><span data-stu-id="24623-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="24623-112">W poniższej tabeli przedstawiono wynikowe stanu i statusu powiązane właściwości pod kilka typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="24623-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="24623-113">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="24623-113">Scenario</span></span>                        | <span data-ttu-id="24623-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="24623-114">LCMState</span></span>             | <span data-ttu-id="24623-115">Stan</span><span class="sxs-lookup"><span data-stu-id="24623-115">Status</span></span>     | <span data-ttu-id="24623-116">Wymagane ponowne uruchomienie komputera</span><span class="sxs-lookup"><span data-stu-id="24623-116">Reboot Requested</span></span> | <span data-ttu-id="24623-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="24623-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="24623-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="24623-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="24623-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="24623-119">S**^**</span></span>                          | <span data-ttu-id="24623-120">W stanie bezczynności</span><span class="sxs-lookup"><span data-stu-id="24623-120">Idle</span></span>                 | <span data-ttu-id="24623-121">Success</span><span class="sxs-lookup"><span data-stu-id="24623-121">Success</span></span>    | <span data-ttu-id="24623-122">$false</span><span class="sxs-lookup"><span data-stu-id="24623-122">$false</span></span>        | <span data-ttu-id="24623-123">S</span><span class="sxs-lookup"><span data-stu-id="24623-123">S</span></span>                            | <span data-ttu-id="24623-124">$null</span><span class="sxs-lookup"><span data-stu-id="24623-124">$null</span></span>                          |
| <span data-ttu-id="24623-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="24623-125">F**^**</span></span>                          | <span data-ttu-id="24623-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="24623-126">PendingConfiguration</span></span> | <span data-ttu-id="24623-127">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-127">Failure</span></span>    | <span data-ttu-id="24623-128">$false</span><span class="sxs-lookup"><span data-stu-id="24623-128">$false</span></span>        | <span data-ttu-id="24623-129">$null</span><span class="sxs-lookup"><span data-stu-id="24623-129">$null</span></span>                        | <span data-ttu-id="24623-130">F</span><span class="sxs-lookup"><span data-stu-id="24623-130">F</span></span>                              |
| <span data-ttu-id="24623-131">S, F</span><span class="sxs-lookup"><span data-stu-id="24623-131">S,F</span></span>                             | <span data-ttu-id="24623-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="24623-132">PendingConfiguration</span></span> | <span data-ttu-id="24623-133">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-133">Failure</span></span>    | <span data-ttu-id="24623-134">$false</span><span class="sxs-lookup"><span data-stu-id="24623-134">$false</span></span>        | <span data-ttu-id="24623-135">S</span><span class="sxs-lookup"><span data-stu-id="24623-135">S</span></span>                            | <span data-ttu-id="24623-136">F</span><span class="sxs-lookup"><span data-stu-id="24623-136">F</span></span>                              |
| <span data-ttu-id="24623-137">F, S</span><span class="sxs-lookup"><span data-stu-id="24623-137">F,S</span></span>                             | <span data-ttu-id="24623-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="24623-138">PendingConfiguration</span></span> | <span data-ttu-id="24623-139">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-139">Failure</span></span>    | <span data-ttu-id="24623-140">$false</span><span class="sxs-lookup"><span data-stu-id="24623-140">$false</span></span>        | <span data-ttu-id="24623-141">S</span><span class="sxs-lookup"><span data-stu-id="24623-141">S</span></span>                            | <span data-ttu-id="24623-142">F</span><span class="sxs-lookup"><span data-stu-id="24623-142">F</span></span>                              |
| <span data-ttu-id="24623-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="24623-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="24623-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="24623-144">PendingConfiguration</span></span> | <span data-ttu-id="24623-145">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-145">Failure</span></span>    | <span data-ttu-id="24623-146">$false</span><span class="sxs-lookup"><span data-stu-id="24623-146">$false</span></span>        | <span data-ttu-id="24623-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="24623-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="24623-148">F</span><span class="sxs-lookup"><span data-stu-id="24623-148">F</span></span>                              |
| <span data-ttu-id="24623-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="24623-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="24623-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="24623-150">PendingConfiguration</span></span> | <span data-ttu-id="24623-151">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-151">Failure</span></span>    | <span data-ttu-id="24623-152">$false</span><span class="sxs-lookup"><span data-stu-id="24623-152">$false</span></span>        | <span data-ttu-id="24623-153">S</span><span class="sxs-lookup"><span data-stu-id="24623-153">S</span></span>                            | <span data-ttu-id="24623-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="24623-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="24623-155">S, r</span><span class="sxs-lookup"><span data-stu-id="24623-155">S, r</span></span>                            | <span data-ttu-id="24623-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="24623-156">PendingReboot</span></span>        | <span data-ttu-id="24623-157">Success</span><span class="sxs-lookup"><span data-stu-id="24623-157">Success</span></span>    | <span data-ttu-id="24623-158">$true</span><span class="sxs-lookup"><span data-stu-id="24623-158">$true</span></span>         | <span data-ttu-id="24623-159">S</span><span class="sxs-lookup"><span data-stu-id="24623-159">S</span></span>                            | <span data-ttu-id="24623-160">r</span><span class="sxs-lookup"><span data-stu-id="24623-160">r</span></span>                              |
| <span data-ttu-id="24623-161">F, r</span><span class="sxs-lookup"><span data-stu-id="24623-161">F, r</span></span>                            | <span data-ttu-id="24623-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="24623-162">PendingReboot</span></span>        | <span data-ttu-id="24623-163">Niepowodzenie</span><span class="sxs-lookup"><span data-stu-id="24623-163">Failure</span></span>    | <span data-ttu-id="24623-164">$true</span><span class="sxs-lookup"><span data-stu-id="24623-164">$true</span></span>         | <span data-ttu-id="24623-165">$null</span><span class="sxs-lookup"><span data-stu-id="24623-165">$null</span></span>                        | <span data-ttu-id="24623-166">F, r</span><span class="sxs-lookup"><span data-stu-id="24623-166">F, r</span></span>                           |
| <span data-ttu-id="24623-167">r, S</span><span class="sxs-lookup"><span data-stu-id="24623-167">r, S</span></span>                            | <span data-ttu-id="24623-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="24623-168">PendingReboot</span></span>        | <span data-ttu-id="24623-169">Success</span><span class="sxs-lookup"><span data-stu-id="24623-169">Success</span></span>    | <span data-ttu-id="24623-170">$true</span><span class="sxs-lookup"><span data-stu-id="24623-170">$true</span></span>         | <span data-ttu-id="24623-171">$null</span><span class="sxs-lookup"><span data-stu-id="24623-171">$null</span></span>                        | <span data-ttu-id="24623-172">r</span><span class="sxs-lookup"><span data-stu-id="24623-172">r</span></span>                              |
| <span data-ttu-id="24623-173">r, F</span><span class="sxs-lookup"><span data-stu-id="24623-173">r, F</span></span>                            | <span data-ttu-id="24623-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="24623-174">PendingReboot</span></span>        | <span data-ttu-id="24623-175">Success</span><span class="sxs-lookup"><span data-stu-id="24623-175">Success</span></span>    | <span data-ttu-id="24623-176">$true</span><span class="sxs-lookup"><span data-stu-id="24623-176">$true</span></span>         | <span data-ttu-id="24623-177">$null</span><span class="sxs-lookup"><span data-stu-id="24623-177">$null</span></span>                        | <span data-ttu-id="24623-178">r</span><span class="sxs-lookup"><span data-stu-id="24623-178">r</span></span>                              |

- <span data-ttu-id="24623-179">S<sub>i</sub>: szeregu zasobów, które zostały zastosowane pomyślnie</span><span class="sxs-lookup"><span data-stu-id="24623-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="24623-180">F<sub>i</sub>: szeregu zasobów, które stosowane niepomyślnie</span><span class="sxs-lookup"><span data-stu-id="24623-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="24623-181">r: z zasobem, który wymaga ponownego uruchomienia</span><span class="sxs-lookup"><span data-stu-id="24623-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="24623-182">Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="24623-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="24623-183">Wprowadzono kilka ulepszeń `Get-DscConfigurationStatus` polecenia cmdlet w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="24623-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="24623-184">Wcześniej StartDate własności obiektów zwróconych przez polecenie cmdlet jest typu String.</span><span class="sxs-lookup"><span data-stu-id="24623-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="24623-185">Teraz jest typu Data/Godzina, co umożliwia złożonych, wybieranie i filtrowanie, łatwiej na podstawie wewnętrzne właściwości obiektu daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="24623-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

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

<span data-ttu-id="24623-186">Poniższy przykład zwraca wszystkie rekordy operacji DSC, które miały miejsce tego samego dnia, tygodnia jako bieżący dzień.</span><span class="sxs-lookup"><span data-stu-id="24623-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="24623-187">Rejestruje operacje, które należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacji odczytu) są eliminowane.</span><span class="sxs-lookup"><span data-stu-id="24623-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="24623-188">W związku z tym `Test-DscConfiguration`, `Get-DscConfiguration` operacje są już zafałszowane za w zwracanych obiektów z `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24623-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="24623-189">Rekordy operacja ustawienie konfiguracji metadanych jest dodawana do powrotu `Get-DscConfigurationStatus` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24623-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="24623-190">Poniżej znajduje się przykład wyniku zwracanego z `Get-DscConfigurationStatus –All` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24623-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="24623-191">Rozszerzenie w poleceniu cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24623-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="24623-192">Nowe pole LCMStateDetail zostanie dodany do obiektu zwróconego z `Get-DscLocalConfigurationManager` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24623-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="24623-193">To pole jest wypełniane podczas LCMState jest "Zajęty".</span><span class="sxs-lookup"><span data-stu-id="24623-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="24623-194">Mogą być pobierane przez następujące polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="24623-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="24623-195">Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.</span><span class="sxs-lookup"><span data-stu-id="24623-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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