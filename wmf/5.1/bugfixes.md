---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Poprawki błędów w programie WMF 5.1
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085052"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="6a8a8-103">Poprawki błędów w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="6a8a8-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="6a8a8-104">Poprawki błędów</span><span class="sxs-lookup"><span data-stu-id="6a8a8-104">Bug fixes</span></span>

<span data-ttu-id="6a8a8-105">Następujące istotne błędy zostały usunięte w program WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="6a8a8-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="6a8a8-106">W pełni honoruje Autowykrywanie modułu `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="6a8a8-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span>

<span data-ttu-id="6a8a8-107">Funkcja autowykrywania modułu (ładowanie modułów automatycznie bez jawnego Import-Module podczas wywoływania polecenia) została wprowadzona w 3 programu WMF.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="6a8a8-108">Kiedy wprowadzony, program PowerShell sprawdzane pod kątem poleceń w `$PSHome\Modules` przed użyciem `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="6a8a8-109">Program WMF 5.1 zmienia to zachowanie, aby uwzględnić `$env:PSModulePath` całkowicie.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="6a8a8-110">Dzięki temu dla modułu utworzonych przez użytkownika, który definiuje poleceń programu PowerShell (np. `Get-ChildItem`) mają być automatycznie załadowane i poprawnie zastępowaniem wbudowanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="6a8a8-111">Przekierowywanie plików nie dłużej twardych kodów `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="6a8a8-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span>

<span data-ttu-id="6a8a8-112">We wszystkich poprzednich wersjach programu PowerShell, było niemożliwe do kontrolowania kodowanie pliku używany przez operatora przekierowania pliku, np. `Get-ChildItem > out.txt` PowerShell dodane `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="6a8a8-113">Począwszy od programu WMF 5.1 można teraz zmienić kodowanie pliku przekierowania, ustawiając `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="6a8a8-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="6a8a8-114">Naprawiono regresję podczas uzyskiwania dostępu do elementów członkowskich `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="6a8a8-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span>

<span data-ttu-id="6a8a8-115">Regresja wprowadzone w programie WMF 5.0 Przerwano uzyskiwania dostępu do elementów członkowskich `System.Reflection.RuntimeType`, np. `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="6a8a8-116">Ten błąd został naprawiony w WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="6a8a8-117">Rozwiązano niektóre problemy z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="6a8a8-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="6a8a8-118">Program WMF 5.0 wprowadzono nowe integratora modelu COM dla wywołania metod obiektów COM i uzyskiwania dostępu do właściwości obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="6a8a8-119">Ten nowy obiekt wiążący znacznie zwiększona wydajność, ale również wprowadzone pewne błędy, które usunięto w programie WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="6a8a8-120">Konwersje argumentów nie zawsze wykonano poprawnie</span><span class="sxs-lookup"><span data-stu-id="6a8a8-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="6a8a8-121">W poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6a8a8-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="6a8a8-122">Metoda WyślijKlawisze oczekuje ciągu, ale program PowerShell nie zostały przekonwertowane char na ciąg odkładania konwersji uwzględniając, który używa VariantChangeType do wykonywania konwersji, co w tym przykładzie spowodowało zamiast wysyłania kluczy '1', '7' i '3' Oczekiwano klucza Volume.Mute.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="6a8a8-123">Wyliczalne obiektów COM nie zawsze obsługiwane poprawnie</span><span class="sxs-lookup"><span data-stu-id="6a8a8-123">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="6a8a8-124">PowerShell zwykle wylicza większość obiektów wyliczalny, ale regresji, wprowadzone w programie WMF 5.0 uniemożliwił wyliczenie obiektów COM, które implementują interfejs IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="6a8a8-125">Przykład:</span><span class="sxs-lookup"><span data-stu-id="6a8a8-125">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="6a8a8-126">W powyższym przykładzie WMF 5.0 niepoprawnie napisany Scripting.Dictionary do potoku zamiast wyliczania pary klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="6a8a8-127">Zmiany adresów [wystawiać 1752224 w witrynie Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="6a8a8-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="6a8a8-128">`[ordered]` był niedozwolony wewnątrz klasy</span><span class="sxs-lookup"><span data-stu-id="6a8a8-128">`[ordered]` was not allowed inside classes</span></span>

<span data-ttu-id="6a8a8-129">Program WMF 5.0 wprowadzono klasy z weryfikacją literałów typu, używany w klasach.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="6a8a8-130">`[ordered]` wygląda jak literał typu, ale nie jest to wartość true, typ platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="6a8a8-131">Program WMF 5.0 niepoprawnie zgłosił błąd na `[ordered]` wewnątrz klasy:</span><span class="sxs-lookup"><span data-stu-id="6a8a8-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="6a8a8-132">Pomoc na temat tematów z wieloma wersjami nie działa.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="6a8a8-133">Zanim program WMF 5.1, jeśli masz wiele wersji zainstalować moduł, a wszystkie one udostępnione tematu pomocy, na przykład about_PSReadline, `help about_PSReadline` zwróci wiele tematów w oczywisty sposób wyświetlenia rzeczywiste pomocy.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="6a8a8-134">Program WMF 5.1 rozwiązuje to zwracając pomocy dla najnowszej wersji tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="6a8a8-135">`Get-Help` nie zapewnia możliwość określenia, która wersja ma dotyczyć pomoc dla.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="6a8a8-136">Aby obejść ten problem, przejdź do katalogu modułów, a następnie Wyświetl Pomoc bezpośrednio za pomocą narzędzia, takiego jak ulubionego edytora.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="6a8a8-137">Odczytywanie z STDIN PowerShell.exe przerywane.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="6a8a8-138">Klienci używają `powershell -command -` od natywnych aplikacji do wykonywania programu PowerShell przekazywanie w skrypcie za pośrednictwem STDIN Niestety to zostało przerwane ze względu na inne zmiany w jej hosta konsoli.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="6a8a8-139">PowerShell.exe tworzy nagły wzrost użycia procesora CPU podczas uruchamiania</span><span class="sxs-lookup"><span data-stu-id="6a8a8-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="6a8a8-140">PowerShell używa kwerendy usługi WMI, aby sprawdzić, czy została uruchomiona przy użyciu zasad grupy, aby uniknąć, powodując opóźnienie podczas logowania.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="6a8a8-141">Kwerenda WMI kończy się wprowadzanie tzres.mui.dll na każdym etapie procesu w systemie, ponieważ klasy WMI Win32_Process podejmie próbę pobrania informacje dotyczące lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="6a8a8-142">Skutkuje to duży wzrost użycia Procesora wmiprvse (host dostawcy WMI).</span><span class="sxs-lookup"><span data-stu-id="6a8a8-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="6a8a8-143">Obejście polega na użyciu wywołań interfejsu API Win32 te same informacje, a nie przy użyciu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="6a8a8-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
