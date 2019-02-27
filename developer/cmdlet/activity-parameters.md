---
title: Parametry działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849091"
---
# <a name="activity-parameters"></a><span data-ttu-id="7c7fc-102">Parametry działań</span><span class="sxs-lookup"><span data-stu-id="7c7fc-102">Activity Parameters</span></span>

<span data-ttu-id="7c7fc-103">W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów działań.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

<span data-ttu-id="7c7fc-104">Dołącz — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-104">Append Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-105">Implementowanie tego parametru, użytkownik może dodawać zawartość do końca zasobu, jeśli określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-105">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-106">Typ danych CaseSensitive: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-106">CaseSensitive Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-107">Implementuje ten parametr, dzięki czemu użytkownik może wymagać rozróżnianie wielkości liter, jeśli określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-107">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-108">Typ danych z poleceń: Ciąg</span><span class="sxs-lookup"><span data-stu-id="7c7fc-108">Command Data type: String</span></span>

<span data-ttu-id="7c7fc-109">Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić ciąg polecenia do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-109">Implement this parameter so the user can specify a command string to run.</span></span>

<span data-ttu-id="7c7fc-110">Typ danych CompatibleVersion: Obiekt System.Version</span><span class="sxs-lookup"><span data-stu-id="7c7fc-110">CompatibleVersion Data type: System.Version object</span></span>

<span data-ttu-id="7c7fc-111">Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić semantykę, która polecenie cmdlet musi być zgodny z potrzeby utrzymywania zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-111">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>

<span data-ttu-id="7c7fc-112">Kompresuj — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-112">Compress Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-113">Implementowanie tego parametru, kompresja danych jest używany, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-113">Implement this parameter so that data compression is used when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-114">Kompresuj — typ danych: Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="7c7fc-114">Compress Data type: Keyword</span></span>

<span data-ttu-id="7c7fc-115">Implementowanie tego parametru, użytkownik może określić algorytm kompresji danych.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-115">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>

<span data-ttu-id="7c7fc-116">Ciągłe typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-116">Continuous Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-117">Implementowanie tego parametru, dane zostaną przetworzone, dopóki użytkownik kończy działanie polecenia cmdlet, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-117">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-118">Jeśli parametr nie jest określony, polecenie cmdlet przetwarza wstępnie zdefiniowanych ilości danych i następnie kończy operację.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-118">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>

<span data-ttu-id="7c7fc-119">Utwórz typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-119">Create Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-120">Implementowanie tego parametru, aby wskazać, czy zasób został utworzony, jeśli jeden nie już istnieć, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-120">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-121">Usuń typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-121">Delete Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-122">Implementowanie tego parametru, aby zasoby zostaną usunięte po zakończeniu jego działania polecenia cmdlet, jeśli określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-122">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-123">Opróżnij — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-123">Drain Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-124">Implementowanie tego parametru, aby wskazać, że elementy robocze oczekujących są przetwarzane przed polecenia cmdlet przetwarza nowe dane, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-124">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-125">Jeśli parametr nie jest określony, elementy robocze są przetwarzane od razu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-125">If the parameter is not specified, the work items are processed immediately.</span></span>

<span data-ttu-id="7c7fc-126">ERASE — typ danych: Int32</span><span class="sxs-lookup"><span data-stu-id="7c7fc-126">Erase Data type: Int32</span></span>

<span data-ttu-id="7c7fc-127">Implementowanie tego parametru, użytkownik może określić liczbę przypadków, gdy zasób jest usunięte przed usunięciem.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-127">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>

<span data-ttu-id="7c7fc-128">Typ danych parametru ErrorLevel: Int32</span><span class="sxs-lookup"><span data-stu-id="7c7fc-128">ErrorLevel Data type: Int32</span></span>

<span data-ttu-id="7c7fc-129">Implementowanie tego parametru, użytkownik może określić poziom błędów do zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-129">Implement this parameter so that the user can specify the level of errors to report.</span></span>

<span data-ttu-id="7c7fc-130">Wyklucz — typ danych: Ciąg]</span><span class="sxs-lookup"><span data-stu-id="7c7fc-130">Exclude Data type: String[]</span></span>

<span data-ttu-id="7c7fc-131">Implementowanie tego parametru, aby użytkownik wykluczyć coś z działania.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-131">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="7c7fc-132">Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7c7fc-132">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="7c7fc-133">Filtruj typ danych: Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="7c7fc-133">Filter Data type: Keyword</span></span>

