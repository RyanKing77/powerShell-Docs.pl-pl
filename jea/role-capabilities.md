---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Możliwości roli JEA
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190540"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="2f5f1-103">Możliwości roli JEA</span><span class="sxs-lookup"><span data-stu-id="2f5f1-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="2f5f1-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2f5f1-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2f5f1-105">Podczas tworzenia punktu końcowego JEA, musisz zdefiniować co najmniej jeden "roli funkcji" opisujące *co* ktoś zrobić w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="2f5f1-106">Możliwość roli jest plik danych programu PowerShell z rozszerzeniem .psrc, które wyświetla listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrzne programy, które powinny być udostępniane łączenia użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="2f5f1-107">W tym temacie opisano, jak utworzyć plik programu PowerShell roli możliwości użytkowników JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="2f5f1-108">Ustalić, jakie polecenia, aby umożliwić</span><span class="sxs-lookup"><span data-stu-id="2f5f1-108">Determine which commands to allow</span></span>

<span data-ttu-id="2f5f1-109">Pierwszym krokiem podczas tworzenia pliku możliwości roli jest określenie, co użytkownicy, którzy mają przypisaną rolę wymaga dostępu do.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="2f5f1-110">Wymagania, ten proces zbierania może trochę potrwać, ale jest bardzo ważne procesu.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="2f5f1-111">Przyznawanie użytkownikom dostępu do zbyt mało polecenia cmdlet i funkcje może uniemożliwić ich pobierania ich pracy.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="2f5f1-112">Zezwalania na dostęp do zbyt wielu poleceń cmdlet i funkcje może prowadzić do użytkowników czynności więcej niż przeznaczone z ich uprawnieniami administratora niejawne osłabienia Twojej strony zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="2f5f1-113">Jak przejść na ten tego procesu zależy od organizacji i cele, jednak poniższe porady mogą pomóc, upewnij się, że jesteś na prawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="2f5f1-114">**Zidentyfikuj** użytkowników poleceń używasz do wykonywania pracy.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="2f5f1-115">Może to obejmować badanie personel działu informatycznego, sprawdzanie skryptów automatyzacji lub analizowania zapisy sesji programu PowerShell lub dzienniki.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="2f5f1-116">**Aktualizacja** używać narzędzi wiersza polecenia, aby ich odpowiedniki programu PowerShell, jeśli to możliwe, najlepszą inspekcji i JEA dostosowanie doświadczenie.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="2f5f1-117">Nie można ograniczyć programy zewnętrzne jako częściami jako natywnych poleceń cmdlet programu PowerShell i funkcji w ramach zasad JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="2f5f1-118">**Ogranicz** zakresu polecenia cmdlet, jeśli to konieczne tylko pozwalają określonych parametrów lub wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="2f5f1-119">Jest to szczególnie ważne, jeśli użytkownicy powinni być tylko możliwość zarządzania części systemu.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="2f5f1-120">**Utwórz** niestandardowych funkcji w celu zastąpienia złożonych polecenia lub poleceń, które są trudne do ograniczyć w ramach zasad JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="2f5f1-121">Proste funkcję, która opakowuje złożone polecenia lub stosuje logikę weryfikacji dodatkowe mogą oferować dodatkową kontrolę dla uproszczenia administratorów i użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="2f5f1-122">**Test** listy zakresie dozwolonym poleceń użytkowników i/lub automatyzacji usług i Dostosuj odpowiednio do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="2f5f1-123">Należy pamiętać, że polecenia w sesji JEA są często uprawnień uruchom admin (lub w inny sposób z podniesionymi uprawnieniami).</span><span class="sxs-lookup"><span data-stu-id="2f5f1-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="2f5f1-124">Staranne wybieranie dostępnych poleceń ważne jest, aby upewnić się, że punkt końcowy JEA nie zezwala użytkownik nawiązujący połączenie podniesienie poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="2f5f1-125">Poniżej przedstawiono kilka przykładów poleceń, których można użyć złośliwie Jeśli dozwolone w stanie nieograniczonego.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="2f5f1-126">Zauważ, że to nie jest kompletną listą i należy używać tylko jako punktu wyjścia ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="2f5f1-127">Przykłady poleceń potencjalnie niebezpiecznych</span><span class="sxs-lookup"><span data-stu-id="2f5f1-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="2f5f1-128">Ryzyko</span><span class="sxs-lookup"><span data-stu-id="2f5f1-128">Risk</span></span> | <span data-ttu-id="2f5f1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f5f1-129">Example</span></span> | <span data-ttu-id="2f5f1-130">Pokrewne polecenia</span><span class="sxs-lookup"><span data-stu-id="2f5f1-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="2f5f1-131">Udzielanie uprawnień administratora, aby pominąć JEA użytkownik nawiązujący połączenie</span><span class="sxs-lookup"><span data-stu-id="2f5f1-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="2f5f1-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="2f5f1-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="2f5f1-133">Uruchomienia dowolnego kodu, np. złośliwego oprogramowania, luki w zabezpieczeniach lub niestandardowych skryptów do obejścia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2f5f1-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="2f5f1-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="2f5f1-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="2f5f1-135">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="2f5f1-135">Create a role capability file</span></span>

