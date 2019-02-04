---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Uzyskiwanie szczegółowych informacji pomocy
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 8b56f003fdef38b0f126cfe82eefcc145cc54783
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684087"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="ed97b-103">Uzyskiwanie szczegółowych informacji pomocy</span><span class="sxs-lookup"><span data-stu-id="ed97b-103">Getting detailed help information</span></span>

<span data-ttu-id="ed97b-104">Program PowerShell zawiera szczegółowe artykuły pomocy pojęcia programu PowerShell i języka programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed97b-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="ed97b-105">Dostępne są także artykuły pomocy dla każdego polecenia cmdlet i dostawcy i wiele funkcji i skryptów.</span><span class="sxs-lookup"><span data-stu-id="ed97b-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="ed97b-106">Można wyświetlić tych artykułów pomocy, w wierszu polecenia lub Wyświetl ostatnio zaktualizowane wersje tych artykułów w [PowerShell](/powershell/scripting/overview) dokumentacji online.</span><span class="sxs-lookup"><span data-stu-id="ed97b-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="ed97b-107">Uzyskiwanie pomocy dla poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="ed97b-107">Getting help for cmdlets</span></span>

<span data-ttu-id="ed97b-108">Aby uzyskać pomoc dotyczącą poleceń cmdlet programu PowerShell, należy użyć [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed97b-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="ed97b-109">Na przykład, aby uzyskać pomoc dotyczącą `Get-ChildItem` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="ed97b-110">lub</span><span class="sxs-lookup"><span data-stu-id="ed97b-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="ed97b-111">Można nawet uzyskać pomoc dotyczącą polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="ed97b-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="ed97b-112">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ed97b-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="ed97b-113">Aby uzyskać listę polecenia cmdlet artykułów pomocy, w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="ed97b-114">Aby wyświetlić jedną stronę części każdego artykułu pomocy w czasie, użyj `help` funkcji lub jego alias `man`.</span><span class="sxs-lookup"><span data-stu-id="ed97b-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="ed97b-115">Na przykład, aby wyświetlić Pomoc dla `Get-ChildItem` polecenia cmdlet, typ</span><span class="sxs-lookup"><span data-stu-id="ed97b-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="ed97b-116">lub</span><span class="sxs-lookup"><span data-stu-id="ed97b-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="ed97b-117">Aby wyświetlić szczegółowe informacje, należy użyć **szczegółowe** parametru `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed97b-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ed97b-118">Na przykład, aby uzyskać szczegółowe informacje na `Get-ChildItem` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="ed97b-119">Aby wyświetlić całą zawartość w artykule pomocy, użyj **pełne** parametru `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed97b-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ed97b-120">Na przykład, aby wyświetlić całą zawartość w artykule pomocy, aby `Get-ChildItem` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="ed97b-121">Aby uzyskać szczegółową pomoc dotyczącą parametry polecenia cmdlet, użyj **parametru** parametru `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed97b-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ed97b-122">Na przykład, aby uzyskać szczegółowe pomocy dla wszystkich parametrów `Get-ChildItem` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="ed97b-123">Aby wyświetlić tylko w przykładach w artykule pomocy, użyj **przykłady** parametru `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ed97b-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="ed97b-124">Na przykład, aby wyświetlić tylko w przykładach w artykule pomocy, aby `Get-ChildItem `polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-124">For example, to display only the examples in the Help article for the `Get-ChildItem `cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="ed97b-125">Aby uzyskać informacji na temat sposobu pisania artykułów pomocy dla poleceń cmdlet, które piszesz, zobacz [sposobu pisania pomoc dotyczącą polecenia Cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="ed97b-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="ed97b-126">Uzyskiwanie pomocy koncepcyjne</span><span class="sxs-lookup"><span data-stu-id="ed97b-126">Getting conceptual help</span></span>

<span data-ttu-id="ed97b-127">`Get-Help` Polecenie cmdlet wyświetla również informacji na temat artykułów koncepcyjnych w programie PowerShell, w tym artykuły na temat języka programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed97b-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="ed97b-128">Koncepcyjny pomocy artykuły zaczynają się od prefiksu "about_", takich jak about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="ed97b-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="ed97b-129">(Nazwa artykuł koncepcyjny należy podać w języku angielskim nawet w przypadku wersji innej niż angielska programu PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="ed97b-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="ed97b-130">Aby wyświetlić listę artykułów koncepcyjnych, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="ed97b-131">Aby wyświetlić określonego artykułu pomocy, wpisz nazwę artykułu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ed97b-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="ed97b-132">Parametry `Get-Help`, takich jak **szczegółowe**, **parametru**, i **przykłady**, nie mają wpływu na wyświetlanie artykuły koncepcyjne pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="ed97b-133">Uzyskiwanie pomocy na temat dostawców</span><span class="sxs-lookup"><span data-stu-id="ed97b-133">Getting help about providers</span></span>

<span data-ttu-id="ed97b-134">`Get-Help` Polecenie cmdlet wyświetla informacje dotyczące dostawcy programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed97b-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="ed97b-135">Aby uzyskać pomoc dotyczącą dostawcę, należy wpisać `Get-Help` następuje nazwa dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="ed97b-136">Na przykład aby uzyskać pomoc dotyczącą dostawcy rejestru, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="ed97b-137">Aby uzyskać listę wszystkich dostawca artykułów pomocy w sesji, wpisz</span><span class="sxs-lookup"><span data-stu-id="ed97b-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="ed97b-138">Parametry `Get-Help`, takich jak **szczegółowe**, **parametru**, i **przykłady**, nie mają wpływu na wyświetlanie dostawca artykułów pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="ed97b-139">Uzyskiwanie pomocy na temat skryptów i funkcji</span><span class="sxs-lookup"><span data-stu-id="ed97b-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="ed97b-140">Wiele skryptów i funkcji w programie PowerShell ma artykułów pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="ed97b-141">Użyj `Get-Help` polecenia cmdlet, aby wyświetlić artykułów pomocy, skryptach i funkcjach.</span><span class="sxs-lookup"><span data-stu-id="ed97b-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="ed97b-142">Aby wyświetlić Pomoc dla funkcji, wpisz `Get-Help` przed nazwą funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed97b-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="ed97b-143">Na przykład, aby uzyskać pomoc dotyczącą `Disable-PSRemoting` funkcji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="ed97b-144">Aby wyświetlić Pomoc, aby uzyskać skrypt, wpisz ścieżkę do pliku skryptu.</span><span class="sxs-lookup"><span data-stu-id="ed97b-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="ed97b-145">Jeśli skrypt nie jest w ścieżce wymienione w zmiennej środowiskowej Path, musisz podać pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ed97b-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="ed97b-146">Na przykład, jeśli masz skrypt o nazwie "TestScript.ps1" c:\\katalogu PS testów do wyświetlenia artykułu pomocy, aby skrypt, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="ed97b-147">Parametry, które są przeznaczone do wyświetlania pracy pomocy polecenia cmdlet dla skryptów i funkcję Pomoc zbyt.</span><span class="sxs-lookup"><span data-stu-id="ed97b-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="ed97b-148">Jednak Pomoc dla funkcji i skryptów nie jest wyświetlany po uruchomieniu `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="ed97b-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="ed97b-149">Informacje na temat pisania artykułów pomocy dla funkcji i skryptów zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="ed97b-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="ed97b-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ed97b-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ed97b-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ed97b-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ed97b-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ed97b-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="ed97b-153">Uzyskiwanie pomocy online</span><span class="sxs-lookup"><span data-stu-id="ed97b-153">Getting help online</span></span>

<span data-ttu-id="ed97b-154">Przeglądanie artykułów pomocy online jest jednym z najlepszych sposobów uzyskania pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="ed97b-155">Artykuły w trybie online są łatwiejsze do aktualizacji i zapewnia najbardziej aktualną zawartość.</span><span class="sxs-lookup"><span data-stu-id="ed97b-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="ed97b-156">Aby uzyskać pomoc w trybie online, należy użyć **Online** parametru `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed97b-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ed97b-157">Wszystkich artykułów pomocy, które przy użyciu programu PowerShell, włącznie z dostawcą pomocy i pojęciach (artykułów pomocy informacje) są dostępne w trybie online w [PowerShell](/powershell/scripting/powershell-scripting) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ed97b-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="ed97b-158">Nie można użyć **Online** parametrem koncepcyjnej (about_\*) lub dostawca artykułów pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="ed97b-159">Pomoc online jest opcjonalne, więc nie działa dla każdego polecenia cmdlet, funkcji lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="ed97b-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="ed97b-160">Na przykład, aby uzyskać wersję online artykułu pomocy na temat `Get-ChildItem` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="ed97b-161">Program PowerShell spowoduje otwarcie tego artykułu w domyślnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="ed97b-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="ed97b-162">Pomoc online jest przeznaczony do artykułu pomocy, można również wyświetlić adres URL artykułu pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="ed97b-163">Adres URL pojawia się w sekcji linki powiązane artykułu pomocy.</span><span class="sxs-lookup"><span data-stu-id="ed97b-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="ed97b-164">Na przykład aby zobaczyć adres URL dla wersji online polecenia cmdlet Add-Computer, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ed97b-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="ed97b-165">Poniżej przedstawiono pierwszy wiersz w sekcji linki powiązane tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="ed97b-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="ed97b-166">Aby uzyskać informacje o tym, jak zapewnienie wsparcia online dla artykułów pomocy, zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="ed97b-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed97b-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed97b-167">See also</span></span>

- [<span data-ttu-id="ed97b-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ed97b-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ed97b-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ed97b-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ed97b-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ed97b-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="ed97b-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ed97b-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