<span data-ttu-id="7c7fc-134">Implementowanie tego parametru, użytkownik może określić filtr, który wybiera zasoby, na którym do wykonania tego działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-134">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="7c7fc-135">Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7c7fc-135">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="7c7fc-136">Postępuj zgodnie z typem danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-136">Follow Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-137">Implementowanie tego parametru, postęp jest widoczny, jeśli określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-137">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-138">Wymusić typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-138">Force Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-139">Implementuje ten parametr, aby wskazać, że użytkownik będzie mógł wykonać akcję nawet, jeśli ograniczenia zostaną napotkane, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-139">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-140">Parametr nie zezwala na zabezpieczenia, aby być narażone na ataki.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-140">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="7c7fc-141">Na przykład ten parametr umożliwia użytkownikowi zastąpić plik tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-141">For example, this parameter lets a user overwrite a read-only file.</span></span>

<span data-ttu-id="7c7fc-142">Obejmują typ danych: Ciąg]</span><span class="sxs-lookup"><span data-stu-id="7c7fc-142">Include Data type: String[]</span></span>

<span data-ttu-id="7c7fc-143">Implementowanie tego parametru, użytkownik może zawierać coś w działaniu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-143">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="7c7fc-144">Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7c7fc-144">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="7c7fc-145">Typ danych przyrostowe: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-145">Incremental Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-146">Implementowanie tego parametru, aby wskazać, że przetwarzanie odbywa się przyrostowo gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-146">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-147">Na przykład ten parametr umożliwia użytkownikowi wykonywać przyrostowe kopie zapasowe, które wykonują kopie zapasowe plików tylko od czasu ostatniej kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-147">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>

<span data-ttu-id="7c7fc-148">Typ danych InputObject: Obiekt</span><span class="sxs-lookup"><span data-stu-id="7c7fc-148">InputObject Data type: Object</span></span>

<span data-ttu-id="7c7fc-149">Implementuje ten parametr, gdy polecenie cmdlet pobiera inne polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-149">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="7c7fc-150">Podczas definiowania `InputObject` parametru zawsze określać `ValueFromPipeline` — słowo kluczowe, kiedy Deklarujesz **parametru** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-150">When you define an `InputObject` parameter, always specify the `ValueFromPipeline` keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="7c7fc-151">Aby uzyskać więcej informacji o korzystaniu z filtrów wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7c7fc-151">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="7c7fc-152">Wstaw — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-152">Insert Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-153">Implementowanie tego parametru, jeśli parametr jest określony, polecenie cmdlet wstawia element.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-153">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-154">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-154">Interactive Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-155">Implementowanie tego parametru, polecenie cmdlet działa interaktywnie z użytkownikiem, gdy parametr jest określony.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-155">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-156">Typ danych interwału: Tablica skrótów</span><span class="sxs-lookup"><span data-stu-id="7c7fc-156">Interval Data type: HashTable</span></span>

