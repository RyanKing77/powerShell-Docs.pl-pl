---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Trwa pobieranie informacji o szczegółową pomoc"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="c0cc3-103">Trwa pobieranie informacji o szczegółową pomoc</span><span class="sxs-lookup"><span data-stu-id="c0cc3-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="c0cc3-104">Program Windows PowerShell zawiera szczegółowe tematy pomocy, które opisano pojęcia dotyczące środowiska Windows PowerShell i język środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="c0cc3-105">Istnieją także tematy pomocy dla każdego polecenia cmdlet i dostawcy i tematy pomocy dla wielu funkcji i skryptów.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="c0cc3-106">Możesz wyświetlić te tematy pomocy w wierszu polecenia lub wyświetlić najnowsze wersje tych tematów w Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="c0cc3-107">Wiele programów obsługujące środowisko Windows PowerShell, takie jak Windows PowerShell zintegrowane skryptów środowisko, oferują dodatkowe funkcje pomocy, takich jak Pomoc kontekstowa i skompilowany plik pomocy (.chm).</span><span class="sxs-lookup"><span data-stu-id="c0cc3-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="c0cc3-108">Uzyskiwanie pomocy dotyczącej poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0cc3-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="c0cc3-109">Aby uzyskać pomoc dotyczącą poleceń cmdlet programu Windows PowerShell, użyj [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="c0cc3-110">Na przykład, aby uzyskać pomoc dotyczącą [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="c0cc3-111">lub</span><span class="sxs-lookup"><span data-stu-id="c0cc3-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="c0cc3-112">Można nawet uzyskać pomoc dotyczącą polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="c0cc3-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="c0cc3-114">Aby uzyskać listę wszystkich tematów pomocy polecenia cmdlet w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="c0cc3-115">Aby wyświetlić jedną stronę każdego tematu pomocy w czasie, należy użyć **pomocy** funkcji lub aliasem **man**.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="c0cc3-116">Na przykład aby wyświetlić Pomoc dla polecenia cmdlet Get-ChildItem, wpisz</span><span class="sxs-lookup"><span data-stu-id="c0cc3-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="c0cc3-117">lub</span><span class="sxs-lookup"><span data-stu-id="c0cc3-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="c0cc3-118">Aby wyświetlić szczegółowe informacje na temat polecenia cmdlet, funkcji lub skryptu, między innymi opisy parametrów i przykłady ich użycia, należy użyć *szczegółowy* parametru polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c0cc3-119">Na przykład aby uzyskać szczegółowe informacje na temat polecenia cmdlet Get-ChildItem, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="c0cc3-120">Aby wyświetlić całą zawartość w temacie pomocy, użyj *pełne* parametru polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c0cc3-121">Na przykład aby wyświetlić całą zawartość w temacie pomocy dla polecenia cmdlet Get-ChildItem, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="c0cc3-122">Aby uzyskać szczegółową pomoc dotyczącą parametry polecenia cmdlet, użyj *parametru* parametru polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c0cc3-123">Na przykład aby uzyskać szczegółowe pomocy dla wszystkich parametrów polecenia cmdlet Get-ChildItem, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="c0cc3-124">Aby wyświetlić tylko w przykładach w temacie pomocy, użyj *przykład* parametr Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="c0cc3-125">Na przykład aby wyświetlić tylko w przykładach w temacie pomocy dla polecenia cmdlet Get-ChildItem, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="c0cc3-126">Aby uzyskać informacje dotyczące pisania tematy pomocy dla poleceń cmdlet, który można zapisać, zobacz [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="c0cc3-127">Uzyskiwanie pomocy koncepcyjne</span><span class="sxs-lookup"><span data-stu-id="c0cc3-127">Getting Conceptual Help</span></span>
<span data-ttu-id="c0cc3-128">Polecenie cmdlet Get-Help Wyświetla również informacje o tematy dotyczące pojęć w programie Windows PowerShell, w tym tematy dotyczące języków środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="c0cc3-129">Tematy dotyczące pojęć pomocy zaczynać się prefiksem "about_", na przykład about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="c0cc3-130">(Nazwa bieżącego tematu należy podać w języku angielskim nawet w przypadku innych niż angielska wersji środowiska Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="c0cc3-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="c0cc3-131">Aby wyświetlić listę pojęć, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="c0cc3-132">Aby wyświetlić określonego tematu pomocy, wpisz nazwę tematu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="c0cc3-133">Parametr Get-Help, takich jak *szczegółowy*, *parametru*, i *przykłady*, nie mają wpływu na wyświetlanie koncepcyjne tematy Pomocy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="c0cc3-134">Uzyskiwanie pomocy dotyczące dostawców</span><span class="sxs-lookup"><span data-stu-id="c0cc3-134">Getting Help About Providers</span></span>
<span data-ttu-id="c0cc3-135">Polecenie cmdlet Get-Help Wyświetla informacje dotyczące dostawcy programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="c0cc3-136">Aby uzyskać pomoc dla dostawcy, wpisz "Get-Help", a po niej nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="c0cc3-137">Na przykład aby uzyskać pomoc dotyczącą dostawcy rejestru, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="c0cc3-138">Aby uzyskać listę wszystkich tematów pomocy dostawcy w sesji, wpisz</span><span class="sxs-lookup"><span data-stu-id="c0cc3-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="c0cc3-139">Parametr Get-Help, takich jak *szczegółowy*, *parametru*, i *przykłady*, nie mają wpływu na wyświetlanie tematy pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="c0cc3-140">Uzyskiwanie pomocy o skryptach i funkcjach</span><span class="sxs-lookup"><span data-stu-id="c0cc3-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="c0cc3-141">Wiele skryptów i funkcji w programie Windows PowerShell są dostępne tematy Pomocy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="c0cc3-142">Aby wyświetlić tematy pomocy dla skryptów i funkcji, należy użyć polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="c0cc3-143">Aby wyświetlić Pomoc dla funkcji, wpisz "get-help", a po niej nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="c0cc3-144">Na przykład aby uzyskać pomoc dotyczącą funkcja Disable-PSRemoting, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="c0cc3-145">Aby wyświetlić Pomoc, aby uzyskać skrypt, wpisz w pełni kwalifikowana ścieżka do pliku skryptu.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="c0cc3-146">Jeśli skrypt jest w ścieżce, która znajduje się w zmiennej środowiskowej Path, ścieżka polecenia można pominąć.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="c0cc3-147">Na przykład, jeśli masz skryptu o nazwie "TestScript.ps1" w Twojej C:\\katalogu PS testu, można wyświetlić tematu Pomocy dotyczącego skrypt, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="c0cc3-148">Pomoc parametrów, które zostały zaprojektowane do wyświetlania polecenia cmdlet, takich jak *szczegółowy*, *pełne*, *przykłady*, i *parametru*, nadają się do skrypt pomocy i funkcja Pomoc zbyt.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="c0cc3-149">Jednak po wyświetleniu wszystkich pomocy, wpisując "get-help \*" Pomoc dla funkcji i skryptów nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="c0cc3-150">Informacje na temat pisania tematy pomocy dla funkcji i skryptów, zobacz [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), i [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="c0cc3-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="c0cc3-151">Uzyskiwanie pomocy Online</span><span class="sxs-lookup"><span data-stu-id="c0cc3-151">Getting Help Online</span></span>
<span data-ttu-id="c0cc3-152">Po nawiązaniu połączenia z Internetem, jednym z najlepszych sposobów uzyskania pomocy jest aby wyświetlić tematy Pomocy online.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="c0cc3-153">Ponieważ tematy online są łatwe do aktualizacji, są one może zapewnić aktualna zawartość.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="c0cc3-154">Aby uzyskać pomoc w trybie online, spróbuj *Online* parametru polecenia cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c0cc3-155">*Online* parametru działania polecenia cmdlet Get-Help tylko dla polecenia cmdlet pomocy, pomocy funkcji i skryptów pomocy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="c0cc3-156">Nie można użyć *Online* parametr o pojęciach (informacje) tematy, albo tematy pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="c0cc3-157">Ponadto ponieważ ta funkcja jest opcjonalny, go nie działa w przypadku każdego polecenia cmdlet, funkcji lub tematu Pomocy skryptu.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="c0cc3-158">Jednak wszystkie tematy pomocy pochodzące z programu Windows PowerShell, w tym dostawcy pomocy i koncepcyjne (tematy Pomocy informacje) są dostępne w trybie online w [programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) sekcji Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="c0cc3-159">Aby użyć *Online* parametru polecenia cmdlet Get-Help, użyj następującego formatu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="c0cc3-160">Na przykład aby uzyskać wersji online tematu Pomocy dotyczących polecenia cmdlet Get-ChildItem, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="c0cc3-161">Jeśli wersji online tematu Pomocy jest dostępny, zostanie otwarty w domyślnej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="c0cc3-162">Pomoc online jest obsługiwana dla tematu pomocy, można również wyświetlić adres internetowy (URL) tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="c0cc3-163">Adres internetowy pojawia się w sekcji łączy pokrewnych tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="c0cc3-164">Na przykład aby wyświetlić adres URL dla wersji online polecenia cmdlet Add-Computer, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c0cc3-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="c0cc3-165">Pierwszy wiersz w sekcji łączy pokrewnych tego tematu przedstawiono poniżej.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="c0cc3-166">Aby uzyskać informacje dotyczące zapewnienie pomocy technicznej online tematy pomocy, zobacz [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)i zobacz [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="c0cc3-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0cc3-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0cc3-167">See Also</span></span>
- <span data-ttu-id="c0cc3-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="c0cc3-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="c0cc3-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="c0cc3-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="c0cc3-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="c0cc3-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="c0cc3-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="c0cc3-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>

