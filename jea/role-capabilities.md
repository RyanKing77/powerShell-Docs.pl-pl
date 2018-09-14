---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Możliwości roli usługi JEA
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522946"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="047a9-103">Możliwości roli usługi JEA</span><span class="sxs-lookup"><span data-stu-id="047a9-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="047a9-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="047a9-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="047a9-105">Podczas tworzenia punktu końcowego JEA, należy zdefiniować co najmniej jeden "możliwości roli" zawierające *co* ktoś można wykonać w ramach sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="047a9-106">Funkcja roli jest plikiem danych środowiska PowerShell z rozszerzeniem .psrc, które wyświetla listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrznych programów, które powinny zostać udostępnione do procesu łączenia użytkowników.</span><span class="sxs-lookup"><span data-stu-id="047a9-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="047a9-107">W tym temacie opisano, jak utworzyć plik możliwości roli programu PowerShell dla użytkowników usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="047a9-108">Określić, jakie polecenia, aby umożliwić</span><span class="sxs-lookup"><span data-stu-id="047a9-108">Determine which commands to allow</span></span>

<span data-ttu-id="047a9-109">Pierwszym krokiem podczas tworzenia pliku możliwości roli jest należy wziąć pod uwagę, jakie użytkownicy, którzy mają przypisaną rolę będą potrzebowali dostępu do.</span><span class="sxs-lookup"><span data-stu-id="047a9-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="047a9-110">To wymaganie procesu zbierania może wymagać trochę czasu, ale jest bardzo ważne procesu.</span><span class="sxs-lookup"><span data-stu-id="047a9-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="047a9-111">Zapewniając użytkownikom dostęp do zbyt małej liczby poleceń cmdlet i funkcji może uniemożliwić ich wprowadzenie ich pracę.</span><span class="sxs-lookup"><span data-stu-id="047a9-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="047a9-112">Zezwalanie na dostęp do zbyt wielu poleceń cmdlet i funkcji może prowadzić do użytkowników, wykonując bardziej niż planowano z ich uprawnieniami administratora niejawne osłabienia Twoje wystąpienie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="047a9-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="047a9-113">Jak obniżyć informacji na temat tego procesu zależy od organizacji i cele, jednak poniższe porady mogą pomóc upewnić się, że jesteś na prawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="047a9-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="047a9-114">**Identyfikowanie** korzystają użytkownicy polecenia do wykonywania ich zadań.</span><span class="sxs-lookup"><span data-stu-id="047a9-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="047a9-115">Może to obejmować badanie informatykami, sprawdzanie skryptów automatyzacji lub analizowanie zapisy sesji programu PowerShell lub dzienniki.</span><span class="sxs-lookup"><span data-stu-id="047a9-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="047a9-116">**Aktualizacja** na użytek narzędzi wiersza polecenia do odpowiedników środowiska PowerShell, jeśli jest to możliwe, najlepsze inspekcji i JEA dostosowywania środowiska.</span><span class="sxs-lookup"><span data-stu-id="047a9-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="047a9-117">Nie można ograniczyć zewnętrznych programów jako dokładnością jako natywnych poleceń cmdlet programu PowerShell i funkcji jea.</span><span class="sxs-lookup"><span data-stu-id="047a9-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="047a9-118">**Ogranicz** zakresu poleceń cmdlet, jeśli to konieczne tylko pozwalają określonych parametrów lub wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="047a9-119">Jest to szczególnie ważne, jeśli użytkownicy tylko powinny mieć możliwość zarządzania części systemu.</span><span class="sxs-lookup"><span data-stu-id="047a9-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="047a9-120">**Utwórz** funkcji niestandardowych w celu zastąpienia polecenia złożonych lub polecenia, które są trudne do ograniczenia jea.</span><span class="sxs-lookup"><span data-stu-id="047a9-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="047a9-121">Prostej funkcji, która opakowuje złożone polecenia lub stosuje logikę dodatkowe sprawdzenie poprawności oferują dodatkową kontrolę dla uproszczenia administratorów i użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="047a9-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="047a9-122">**Test** o określonym zakresie listę dopuszczalnych poleceń z użytkowników i/lub automatyzacji usług i dostosować zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="047a9-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="047a9-123">Koniecznie należy pamiętać, że polecenia w sesji JEA często uprawnieniami Uruchom za pomocą administratora (lub inaczej podwyższonego poziomu uprawnień).</span><span class="sxs-lookup"><span data-stu-id="047a9-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="047a9-124">Staranne wybieranie dostępnych poleceń ważne jest, aby upewnić się, że punkt końcowy usługi JEA nie zezwala na użytkownik nawiązujący połączenie do podniesienia swoich uprawnień.</span><span class="sxs-lookup"><span data-stu-id="047a9-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="047a9-125">Poniżej przedstawiono kilka przykładów poleceń, które mogą służyć złośliwie Jeśli jest to dozwolone w stanie nieograniczone.</span><span class="sxs-lookup"><span data-stu-id="047a9-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="047a9-126">Pamiętaj, że to nie jest kompletną listą i powinna służyć wyłącznie jako punktu wyjścia ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="047a9-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="047a9-127">Przykłady poleceń potencjalnie niebezpiecznych</span><span class="sxs-lookup"><span data-stu-id="047a9-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="047a9-128">Ryzyko</span><span class="sxs-lookup"><span data-stu-id="047a9-128">Risk</span></span> | <span data-ttu-id="047a9-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="047a9-129">Example</span></span> | <span data-ttu-id="047a9-130">Powiązane polecenia</span><span class="sxs-lookup"><span data-stu-id="047a9-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="047a9-131">Udzielanie użytkownik nawiązujący połączenie z uprawnieniami administratora w celu OBEJŚCIE usługi JEA</span><span class="sxs-lookup"><span data-stu-id="047a9-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="047a9-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="047a9-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="047a9-133">Uruchamiania dowolnego kodu, takich jak złośliwe oprogramowanie luki w zabezpieczeniach i niestandardowe skrypty do obejścia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="047a9-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="047a9-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="047a9-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="047a9-135">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="047a9-135">Create a role capability file</span></span>