<span data-ttu-id="7c7fc-157">Implementowanie tego parametru, użytkownik może określić tabeli mieszania słów kluczowych, która zawiera wartości.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-157">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="7c7fc-158">W poniższym przykładzie przedstawiono przykładowe wartości dla `Interval` parametru: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-158">The following example shows sample values for the `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>

<span data-ttu-id="7c7fc-159">Typ danych dziennika: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-159">Log Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-160">Implementuje inspekcji tego parametru działania polecenia cmdlet, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-160">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-161">Typ danych NoClobber: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-161">NoClobber Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-162">Implementowanie tego parametru, zasób nie zostaną zastąpione, jeśli określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-162">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-163">Ten parametr dotyczy poleceń cmdlet, które tworzyć nowych obiektów, dzięki czemu można zapobiec zastępowaniu istniejących obiektów o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-163">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>

<span data-ttu-id="7c7fc-164">Powiadom — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-164">Notify Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-165">Implementowanie tego parametru, użytkownik zostanie powiadomiony, że działanie została zakończona, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-165">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-166">Typ danych NotifyAddress: Adres e-mail</span><span class="sxs-lookup"><span data-stu-id="7c7fc-166">NotifyAddress Data type: E-mail address</span></span>

<span data-ttu-id="7c7fc-167">Implementowanie tego parametru, aby użytkownik może określić adres e-mail do wysłania powiadomienia po `Notify` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-167">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the `Notify` parameter is specified.</span></span>

<span data-ttu-id="7c7fc-168">Zastąpienie — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-168">Overwrite Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-169">Implementowanie tego parametru, polecenie cmdlet zastępuje wszelkie istniejące dane, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-169">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-170">Monituj — typ danych: Ciąg</span><span class="sxs-lookup"><span data-stu-id="7c7fc-170">Prompt Data type: String</span></span>

<span data-ttu-id="7c7fc-171">Implementowanie tego parametru, użytkownik może określić w wierszu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-171">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>

<span data-ttu-id="7c7fc-172">Quiet — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-172">Quiet Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-173">Implementowanie tego parametru polecenia cmdlet pomija opinie użytkowników podczas jej działania, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-173">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-174">Recurse — typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-174">Recurse Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-175">Implementowanie tego parametru rekursywnie polecenia cmdlet wykonuje swoje działania dotyczące zasobów, gdy parametr jest określony.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-175">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-176">Dane naprawa, wpisz: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-176">Repair Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-177">Implementowanie tego parametru, polecenie cmdlet podejmie próbę Popraw coś w stanie uszkodzenia, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-177">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-178">Typ danych RepairString: Ciąg</span><span class="sxs-lookup"><span data-stu-id="7c7fc-178">RepairString Data type: String</span></span>

<span data-ttu-id="7c7fc-179">Implementowanie tego parametru, aby użytkownik może określić ciąg do użycia podczas `Repair` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-179">Implement this parameter so that the user can specify a string to use when the `Repair` parameter is specified.</span></span>

<span data-ttu-id="7c7fc-180">Ponów próbę — typ danych: Int32</span><span class="sxs-lookup"><span data-stu-id="7c7fc-180">Retry Data type: Int32</span></span>

<span data-ttu-id="7c7fc-181">Implementuje ten parametr, dzięki czemu użytkownik może określić, ile razy polecenie cmdlet podejmie akcję.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-181">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>

<span data-ttu-id="7c7fc-182">Wybierz typ danych: Array — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="7c7fc-182">Select Data type: Keyword array</span></span>

<span data-ttu-id="7c7fc-183">Implementowanie tego parametru, użytkownik może określić tablicę typów elementów.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-183">Implement this parameter so that the user can specify an array of the types of items.</span></span>

<span data-ttu-id="7c7fc-184">Typ danych Stream: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-184">Stream Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-185">Implementuje ten parametr, dzięki czemu użytkownik może strumienia wielu obiektów danych wyjściowych przez potok, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-185">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-186">Typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-186">Strict Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-187">Implementowanie tego parametru, aby wszystkie błędy są obsługiwane jako błędy Trwa przerywanie działania, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-187">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-188">Typ danych TempLocation: Ciąg</span><span class="sxs-lookup"><span data-stu-id="7c7fc-188">TempLocation Data type: String</span></span>

<span data-ttu-id="7c7fc-189">Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić lokalizację danych tymczasowych, który jest używany podczas działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-189">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>

<span data-ttu-id="7c7fc-190">Typ danych limit czasu: Int32</span><span class="sxs-lookup"><span data-stu-id="7c7fc-190">Timeout Data type: Int32</span></span>

<span data-ttu-id="7c7fc-191">Implementowanie tego parametru, użytkownik może określić interwał limitu czasu (w milisekundach).</span><span class="sxs-lookup"><span data-stu-id="7c7fc-191">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>

<span data-ttu-id="7c7fc-192">Obciąć typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-192">Truncate Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-193">Implementowanie tego parametru polecenia cmdlet obetnie swoje działania, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-193">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="7c7fc-194">Jeśli parametr nie jest określony, polecenie cmdlet wykonuje kolejną akcję.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-194">If the parameter is not specified, the cmdlet performs another action.</span></span>

<span data-ttu-id="7c7fc-195">Sprawdź typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-195">Verify Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-196">Implementowanie tego parametru polecenia cmdlet zostanie test, aby ustalić, czy działanie miało miejsce, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-196">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-197">Poczekaj na typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="7c7fc-197">Wait Data type: SwitchParameter</span></span>

<span data-ttu-id="7c7fc-198">Implementowanie tego parametru, polecenie cmdlet będzie czekać na dane wejściowe użytkownika przed kontynuowaniem, gdy określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-198">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>

<span data-ttu-id="7c7fc-199">Typ danych; czas oczekiwania: Int32</span><span class="sxs-lookup"><span data-stu-id="7c7fc-199">WaitTime Data type: Int32</span></span>

<span data-ttu-id="7c7fc-200">Implementowanie tego parametru, aby użytkownik może określić czas trwania (w sekundach), polecenia cmdlet będzie czekać użytkownika danych wejściowych podczas `Wait` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-200">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the `Wait` parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c7fc-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c7fc-201">See Also</span></span>

[<span data-ttu-id="7c7fc-202">Parametry polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7c7fc-202">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="7c7fc-203">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c7fc-203">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="7c7fc-204">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c7fc-204">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
