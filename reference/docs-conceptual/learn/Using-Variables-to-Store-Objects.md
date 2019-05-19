---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Używanie zmiennych na potrzeby przechowywania obiektów
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 16e82b83df967674da11193c8ac60d637687a01b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854331"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="1f655-103">Używanie zmiennych na potrzeby przechowywania obiektów</span><span class="sxs-lookup"><span data-stu-id="1f655-103">Using variables to store objects</span></span>

<span data-ttu-id="1f655-104">Program PowerShell działa z obiektami.</span><span class="sxs-lookup"><span data-stu-id="1f655-104">PowerShell works with objects.</span></span> <span data-ttu-id="1f655-105">Program PowerShell umożliwia tworzenie nazwane obiekty znane jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="1f655-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="1f655-106">Nazwy zmiennych może zawierać znaku podkreślenia i znaków alfanumerycznych.</span><span class="sxs-lookup"><span data-stu-id="1f655-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="1f655-107">W przypadku użycia w programie PowerShell, zmienna jest zawsze określona za pomocą \$ znak następuje nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f655-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="1f655-108">Tworzenie zmiennej</span><span class="sxs-lookup"><span data-stu-id="1f655-108">Creating a variable</span></span>

<span data-ttu-id="1f655-109">Można utworzyć zmienną, wpisując prawidłową nazwę zmiennej:</span><span class="sxs-lookup"><span data-stu-id="1f655-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="1f655-110">W tym przykładzie zwraca żadnego wyniku, ponieważ `$loc` nie ma wartości.</span><span class="sxs-lookup"><span data-stu-id="1f655-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="1f655-111">Można utworzyć zmienną i przypisać jej wartości w tym samym kroku.</span><span class="sxs-lookup"><span data-stu-id="1f655-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="1f655-112">Programu PowerShell tworzy zmienną tylko, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1f655-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="1f655-113">W przeciwnym razie przypisuje określoną wartość do istniejącej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f655-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="1f655-114">Poniższy przykład zapisuje bieżącej lokalizacji w zmiennej `$loc`:</span><span class="sxs-lookup"><span data-stu-id="1f655-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="1f655-115">Program PowerShell nie wyświetla danych wyjściowych po wpisaniu tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f655-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="1f655-116">Program PowerShell wysyła dane wyjściowe "Get-Location" `$loc`.</span><span class="sxs-lookup"><span data-stu-id="1f655-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="1f655-117">W programie PowerShell, który nie jest przypisany lub przekierowanie przesyłane do ekranu.</span><span class="sxs-lookup"><span data-stu-id="1f655-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="1f655-118">Wpisywanie `$loc` pokazuje bieżącą lokalizację:</span><span class="sxs-lookup"><span data-stu-id="1f655-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="1f655-119">Możesz użyć `Get-Member` do wyświetlania informacji o zawartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="1f655-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="1f655-120">`Get-Member` Pokazuje, że `$loc` jest **PATHINFO zawiera** obiektu, podobnie jak dane wyjściowe z `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="1f655-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="1f655-121">Manipulowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="1f655-121">Manipulating variables</span></span>

<span data-ttu-id="1f655-122">Program PowerShell udostępnia kilka poleceń do manipulowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="1f655-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="1f655-123">Aby zobaczyć pełną listę w postaci do odczytu, należy wpisać:</span><span class="sxs-lookup"><span data-stu-id="1f655-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="1f655-124">Program PowerShell tworzy również kilka zmiennych zdefiniowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="1f655-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="1f655-125">Możesz użyć `Remove-Variable` polecenie cmdlet do usuwania zmiennych, które nie są kontrolowane przez program PowerShell z bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="1f655-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="1f655-126">Wpisz następujące polecenie, aby wyczyścić wszystkie zmienne:</span><span class="sxs-lookup"><span data-stu-id="1f655-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="1f655-127">Po uruchomieniu poprzednie polecenie `Get-Variable` polecenie cmdlet pokazuje zmiennych systemowych programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f655-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="1f655-128">Programu PowerShell tworzy dysk zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f655-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="1f655-129">Skorzystaj z następującego przykładu, aby wyświetlić wszystkie zmienne programu PowerShell przy użyciu zmiennej dysku:</span><span class="sxs-lookup"><span data-stu-id="1f655-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="1f655-130">Używanie zmiennych cmd.exe</span><span class="sxs-lookup"><span data-stu-id="1f655-130">Using cmd.exe variables</span></span>

<span data-ttu-id="1f655-131">Program PowerShell można użyć tego samego zmiennych środowiskowych dostępnych do dowolnego procesu Windows łącznie **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="1f655-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="1f655-132">Te zmienne są udostępniane za pośrednictwem dysku o nazwie `env:`.</span><span class="sxs-lookup"><span data-stu-id="1f655-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="1f655-133">Te zmienne można wyświetlić, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="1f655-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="1f655-134">Standardowa `*-Variable` poleceń cmdlet nie są zaprojektowane do pracy ze zmiennymi środowiskowymi.</span><span class="sxs-lookup"><span data-stu-id="1f655-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="1f655-135">Zmienne środowiskowe są dostępne przy użyciu `env:` prefiksu dysku.</span><span class="sxs-lookup"><span data-stu-id="1f655-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="1f655-136">Na przykład **% SystemRoot %** zmienną **cmd.exe** zawiera nazwę katalogu głównego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1f655-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="1f655-137">W programie PowerShell użyj `$env:SystemRoot` dostępu do tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="1f655-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="1f655-138">Można również tworzyć i modyfikować zmiennych środowiskowych z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f655-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="1f655-139">Zmienne środowiskowe w programie PowerShell, wykonaj te same zasady stosowania zmienne środowiskowe używane w innym miejscu w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="1f655-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="1f655-140">Poniższy przykład tworzy nową zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="1f655-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="1f655-141">Nie jest to wymagane, ale jest typowe dla nazwy zmiennych środowiskowych użyć wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="1f655-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