<span data-ttu-id="047a9-136">Można utworzyć nowy plik możliwości roli programu PowerShell przy użyciu [New PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="047a9-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="047a9-137">Wynikowy plik możliwości roli można otworzyć w edytorze tekstów i zmodyfikowane w celu zezwalania na żądaną polecenia dla roli.</span><span class="sxs-lookup"><span data-stu-id="047a9-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="047a9-138">Dokumentacja pomocy programu PowerShell zawiera kilka przykładów sposobu konfigurowania pliku.</span><span class="sxs-lookup"><span data-stu-id="047a9-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="047a9-139">Polecenia cmdlet programu PowerShell i funkcji</span><span class="sxs-lookup"><span data-stu-id="047a9-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="047a9-140">Aby autoryzować użytkowników o uruchomienie polecenia cmdlet programu PowerShell lub funkcje, należy dodać nazwę polecenia cmdlet lub funkcji do VisbibleCmdlets lub VisibleFunctions pól.</span><span class="sxs-lookup"><span data-stu-id="047a9-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="047a9-141">Jeśli nie masz pewności, czy polecenie jest polecenie cmdlet lub funkcji, możesz uruchomić `Get-Command <name>` i sprawdź właściwość "CommandType" w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="047a9-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="047a9-142">Czasami zakresu określonego polecenia cmdlet lub funkcji jest zbyt ogólnym, na potrzeby użytkowników.</span><span class="sxs-lookup"><span data-stu-id="047a9-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="047a9-143">Administrator systemu DNS, na przykład wymaga jedynie prawdopodobnie uzyskać dostęp do ponownego uruchomienia usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="047a9-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="047a9-144">W środowisku z wieloma dzierżawami, gdy dzierżawcy uzyskują dostęp do narzędzia do samoobsługowego zarządzania dzierżaw, należy ograniczyć do zarządzania za pomocą ich własnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="047a9-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="047a9-145">W takich przypadkach można ograniczyć, które parametry są udostępniane z polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="047a9-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="047a9-146">W bardziej zaawansowanych scenariuszy może być również konieczne ograniczenie wartości, które osoba może dostarczyć do tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="047a9-147">Możliwości roli pozwalają zdefiniować zestaw dozwolonych wartości lub wzorzec wyrażenia regularnego, który jest oceniany w celu określenia, czy dany danych wejściowych może.</span><span class="sxs-lookup"><span data-stu-id="047a9-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="047a9-148">[Typowe parametry programu PowerShell](https://technet.microsoft.com/library/hh847884.aspx) zawsze dozwolone, nawet wtedy, gdy ograniczenia dostępnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="047a9-149">Należy nie jawnie ich listę w polu Parametry.</span><span class="sxs-lookup"><span data-stu-id="047a9-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="047a9-150">W poniższej tabeli opisano różne sposoby, które można dostosować widoczne polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="047a9-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="047a9-151">Możesz mieszać i dopasowywać znajdujących się poniżej w VisibleCmdlets pola.</span><span class="sxs-lookup"><span data-stu-id="047a9-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="047a9-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="047a9-152">Example</span></span>                                                                                      | <span data-ttu-id="047a9-153">Przypadek użycia</span><span class="sxs-lookup"><span data-stu-id="047a9-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="047a9-154">`'My-Func'` lub `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="047a9-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="047a9-155">Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń na parametry.</span><span class="sxs-lookup"><span data-stu-id="047a9-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="047a9-156">Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń na parametry.</span><span class="sxs-lookup"><span data-stu-id="047a9-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="047a9-157">Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji za pomocą zlecenie `My`.</span><span class="sxs-lookup"><span data-stu-id="047a9-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="047a9-158">Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji z rzeczownikiem `Func`.</span><span class="sxs-lookup"><span data-stu-id="047a9-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="047a9-159">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` i/lub `Param2` parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="047a9-160">Dowolna wartość mogą być dostarczane do parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="047a9-161">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru.</span><span class="sxs-lookup"><span data-stu-id="047a9-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="047a9-162">Tylko "Wartość1" i "Wartość2" mogą być dostarczane do parametru.</span><span class="sxs-lookup"><span data-stu-id="047a9-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="047a9-163">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru.</span><span class="sxs-lookup"><span data-stu-id="047a9-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="047a9-164">Żadnej wartości, zaczynając od "contoso" mogą być dostarczane do parametru.</span><span class="sxs-lookup"><span data-stu-id="047a9-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="047a9-165">Aby uzyskać najlepsze rozwiązania w zakresie zabezpieczeń nie zaleca się używać symboli wieloznacznych, podczas definiowania widoczne dla poleceń cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="047a9-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="047a9-166">Zamiast tego należy jawnie listę każdego zaufanych polecenia, aby upewnić się, że żadne polecenia, które współużytkują ten sam schemat nazewnictwa przypadkowo uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="047a9-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="047a9-167">Nie można zastosować ValidatePattern i ValidateSet do tego samego polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="047a9-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="047a9-168">Jeśli to zrobisz, ValidatePattern spowoduje zastąpienie ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="047a9-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="047a9-169">Aby uzyskać więcej informacji na temat ValidatePattern, zapoznaj się [to *Hey, Scripting Guy!* wpis](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) i [wyrażeń regularnych w programie PowerShell](https://technet.microsoft.com/library/hh847880.aspx) odwoływać się do zawartości.</span><span class="sxs-lookup"><span data-stu-id="047a9-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="047a9-170">Dzięki niemu agencje poleceń zewnętrznych i skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="047a9-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="047a9-171">Aby zezwolić użytkownikom na uruchamianie plików wykonywalnych i skryptów programu PowerShell (.ps1) w ramach sesji usługi JEA, musisz dodać pełną ścieżkę do każdego programu, w polu VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="047a9-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="047a9-172">Zalecane jest, jeśli to możliwe, użyj odpowiedników funkcji/polecenia cmdlet programu PowerShell zewnętrznych plików wykonywalnych, autoryzowane, ponieważ masz pełną kontrolę nad tym, którzy parametrów są dozwolone w przypadku poleceń cmdlet programu PowerShell/funkcji.</span><span class="sxs-lookup"><span data-stu-id="047a9-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="047a9-173">Wiele plików wykonywalnych umożliwiają zarówno odczyt bieżącego stanu, a następnie zmienić je po prostu, podając różne parametry.</span><span class="sxs-lookup"><span data-stu-id="047a9-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="047a9-174">Na przykład należy wziąć pod uwagę w roli administratora serwera plików, kto chce, aby sprawdzić, które udziały sieciowe są hostowane przez komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="047a9-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="047a9-175">Jednym ze sposobów, aby sprawdzić, jest użycie `net share`.</span><span class="sxs-lookup"><span data-stu-id="047a9-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="047a9-176">Jednakże, dzięki czemu net.exe jest bardzo niebezpieczny, ponieważ administrator może równie łatwo polecenie służy do uzyskania uprawnień administratora za pomocą `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="047a9-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="047a9-177">Lepszym rozwiązaniem jest umożliwienie [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) które osiąga ten sam wynik, ale ma bardziej ograniczony zakres.</span><span class="sxs-lookup"><span data-stu-id="047a9-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="047a9-178">Podczas wprowadzania poleceń zewnętrznych dostępnych dla użytkowników w ramach sesji usługi JEA, zawsze należy określić pełną ścieżkę do pliku wykonywalnego, aby upewnić się, program o podobnej nazwie (i potencjalnie malicous) umieszczone w innym miejscu w systemie nie są wykonywane zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="047a9-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="047a9-179">Zezwalanie na dostęp do dostawcy programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="047a9-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="047a9-180">Domyślnie żaden dostawca programu PowerShell są dostępne w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="047a9-181">To jest głównie zmniejszenia ryzyka poufnych informacji i ustawienia konfiguracji zostały ujawnione użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="047a9-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="047a9-182">Gdy jest to konieczne, można zezwolić na dostęp do dostawcy programu PowerShell przy użyciu `VisibleProviders` polecenia.</span><span class="sxs-lookup"><span data-stu-id="047a9-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="047a9-183">Aby uzyskać pełną listę dostawców, uruchamianie `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="047a9-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="047a9-184">Proste zadania, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych dostawców poufnych możesz też rozważyć pisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="047a9-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="047a9-185">Funkcje, poleceń cmdlet i zewnętrznych programów, które są dostępne w ramach sesji usługi JEA nie podlegają tych samych ograniczeń, jak JEA — mogą uzyskiwać dostęp do dowolnego dostawcy domyślnie.</span><span class="sxs-lookup"><span data-stu-id="047a9-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="047a9-186">Ponadto należy wziąć pod uwagę przy użyciu [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do/z punktu końcowego JEA jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="047a9-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="047a9-187">Tworzenie funkcji niestandardowych</span><span class="sxs-lookup"><span data-stu-id="047a9-187">Creating custom functions</span></span>

<span data-ttu-id="047a9-188">Można tworzyć niestandardowe funkcje w pliku możliwości roli, aby uprościć złożone zadania dla użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="047a9-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="047a9-189">Funkcje niestandardowe są również przydatne, gdy potrzebujesz logikę weryfikacji zaawansowane o wprowadzenie wartości parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="047a9-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="047a9-190">Możesz pisać proste funkcje **FunctionDefinitions** pola:</span><span class="sxs-lookup"><span data-stu-id="047a9-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="047a9-191">Nie zapomnij dodać nazwę Twojej funkcji niestandardowych do **VisibleFunctions** pola, aby mogły być uruchamiane przez użytkowników usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="047a9-192">Treść funkcji niestandardowych (blok skryptu) działa w trybie język domyślny dla systemu i nie jest przedmiotem ograniczeń języka firmy JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="047a9-193">Oznacza to, czy funkcje można uzyskać dostęp do systemu plików i rejestru i uruchamiania poleceń, które zostały utworzone widoczny w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="047a9-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="047a9-194">Pamiętaj, aby uniknąć, dzięki czemu dowolny kod ma być uruchamiany przy użyciu parametrów i uniknąć dane wejściowe użytkownika potokowanie bezpośrednio do polecenia cmdlet, takich jak `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="047a9-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="047a9-195">W powyższym przykładzie można zauważyć, że nazwa FQDN modułu (FQMN) `Microsoft.PowerShell.Utility\Select-Object` był używany zamiast skrót `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="047a9-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="047a9-196">Funkcje zdefiniowane w plikach możliwości roli są nadal podlega procesowi zakresu sesji JEA, który zawiera funkcje serwera proxy usługi JEA tworzy ograniczenie istniejące polecenia.</span><span class="sxs-lookup"><span data-stu-id="047a9-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="047a9-197">Select-Object jest domyślnie ograniczone polecenia cmdlet we wszystkich sesjach JEA, który nie zezwala na wybranie dowolnego właściwości obiektów.</span><span class="sxs-lookup"><span data-stu-id="047a9-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="047a9-198">Aby używać nieograniczonego Select-Object w przypadku funkcji, możesz jawne żądanie pełną implementację, określając FQMN.</span><span class="sxs-lookup"><span data-stu-id="047a9-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="047a9-199">Każdego ograniczone polecenia cmdlet w sesji JEA będzie mieć takie samo zachowanie, gdy wywoływana z funkcji, zgodnie z programu PowerShell [polecenia pierwszeństwo](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="047a9-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="047a9-200">Jeśli piszesz wiele niestandardowych funkcji może być łatwiej je umieszczać [modułu skryptu PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="047a9-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="047a9-201">Następnie można wprowadzić te funkcje widoczne w sesji JEA, korzystając z pola VisibleFunctions, jak w przypadku modułów wbudowane i innych firm.</span><span class="sxs-lookup"><span data-stu-id="047a9-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="047a9-202">W module umieścić możliwości roli</span><span class="sxs-lookup"><span data-stu-id="047a9-202">Place role capabilities in a module</span></span>

<span data-ttu-id="047a9-203">Aby dla programu PowerShell, aby znaleźć plik możliwości roli muszą być przechowywane w folderze "RoleCapabilities" w module programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="047a9-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="047a9-204">Moduł mogą być przechowywane w dowolnym folderze zawarte w `$env:PSModulePath` zmiennej środowiskowej, jednak należy nie umieszczać w System32 (zarezerwowane dla wbudowanych modułów) lub folderu gdzie niezaufanych, łączenie użytkowników można zmodyfikować pliki.</span><span class="sxs-lookup"><span data-stu-id="047a9-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="047a9-205">Poniżej znajduje się przykład tworzenia podstawowych moduł skrypt programu PowerShell o nazwie *ContosoJEA* w ścieżce "Program Files".</span><span class="sxs-lookup"><span data-stu-id="047a9-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="047a9-206">Zobacz [opis modułu programu PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) Aby uzyskać więcej informacji na temat modułów programu PowerShell, moduł manifesty i zmienną środowiskową PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="047a9-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="047a9-207">Aktualizowanie możliwości roli</span><span class="sxs-lookup"><span data-stu-id="047a9-207">Updating role capabilities</span></span>


<span data-ttu-id="047a9-208">Aby zaktualizować plik możliwości roli w dowolnym momencie, po prostu zapisywanie zmian w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="047a9-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="047a9-209">Wszystkie nowe sesje JEA pracę po zaktualizowaniu możliwości roli będą odzwierciedlać poprawione możliwości.</span><span class="sxs-lookup"><span data-stu-id="047a9-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="047a9-210">Jest to, dlaczego kontrola dostępu do folderu możliwości roli jest tak ważny.</span><span class="sxs-lookup"><span data-stu-id="047a9-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="047a9-211">Tylko wysoce zaufanych administratorów powinno być możliwe na zmianę plików możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="047a9-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="047a9-212">Niezaufanego użytkownika mogą zmieniać pliki możliwości roli, łatwo udzielenie się dostępu do poleceń cmdlet, co pozwala je do podniesienia swoich uprawnień.</span><span class="sxs-lookup"><span data-stu-id="047a9-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="047a9-213">Dla administratorów chcących blokowanie dostępu do możliwości roli upewnij się, że System lokalny ma dostęp do odczytu do plików funkcji roli i zawierającego moduły.</span><span class="sxs-lookup"><span data-stu-id="047a9-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="047a9-214">Jak są scalane możliwości roli</span><span class="sxs-lookup"><span data-stu-id="047a9-214">How role capabilities are merged</span></span>

<span data-ttu-id="047a9-215">Użytkownicy mogą uzyskać dostęp do wiele możliwości roli po użytkownik podał sesję JEA w zależności od roli mapowania w [plik konfiguracji sesji](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="047a9-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="047a9-216">W takim przypadku JEA próbuje przyznać użytkownikowi *restrykcyjny* zestaw poleceń dozwolone przez dowolną rolę.</span><span class="sxs-lookup"><span data-stu-id="047a9-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="047a9-217">**VisibleCmdlets i VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="047a9-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="047a9-218">Najbardziej złożoną logikę scalanie wpływa na poleceń cmdlet i funkcje, które mogą mieć ich parametrów i wartości parametrów ograniczone jea.</span><span class="sxs-lookup"><span data-stu-id="047a9-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="047a9-219">Dostępne są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="047a9-219">The rules are as follows:</span></span>

1. <span data-ttu-id="047a9-220">Jeśli polecenie cmdlet jest dostępne tylko widoczne w jednej roli, będzie widoczna dla użytkownika o wszelkich ograniczeń odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="047a9-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="047a9-221">Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola ma ograniczenia tego samego polecenia cmdlet, polecenie cmdlet będzie widoczny dla użytkownika przy użyciu tych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="047a9-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="047a9-222">Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola umożliwia inny zbiór parametrów, polecenia cmdlet i wszystkich parametrów zdefiniowanych w każdej roli będą widoczne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="047a9-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="047a9-223">Jeśli jedna rola nie ma ograniczenia dotyczące parametrów, będą miały wszystkie parametry.</span><span class="sxs-lookup"><span data-stu-id="047a9-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="047a9-224">Jeśli jedna rola definiuje zestaw sprawdzania poprawności lub wzorca weryfikacji dla parametru polecenia cmdlet, a także innych ról pozwala parametru, ale nie ogranicza wartości parametrów, sprawdzanie poprawności zestawu lub wzorzec zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="047a9-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="047a9-225">Jeśli zestaw sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, może być wszystkie wartości z wszystkich zestawów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="047a9-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="047a9-226">Jeśli wzorzec sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, będą miały żadnych wartości, które pasuje do żadnego z wzorców.</span><span class="sxs-lookup"><span data-stu-id="047a9-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="047a9-227">Jeśli zestaw sprawdzania poprawności jest zdefiniowany w co najmniej jedną rolę, a wzorzec sprawdzania poprawności jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, zestaw sprawdzania poprawności jest ignorowana, a do pozostałych wzorców sprawdzania poprawności zostanie zastosowana reguła (6).</span><span class="sxs-lookup"><span data-stu-id="047a9-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="047a9-228">Poniżej przedstawiono przykładowy sposób role są łączone zgodnie z tymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="047a9-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="047a9-229">**VisibleExternalCommands, ScriptsToProcess VisibleAliases, VisibleProviders,**</span><span class="sxs-lookup"><span data-stu-id="047a9-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="047a9-230">Wszystkie pola w pliku możliwości roli, po prostu są dodawane do zbiorczego zestawu poleceń zewnętrznych dopuszczalny rozmiar, aliasy, dostawców i skrypty uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="047a9-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="047a9-231">Polecenia, alias, dostawca lub skryptu w jedną rolę możliwości będą dostępne dla użytkownika usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="047a9-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="047a9-232">Uważaj upewnić się, że połączony zestaw dostawców z jednej roli funkcji i poleceń cmdlet/funkcje/poleceń z innego nie zezwalają na połączenia użytkowników niezamierzonego dostępu do zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="047a9-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="047a9-233">Na przykład, jeśli zezwala na jedną rolę `Remove-Item` polecenia cmdlet, a drugi umożliwia `FileSystem` dostawcy, są narażeni użytkownika JEA usuwanie dowolnych plików na komputerze.</span><span class="sxs-lookup"><span data-stu-id="047a9-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="047a9-234">Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników można znaleźć w [inspekcji JEA temacie](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="047a9-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="047a9-235">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="047a9-235">Next steps</span></span>

- [<span data-ttu-id="047a9-236">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="047a9-236">Create a session configuration file</span></span>](session-configurations.md)