<span data-ttu-id="2f5f1-136">Można utworzyć nowy plik możliwości roli programu PowerShell z [PSRoleCapabilityFile nowy](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="2f5f1-137">Wynikowy plik możliwości roli można go otworzyć w edytorze tekstów i zmodyfikowane w celu umożliwienia żądanych poleceń dla roli.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="2f5f1-138">Dokumentacja pomocy programu PowerShell zawiera kilka przykładów sposobu konfigurowania pliku.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="2f5f1-139">Stosowanie poleceń cmdlet programu PowerShell i funkcji</span><span class="sxs-lookup"><span data-stu-id="2f5f1-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="2f5f1-140">Aby zezwolić użytkownikom na uruchamianie poleceń cmdlet programu PowerShell lub funkcje, Dodaj nazwę polecenia cmdlet lub funkcja do VisbibleCmdlets lub VisibleFunctions pól.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="2f5f1-141">Jeśli nie masz pewności, czy polecenie jest polecenie cmdlet lub funkcji, można uruchomić `Get-Command <name>` i sprawdź właściwość "CommandType" w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="2f5f1-142">Czasami zakres konkretnego polecenia cmdlet lub funkcji jest zbyt szerokie do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="2f5f1-143">Administrator DNS, na przykład potrzeby prawdopodobnie tylko dostęp do Uruchom ponownie usługę DNS.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="2f5f1-144">W środowisku wielu dzierżawców gdzie dzierżaw uzyskają dostęp do narzędzia do samoobsługowego zarządzania dzierżaw powinien być ograniczony do zarządzanie za pomocą ich własnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="2f5f1-145">W tych przypadkach można ograniczyć, parametry, które są dostępne z polecenie cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="2f5f1-146">W bardziej zaawansowanych scenariuszy, może być również konieczne ograniczanie ktoś może dostarczyć wartości dla tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="2f5f1-147">Możliwości roli pozwalają zdefiniować zestaw dozwolonych wartości lub wzorzec wyrażenia regularnego, które jest obliczane w celu ustalenia, czy jest dozwolone w określonych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="2f5f1-148">[Typowe parametry programu PowerShell](https://technet.microsoft.com/library/hh847884.aspx) są zawsze dozwolone, nawet jeśli ograniczysz dostępnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="2f5f1-149">Użytkownik nie powinny jawnie zawierać je w polu Parametry.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="2f5f1-150">W poniższej tabeli opisano różne sposoby, które można dostosować widoczne polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="2f5f1-151">Można mieszać i zgodna z żadną poniżej w VisibleCmdlets pola.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="2f5f1-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f5f1-152">Example</span></span>                                                                                      | <span data-ttu-id="2f5f1-153">Przypadek użycia</span><span class="sxs-lookup"><span data-stu-id="2f5f1-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="2f5f1-154">`'My-Func'` lub `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="2f5f1-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="2f5f1-155">Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń na parametry.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="2f5f1-156">Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń na parametry.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="2f5f1-157">Zezwala użytkownikowi na uruchamianie polecenia cmdlet ani funkcja ze zleceniem `My`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="2f5f1-158">Zezwala użytkownikowi na Uruchom polecenie cmdlet ani funkcji z rzeczownikiem `Func`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="2f5f1-159">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` i/lub `Param2` parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="2f5f1-160">Można podać wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="2f5f1-161">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="2f5f1-162">Tylko "Wartość1" i "Wartość2" mogą być dostarczane do parametru.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="2f5f1-163">Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="2f5f1-164">Można podać wartości, zaczynając od "contoso" do parametru.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="2f5f1-165">Aby uzyskać najlepsze rozwiązania w zakresie zabezpieczeń nie zaleca się użyć symboli wieloznacznych, definiując widoczne poleceń cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="2f5f1-166">Zamiast tego należy jawnie listy każdego zaufanych polecenie, aby upewnić się, że wszystkie inne polecenia, które współużytkują tego samego schematu nazewnictwa przypadkowo są autoryzowane.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="2f5f1-167">Zarówno ValidatePattern i ValidateSet nie można zastosować do tego samego polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="2f5f1-168">Jeśli to zrobisz, ValidatePattern przesłoni ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="2f5f1-169">Aby uzyskać więcej informacji na temat ValidatePattern, zapoznaj się z [to *Witaj, Twórco skryptów!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) i [wyrażeń regularnych programu PowerShell](https://technet.microsoft.com/library/hh847880.aspx) odwołania zawartości.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="2f5f1-170">Stosowanie zewnętrznych poleceń i skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f5f1-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="2f5f1-171">Aby zezwolić użytkownikom na uruchamianie plików wykonywalnych i skryptów programu PowerShell (ps1) w sesji JEA, należy dodać pełną ścieżkę do każdego programu w polu VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="2f5f1-172">Zalecane jest, gdzie to możliwe, użyj programu PowerShell polecenia cmdlet/funkcja odpowiedniki zewnętrznych plików wykonywalnych, zezwolić, ponieważ mają kontroli nad którym parametry są dozwolone z poleceń cmdlet programu PowerShell/funkcje.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="2f5f1-173">Wiele plików wykonywalnych umożliwiają zarówno odczytać bieżący stan, a następnie zmień ją tak, zapewniając innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="2f5f1-174">Rozważmy na przykład rolę Administrator serwera plików, który chce, aby sprawdzić, które udziały sieciowe są obsługiwane przez komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="2f5f1-175">Jednym ze sposobów sprawdzenia, jest użycie `net share`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="2f5f1-176">Jednakże, dzięki czemu net.exe jest bardzo niebezpieczne, ponieważ administrator może równie łatwo używać polecenia w celu uzyskania uprawnień administratora z `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="2f5f1-177">Lepszym rozwiązaniem jest umożliwienie [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) które osiąga ten sam rezultat, ale ma znacznie bardziej ograniczony zakres.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="2f5f1-178">Podczas wprowadzania poleceń zewnętrznych dostępne dla użytkowników w sesji JEA, należy zawsze podać pełną ścieżkę do pliku wykonywalnego, aby upewnić się o podobnej nazwie (i potencjalnie malicous) program umieszczone w innym miejscu w systemie nie są wykonywane zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="2f5f1-179">Zezwalanie na dostęp do dostawcy programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f5f1-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="2f5f1-180">Domyślnie nie dostawcy programu PowerShell są dostępne w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="2f5f1-181">To jest głównie zmniejszenia ryzyka poufne informacje i ustawienia konfiguracji są ujawniane użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="2f5f1-182">Jeśli to konieczne, można zezwolić na dostęp do dostawcy programu PowerShell przy użyciu `VisibleProviders` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="2f5f1-183">Aby zapoznać się z pełną listą dostawców, uruchamiania `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="2f5f1-184">Proste zadania, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych poufnych dostawców należy również rozważyć pisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="2f5f1-185">Funkcje, polecenia cmdlet i programów zewnętrznych, które są dostępne w sesji JEA nie podlegają takich samych ograniczeń jako JEA — domyślnie uzyskać dostęp do każdego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="2f5f1-186">Należy również rozważyć przy użyciu [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do/z punktu końcowego JEA jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="2f5f1-187">Tworzenie funkcji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="2f5f1-187">Creating custom functions</span></span>

<span data-ttu-id="2f5f1-188">Można tworzyć niestandardowe funkcji w pliku możliwości roli uprościć złożone zadania dla użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="2f5f1-189">Funkcje niestandardowe są także przydatne, gdy wymagają logikę weryfikacji zaawansowane wartości parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="2f5f1-190">Proste funkcje można pisać w **FunctionDefinitions** pola:</span><span class="sxs-lookup"><span data-stu-id="2f5f1-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

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
> <span data-ttu-id="2f5f1-191">Nie zapomnij dodać nazwę funkcji niestandardowych do **VisibleFunctions** pól, co może być uruchamiane przez użytkowników JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="2f5f1-192">Treść funkcji niestandardowych (bloku skryptu) działa w trybie język domyślny dla systemu i nie podlega JEA w języku ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="2f5f1-193">Oznacza to, że funkcji można uzyskiwać dostęp do systemu plików i rejestru i uruchamiania poleceń, które zostały utworzone widoczne w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="2f5f1-194">Zwrócić uwagę, aby uniknąć dowolnego kodu ma być uruchamiany przy użyciu parametrów i uniknąć potokowanie danych wejściowych użytkownika bezpośrednio do polecenia cmdlet, takich jak `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="2f5f1-195">W powyższym przykładzie, można zauważyć, że nazwa FQDN modułu (FQMN) `Microsoft.PowerShell.Utility\Select-Object` użyto zamiast skrócona `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="2f5f1-196">Funkcje zdefiniowane w plikach możliwości roli nadal obowiązują na zakres JEA sesji, która obejmuje funkcje serwera proxy JEA tworzy ograniczyć istniejących poleceń.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="2f5f1-197">Select-Object jest domyślnie ograniczonego polecenia cmdlet we wszystkich sesjach JEA, który nie pozwala na wybranie dowolnego właściwości obiektów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="2f5f1-198">Aby używać nieograniczonego Select-Object w funkcjach, określając FQMN musi jawne żądanie pełnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="2f5f1-199">Ograniczone dowolnym poleceniu cmdlet w sesji JEA będzie mieć takie samo zachowanie, gdy została wywołana z funkcji, zgodnie z jego środowiska PowerShell [pierwszeństwa poleceń](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="2f5f1-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="2f5f1-200">Jeśli piszesz wiele funkcji niestandardowych, może być łatwiej umieść je w [moduł skryptu programu PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="2f5f1-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="2f5f1-201">Następnie można wprowadzić te funkcje widoczne w sesji JEA, korzystając z pola VisibleFunctions, jak w przypadku modułów wbudowane i innych firm.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="2f5f1-202">Umieść funkcji ról w module</span><span class="sxs-lookup"><span data-stu-id="2f5f1-202">Place role capabilities in a module</span></span>

<span data-ttu-id="2f5f1-203">Aby dla programu PowerShell znaleźć plik możliwości roli muszą być przechowywane w folderze "RoleCapabilities" w module środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="2f5f1-204">Moduł mogą być przechowywane w dowolnym folderze zawarte w `$env:PSModulePath` zmiennej środowiskowej, jednak należy nie umieszczać w System32 (zastrzeżone dla wbudowanych modułów) lub w folderze gdzie niezaufanych, łączenie użytkowników można zmodyfikować plików.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="2f5f1-205">Poniżej przedstawiono przykład tworzenia podstawowych moduł skryptu programu PowerShell o nazwie *ContosoJEA* w ścieżce "Program Files".</span><span class="sxs-lookup"><span data-stu-id="2f5f1-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

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

<span data-ttu-id="2f5f1-206">Zobacz [opis modułu programu PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) uzyskać więcej informacji o moduły programu PowerShell, manifesty modułu i PSModulePath zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="2f5f1-207">Aktualizowanie roli</span><span class="sxs-lookup"><span data-stu-id="2f5f1-207">Updating role capabilities</span></span>


<span data-ttu-id="2f5f1-208">Należy zaktualizować plik możliwości roli w dowolnym momencie przez po prostu zapisywanie zmian w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="2f5f1-209">Wszystkie nowe sesje JEA uruchomiony po zaktualizowaniu możliwości roli będzie odzwierciedlać poprawione funkcje.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="2f5f1-210">To dlatego tak ważne jest kontrolowanie dostępu do folderu możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="2f5f1-211">Tylko wysoce zaufanych administratorów powinna być możliwość zmiany roli plikach możliwości.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="2f5f1-212">Niezaufanych użytkownik może zmienić plikach możliwości roli, łatwo przyznanie sobie dostępu do poleceń cmdlet, które zezwolić im na podniesienie ich uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="2f5f1-213">Dla administratorów chcących blokowania dostępu do funkcji roli upewnij się, że System lokalny ma dostęp do odczytu do plików możliwości roli i zawierające moduły.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="2f5f1-214">Jak są scalane możliwości roli</span><span class="sxs-lookup"><span data-stu-id="2f5f1-214">How role capabilities are merged</span></span>

<span data-ttu-id="2f5f1-215">Użytkownicy mogą uzyskać dostęp do wiele możliwości roli po wprowadzeniu JEA sesji w zależności od roli mapowania w [pliku konfiguracji sesji](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f1-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="2f5f1-216">W takim przypadku JEA próbuje dla użytkownika *najbardziej ograniczająca* zestaw poleceń, przy użyciu jednej z ról.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="2f5f1-217">**VisibleCmdlets i VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="2f5f1-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="2f5f1-218">Najbardziej złożonej logiki scalania dotyczy poleceń cmdlet i funkcje, które mogą ich parametrów i wartości parametrów w ramach zasad JEA ograniczone.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="2f5f1-219">Dostępne są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="2f5f1-219">The rules are as follows:</span></span>

1. <span data-ttu-id="2f5f1-220">Jeśli polecenie cmdlet tylko stają się widoczne w jedną rolę, będą widoczne dla użytkowników z żadnych ograniczeń odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="2f5f1-221">Jeśli polecenie cmdlet stają się widoczne w więcej niż jednej roli, a każda rola ma takich samych ograniczeń na polecenia cmdlet, polecenie cmdlet będą widoczne dla użytkowników z tych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="2f5f1-222">Jeśli polecenie cmdlet stają się widoczne w więcej niż jednej roli, a tych rolach inny zestaw parametrów, polecenia cmdlet i wszystkich parametrów zdefiniowanych w każdej roli będzie widoczny dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="2f5f1-223">Jeśli jedna rola nie ma ograniczenia dotyczące parametrów, dozwolone będą wszystkie parametry.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="2f5f1-224">Jeśli jedną rolę definiuje zestaw weryfikacji lub wzorca sprawdzania poprawności dla parametru polecenia cmdlet i innych ról pozwala parametru, ale nie ograniczenie wartości parametrów, sprawdzanie poprawności zestawu lub wzorzec zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="2f5f1-225">Zestaw weryfikacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone będą wszystkie wartości ze wszystkich zbiorów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="2f5f1-226">Jeśli wzorzec weryfikacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone wartości, które spełniają wzorce.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="2f5f1-227">Jeśli zestaw weryfikacji jest zdefiniowany w jedną lub więcej ról, a wzorzec weryfikacji jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, jest ignorowana, ustaw weryfikacji i reguła (6) jest stosowana do pozostałych wzorców weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="2f5f1-228">Poniżej przedstawiono przykładowy sposób role są łączone zgodnie z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="2f5f1-228">Below is an example of how roles are merged according to these rules:</span></span>

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



<span data-ttu-id="2f5f1-229">**VisibleExternalCommands, ScriptsToProcess VisibleAliases, VisibleProviders,**</span><span class="sxs-lookup"><span data-stu-id="2f5f1-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="2f5f1-230">Wszystkie pola w pliku możliwości roli po prostu są dodawane do zbiorczego zestawu dopuszczalny poleceń zewnętrznych, aliasy dostawców i skrypty uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="2f5f1-231">Polecenia, aliasu, dostawcy lub dostępne w jednym możliwości roli skryptu będzie dostępne dla użytkownika JEA.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="2f5f1-232">Uważaj, upewnij się, że połączony zestaw dostawców z jednego możliwości roli i poleceń cmdlet/funkcje/poleceń z innego nie zezwalają na użytkowników łączących niezamierzone dostęp do zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="2f5f1-233">Na przykład, jeśli zezwala na jedną rolę `Remove-Item` polecenia cmdlet, a druga zezwala `FileSystem` dostawcy, są narażeni na ataki użytkownika JEA usuwanie dowolnych plików na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2f5f1-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="2f5f1-234">Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników znajdują się w [inspekcji tematu JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f1-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f5f1-235">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2f5f1-235">Next steps</span></span>

- [<span data-ttu-id="2f5f1-236">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="2f5f1-236">Create a session configuration file</span></span>](session-configurations.md)