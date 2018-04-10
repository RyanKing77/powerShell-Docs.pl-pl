---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie zmiennych na potrzeby przechowywania obiektów
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="c8d1f-103">Używanie zmiennych na potrzeby przechowywania obiektów</span><span class="sxs-lookup"><span data-stu-id="c8d1f-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="c8d1f-104">PowerShell współpracuje z obiektami.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-104">PowerShell works with objects.</span></span> <span data-ttu-id="c8d1f-105">PowerShell umożliwia tworzenie zmiennych zasadniczo o nazwie obiektów, aby zachować dane wyjściowe do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="c8d1f-106">Jeśli są używane do pracy z zmiennych w innych powłok należy pamiętać, że zmienne środowiska PowerShell obiektów, nie tekstu.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="c8d1f-107">Zmienne zawsze są określane za pomocą $ litery i może zawierać dowolne znaki alfanumeryczne lub podkreślenie w nazwach.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="c8d1f-108">Tworzenie zmiennej</span><span class="sxs-lookup"><span data-stu-id="c8d1f-108">Creating a Variable</span></span>
<span data-ttu-id="c8d1f-109">Można utworzyć zmiennej, wpisz prawidłową nazwę zmiennej:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="c8d1f-110">Zwraca żadnego wyniku, ponieważ **$loc** nie ma wartości.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="c8d1f-111">Można utworzyć zmienną i przypisz mu wartość w tym samym kroku.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="c8d1f-112">PowerShell tylko tworzy zmiennej, jeśli nie istnieją; w przeciwnym razie przypisuje określona wartość istniejącej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="c8d1f-113">Do przechowywania bieżącej lokalizacji w zmiennej **$loc**, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="c8d1f-114">Brak żadnych danych wyjściowych wyświetlane po wpisaniu tego polecenia, ponieważ dane wyjściowe są wysyłane do $loc.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="c8d1f-115">W programie PowerShell wyświetlanych wyników jest efektem ubocznym fakt, że dane, który nie jest w przeciwnym razie skierowany, zawsze są wysyłane do ekranu.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="c8d1f-116">Wpisywanie $loc wyświetli bieżącej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="c8d1f-117">Można użyć **elementu członkowskiego Get** do wyświetlania informacji o zawartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="c8d1f-118">Przekazanie w potoku $loc do elementu członkowskiego Get będzie pokazują, że jest **PATHINFO zawiera** obiektu, podobnie jak dane wyjściowe z lokalizacji pobierania:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="c8d1f-119">Manipulowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="c8d1f-119">Manipulating Variables</span></span>
<span data-ttu-id="c8d1f-120">PowerShell zawiera kilka poleceń do modyfikowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="c8d1f-121">Aby zobaczyć pełną listę w czytelnej postaci, należy wpisać:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="c8d1f-122">Oprócz zmiennych tworzonych w bieżącej sesji programu PowerShell istnieje kilka zmienne zdefiniowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="c8d1f-123">Można użyć **Remove-Variable** polecenia cmdlet, aby umożliwić wyczyszczenie wszystkich zmiennych, które nie są kontrolowane przez programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="c8d1f-124">Wpisz następujące polecenie, aby wyczyścić wszystkie zmienne:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="c8d1f-125">Spowoduje to utworzenie poniższą monit o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="c8d1f-126">Jeśli następnie uruchom **Get-Variable** polecenia cmdlet, zobaczysz pozostałych zmiennych środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="c8d1f-127">Ponieważ jest również zmienną dysku środowiska PowerShell, można także wyświetlić wszystkich zmiennych środowiska PowerShell, wpisując:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="c8d1f-128">Korzystając ze zmiennych Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="c8d1f-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="c8d1f-129">Mimo że programu PowerShell nie jest Cmd.exe, jest uruchamiany w środowisku powłoki poleceń i można używać tego samego zmiennych dostępnych w każdym środowisku w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="c8d1f-130">Te zmienne są dostępne za pośrednictwem dysku o nazwie **env**:.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="c8d1f-131">Te zmienne można wyświetlić, wpisując:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="c8d1f-132">Mimo że cmdlet zmiennej standardowe nie są zaprojektowane do pracy z **env:** zmiennych, nadal można je, określając **env:** prefiks.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="c8d1f-133">Na przykład, aby wyświetlić katalog główny systemu operacyjnego, można użyć powłoki poleceń **katalogu % SystemRoot %** zmienną z wewnątrz środowiska PowerShell, wpisując:</span><span class="sxs-lookup"><span data-stu-id="c8d1f-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="c8d1f-134">Można również tworzyć i modyfikować zmiennych środowiskowych z wewnątrz środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="c8d1f-135">Zmienne środowiskowe dostępne z programu Windows PowerShell jest zgodna z normalnym reguły dotyczące zmiennych środowiskowych w innym miejscu w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="c8d1f-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>