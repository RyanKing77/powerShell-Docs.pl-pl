---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Poprawki błędów w programie WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856210"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="71b9e-103">Poprawki błędów w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="71b9e-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="71b9e-104">Poprawki błędów</span><span class="sxs-lookup"><span data-stu-id="71b9e-104">Bug fixes</span></span>

<span data-ttu-id="71b9e-105">Następujące istotne błędy zostały usunięte w program WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="71b9e-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="71b9e-106">Autowykrywanie modułu pełni honoruje PSModulePath</span><span class="sxs-lookup"><span data-stu-id="71b9e-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="71b9e-107">Funkcja autowykrywania modułu (ładowanie modułów automatycznie bez jawnego Import-Module podczas wywoływania polecenia) została wprowadzona w 3 programu WMF.</span><span class="sxs-lookup"><span data-stu-id="71b9e-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="71b9e-108">Kiedy wprowadzony, program PowerShell sprawdzane pod kątem poleceń w `$PSHome\Modules` przed użyciem `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="71b9e-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="71b9e-109">Program WMF 5.1 zmienia to zachowanie, aby uwzględnić `$env:PSModulePath` całkowicie.</span><span class="sxs-lookup"><span data-stu-id="71b9e-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="71b9e-110">Dzięki temu dla modułu utworzonych przez użytkownika, który definiuje poleceń programu PowerShell (np. `Get-ChildItem`) mają być automatycznie załadowane i poprawnie zastępowaniem wbudowanego polecenia.</span><span class="sxs-lookup"><span data-stu-id="71b9e-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="71b9e-111">Przekierowywanie plików nie dłużej twardych kodów — kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="71b9e-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="71b9e-112">We wszystkich poprzednich wersjach programu PowerShell było niemożliwe do kontrolowania kodowanie pliku używane przez plik operatora przekierowania.</span><span class="sxs-lookup"><span data-stu-id="71b9e-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="71b9e-113">Począwszy od programu WMF 5.1 można teraz zmienić kodowanie pliku przekierowania, ustawiając `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="71b9e-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="71b9e-114">Naprawiono regresję podczas uzyskiwania dostępu do elementów członkowskich System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="71b9e-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="71b9e-115">Regresja wprowadzone w programie WMF 5.0 Przerwano uzyskiwania dostępu do elementów członkowskich `System.Reflection.RuntimeType`, na przykład `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="71b9e-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="71b9e-116">Ten błąd został naprawiony w WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="71b9e-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="71b9e-117">Rozwiązano niektóre problemy z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="71b9e-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="71b9e-118">Program WMF 5.0 wprowadzono nowe integratora modelu COM dla wywołania metod obiektów COM i uzyskiwania dostępu do właściwości obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="71b9e-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="71b9e-119">Ten nowy obiekt wiążący znacznie zwiększona wydajność, ale również wprowadzone pewne błędy, które usunięto w programie WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="71b9e-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="71b9e-120">Konwersje argumentów nie zawsze wykonano poprawnie</span><span class="sxs-lookup"><span data-stu-id="71b9e-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="71b9e-121">W poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="71b9e-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="71b9e-122">**WyślijKlawisze** metoda oczekuje ciągu, ale program PowerShell nie zostały przekonwertowane char na ciąg odkładania konwersji na **uwzględniając**, który używa **VariantChangeType**można wykonać konwersji.</span><span class="sxs-lookup"><span data-stu-id="71b9e-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="71b9e-123">W tym przykładzie pozwoliło to odnotować przesyłanie kluczy '1', '7' i "3" zamiast oczekiwanej **Volume.Mute** klucza.</span><span class="sxs-lookup"><span data-stu-id="71b9e-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="71b9e-124">Wyliczalne obiektów COM nie zawsze obsługiwane poprawnie</span><span class="sxs-lookup"><span data-stu-id="71b9e-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="71b9e-125">PowerShell zwykle wylicza większość obiektów wyliczalny, ale regresji, wprowadzone w programie WMF 5.0 uniemożliwił wyliczenie obiektów COM, które implementują interfejs IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="71b9e-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="71b9e-126">Przykład:</span><span class="sxs-lookup"><span data-stu-id="71b9e-126">For example:</span></span>

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

