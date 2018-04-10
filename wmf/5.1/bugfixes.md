---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Poprawki błędów w WMF 5.1
ms.openlocfilehash: dfd9ead447edfe9b7bdae23be14785df4b182bbc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="da4bc-103">Poprawki błędów w WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="da4bc-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="da4bc-104">Poprawki błędów</span><span class="sxs-lookup"><span data-stu-id="da4bc-104">Bug fixes</span></span> ##

<span data-ttu-id="da4bc-105">Następujące godne usterki usunięto w wersji WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="da4bc-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="da4bc-106">Autowykrywanie modułu pełni honoruje `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="da4bc-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="da4bc-107">Moduł Autowykrywanie (ładowania modułów automatycznie bez jawnego Import-Module podczas wywoływania polecenia) została wprowadzona w WMF 3.</span><span class="sxs-lookup"><span data-stu-id="da4bc-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="da4bc-108">Jeśli wprowadzone, programu PowerShell sprawdzenie poleceń w `$PSHome\Modules` przed użyciem `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="da4bc-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="da4bc-109">To zachowanie, aby uwzględnić zmiany WMF 5.1 `$env:PSModulePath` całkowicie.</span><span class="sxs-lookup"><span data-stu-id="da4bc-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="da4bc-110">Dzięki temu moduł utworzonymi przez użytkownika, który definiuje poleceń programu PowerShell (np. `Get-ChildItem`) mają być automatycznie załadowane i poprawnie zastępowaniem wbudowanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="da4bc-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="da4bc-111">Przekierowywanie plików nie dłużej stałe umieszczana w kodzie `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="da4bc-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="da4bc-112">We wszystkich wcześniejszych wersjach programu PowerShell, nie było możliwe do kontrolowania kodowanie pliku używana przez operator przekierowania pliku, np. `Get-ChildItem > out.txt` ponieważ PowerShell dodane `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="da4bc-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="da4bc-113">Począwszy od wersji 5.1 WMF, można teraz zmienić kodowanie pliku przekierowania przez ustawienie `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="da4bc-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="da4bc-114">Stałe regresji podczas uzyskiwania dostępu do elementów członkowskich `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="da4bc-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="da4bc-115">Regresja wprowadzone w programie WMF 5.0 spowodowało przerwanie podczas uzyskiwania dostępu do elementów członkowskich `System.Reflection.RuntimeType`, np. `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="da4bc-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="da4bc-116">Ten problem został rozwiązany w wersji 5.1 WMF.</span><span class="sxs-lookup"><span data-stu-id="da4bc-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="da4bc-117">Stałe problemy z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="da4bc-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="da4bc-118">WMF 5.0 wprowadzono nowe integratora modelu COM dla wywoływanie metod obiektów COM i uzyskiwaniem dostępu do właściwości obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="da4bc-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="da4bc-119">Ten nowy obiekt tworzący powiązanie znacznie wyższą wydajność, ale również wprowadzić pewne usterki, które zostały ustalone w wersji 5.1 WMF.</span><span class="sxs-lookup"><span data-stu-id="da4bc-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="da4bc-120">Konwersje argumentów nie zawsze wykonano poprawnie</span><span class="sxs-lookup"><span data-stu-id="da4bc-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="da4bc-121">W poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="da4bc-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="da4bc-122">Metoda SendKeys spodziewa się ciągu, ale programu PowerShell nie zostały przekonwertowane char na ciąg odkładanie konwersja IDispatch::Invoke, używający VariantChangeType można wykonać konwersji, co w tym przykładzie spowodowało zamiast wysyłania kluczy "1", "7" i "3" Oczekiwano klucza Volume.Mute.</span><span class="sxs-lookup"><span data-stu-id="da4bc-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="da4bc-123">Wyliczalny obiektów COM nie zawsze obsługiwana poprawnie</span><span class="sxs-lookup"><span data-stu-id="da4bc-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="da4bc-124">PowerShell wylicza zazwyczaj większość obiektów wyliczalny, ale regresji wprowadzone w programie WMF 5.0 uniemożliwił wyliczanie obiektów COM, które implementuje interfejs IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="da4bc-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="da4bc-125">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da4bc-125">For example:</span></span>

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="da4bc-126">W powyższym przykładzie WMF 5.0 nieprawidłowo napisane Scripting.Dictionary do potoku zamiast wyliczania pary klucz wartość.</span><span class="sxs-lookup"><span data-stu-id="da4bc-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="da4bc-127">Zmiana adresów [wystawiać 1752224 w Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="da4bc-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="da4bc-128">`[ordered]` niedozwolone wewnątrz klasy</span><span class="sxs-lookup"><span data-stu-id="da4bc-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="da4bc-129">WMF 5.0 wprowadzono klasy z weryfikacją literałów typu używany w klasach.</span><span class="sxs-lookup"><span data-stu-id="da4bc-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="da4bc-130">`[ordered]` wygląda jak literału typu, ale nie jest typem .NET wartość true.</span><span class="sxs-lookup"><span data-stu-id="da4bc-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="da4bc-131">WMF 5.0 niepoprawnie zgłosił błąd na `[ordered]` wewnątrz klasy:</span><span class="sxs-lookup"><span data-stu-id="da4bc-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="da4bc-132">Pomoc na temat tematy z wieloma wersjami nie działa.</span><span class="sxs-lookup"><span data-stu-id="da4bc-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="da4bc-133">Przed WMF 5.1, jeśli ma wiele wersji modułów zainstalowanych i wszystkie udostępnione tematu pomocy, na przykład about_PSReadline, `help about_PSReadline` zwróci wiele tematów można w sposób jednoznaczny Wyświetl Pomoc prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="da4bc-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="da4bc-134">WMF 5.1 rozwiązuje to zwracając pomocy dla najnowszej wersji tego tematu.</span><span class="sxs-lookup"><span data-stu-id="da4bc-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="da4bc-135">`Get-Help` nie zapewnia możliwość określenia, która wersja ma dotyczyć pomoc dla.</span><span class="sxs-lookup"><span data-stu-id="da4bc-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="da4bc-136">Aby obejść ten problem, przejdź do katalogu, moduły i wyświetlić Pomoc bezpośrednio z narzędzia, takiego jak edytor ulubionych.</span><span class="sxs-lookup"><span data-stu-id="da4bc-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="da4bc-137">Odczytywanie z STDIN PowerShell.exe przestał działać</span><span class="sxs-lookup"><span data-stu-id="da4bc-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="da4bc-138">Użyj klientów `powershell -command -` z natywne aplikacje do wykonania programu PowerShell przekazywanie w skrypcie za pośrednictwem STDIN Niestety to został uszkodzony z powodu inne zmiany jej host konsoli.</span><span class="sxs-lookup"><span data-stu-id="da4bc-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="da4bc-139">PowerShell.exe tworzy kolekcji wykorzystania Procesora przy uruchamianiu</span><span class="sxs-lookup"><span data-stu-id="da4bc-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="da4bc-140">Sprawdź, czy została uruchomiona przy użyciu zasad grupy, aby uniknąć opóźnienia podczas logowania PowerShell korzysta z kwerendy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="da4bc-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="da4bc-141">Kwerenda WMI kończy się wstrzykiwania tzres.mui.dll do każdego procesu w systemie, ponieważ klasa WMI Win32_Process próbuje pobrać informacje dotyczące lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="da4bc-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="da4bc-142">Powoduje to duży kolekcji procesora CPU w wmiprvse (host dostawcy WMI).</span><span class="sxs-lookup"><span data-stu-id="da4bc-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="da4bc-143">Poprawka jest Użyj interfejsu API Win32, aby pobrać te same informacje, a nie za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="da4bc-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>