<span data-ttu-id="71b9e-127">W powyższym przykładzie nieprawidłowo napisany program WMF 5.0 **Scripting.Dictionary** do potoku zamiast wyliczania pary klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="71b9e-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="71b9e-128">[uporządkowane] był niedozwolony wewnątrz klasy</span><span class="sxs-lookup"><span data-stu-id="71b9e-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="71b9e-129">Program WMF 5.0 wprowadzono klasy z weryfikacją literałów typu, używany w klasach.</span><span class="sxs-lookup"><span data-stu-id="71b9e-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="71b9e-130">`[ordered]` wygląda jak literał typu, ale nie jest to wartość true, typ platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="71b9e-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="71b9e-131">Program WMF 5.0 niepoprawnie zgłosił błąd na `[ordered]` wewnątrz klasy:</span><span class="sxs-lookup"><span data-stu-id="71b9e-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="71b9e-132">Pomoc na temat tematów z wieloma wersjami nie działa.</span><span class="sxs-lookup"><span data-stu-id="71b9e-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="71b9e-133">Zanim program WMF 5.1, jeśli masz wiele wersji zainstalować moduł, a wszystkie one udostępnione tematu pomocy, na przykład about_PSReadline, `help about_PSReadline` zwróci wiele tematów w oczywisty sposób wyświetlenia rzeczywiste pomocy.</span><span class="sxs-lookup"><span data-stu-id="71b9e-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="71b9e-134">Program WMF 5.1 rozwiązuje to zwracając pomocy dla najnowszej wersji tego tematu.</span><span class="sxs-lookup"><span data-stu-id="71b9e-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="71b9e-135">`Get-Help` nie zapewnia możliwość określenia, która wersja ma dotyczyć pomoc dla.</span><span class="sxs-lookup"><span data-stu-id="71b9e-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="71b9e-136">Aby obejść ten problem, przejdź do katalogu modułów, a następnie Wyświetl Pomoc bezpośrednio za pomocą narzędzia, takiego jak ulubionego edytora.</span><span class="sxs-lookup"><span data-stu-id="71b9e-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="71b9e-137">Odczytywanie z STDIN PowerShell.exe przerywane.</span><span class="sxs-lookup"><span data-stu-id="71b9e-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="71b9e-138">Klienci używają `powershell -command -` od natywnych aplikacji do wykonywania programu PowerShell przekazywanie skryptu za pomocą STDIN Niestety to został zaburzyć przez inne zmiany w konsoli hosta.</span><span class="sxs-lookup"><span data-stu-id="71b9e-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="71b9e-139">Jest to naprawione w wersji 5.1 w Rocznicowej aktualizacji systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="71b9e-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="71b9e-140">PowerShell.exe tworzy nagły wzrost użycia procesora CPU podczas uruchamiania</span><span class="sxs-lookup"><span data-stu-id="71b9e-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="71b9e-141">PowerShell używa kwerendy usługi WMI, aby sprawdzić, czy została uruchomiona przy użyciu zasad grupy, aby uniknąć, powodując opóźnienie podczas logowania.</span><span class="sxs-lookup"><span data-stu-id="71b9e-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="71b9e-142">Kwerenda WMI kończy się wprowadzanie tzres.mui.dll na każdym etapie procesu w systemie od WMI **Win32_Process** klasy podejmie próbę pobrania informacje dotyczące lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="71b9e-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="71b9e-143">Skutkuje to duży wzrost procesora CPU w **wmiprvse** (host dostawcy WMI).</span><span class="sxs-lookup"><span data-stu-id="71b9e-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="71b9e-144">Obejście polega na użyciu wywołań interfejsu API Win32 te same informacje, a nie przy użyciu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="71b9e-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
