---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Używanie zmiennych na potrzeby przechowywania obiektów
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 3168b64039a601857f9c684108de5770f88329e3
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134062"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="aa795-103">Używanie zmiennych do przechowywania obiektów</span><span class="sxs-lookup"><span data-stu-id="aa795-103">Using variables to store objects</span></span>

<span data-ttu-id="aa795-104">Program PowerShell działa z obiektami.</span><span class="sxs-lookup"><span data-stu-id="aa795-104">PowerShell works with objects.</span></span> <span data-ttu-id="aa795-105">Program PowerShell umożliwia tworzenie nazwane obiekty znane jako zmienne.</span><span class="sxs-lookup"><span data-stu-id="aa795-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="aa795-106">Nazwy zmiennych może zawierać żadnych znaków alfanumerycznych możesz znaki podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="aa795-106">Variables names can include the underscore character can any alphanumeric characters.</span></span> <span data-ttu-id="aa795-107">W przypadku użycia w programie PowerShell, zmienna jest zawsze określona za pomocą \$ znak następuje nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="aa795-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="aa795-108">Tworzenie zmiennej</span><span class="sxs-lookup"><span data-stu-id="aa795-108">Creating a variable</span></span>

<span data-ttu-id="aa795-109">Można utworzyć zmienną, wpisując prawidłową nazwę zmiennej:</span><span class="sxs-lookup"><span data-stu-id="aa795-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="aa795-110">W tym przykładzie zwraca żadnego wyniku, ponieważ `$loc` nie ma wartości.</span><span class="sxs-lookup"><span data-stu-id="aa795-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="aa795-111">Można utworzyć zmienną i przypisać jej wartości w tym samym kroku.</span><span class="sxs-lookup"><span data-stu-id="aa795-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="aa795-112">Programu PowerShell tworzy zmienną tylko, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="aa795-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="aa795-113">W przeciwnym razie przypisuje określoną wartość do istniejącej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="aa795-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="aa795-114">Poniższy przykład zapisuje bieżącej lokalizacji w zmiennej `$loc`:</span><span class="sxs-lookup"><span data-stu-id="aa795-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="aa795-115">Program PowerShell nie wyświetla danych wyjściowych po wpisaniu tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="aa795-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="aa795-116">Program PowerShell wysyła dane wyjściowe "Get-Location" `$loc`.</span><span class="sxs-lookup"><span data-stu-id="aa795-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="aa795-117">W programie PowerShell, który nie jest przypisany lub przekierowanie przesyłane do ekranu.</span><span class="sxs-lookup"><span data-stu-id="aa795-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="aa795-118">Wpisywanie `$loc` pokazuje bieżącą lokalizację:</span><span class="sxs-lookup"><span data-stu-id="aa795-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="aa795-119">Możesz użyć `Get-Member` do wyświetlania informacji o zawartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="aa795-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="aa795-120">`Get-Member` Pokazuje, że `$loc` jest **PATHINFO zawiera** obiektu, podobnie jak dane wyjściowe z `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="aa795-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

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

## <a name="manipulating-variables"></a><span data-ttu-id="aa795-121">Manipulowanie zmiennych</span><span class="sxs-lookup"><span data-stu-id="aa795-121">Manipulating variables</span></span>

<span data-ttu-id="aa795-122">Program PowerShell udostępnia kilka poleceń do manipulowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="aa795-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="aa795-123">Aby zobaczyć pełną listę w postaci do odczytu, należy wpisać:</span><span class="sxs-lookup"><span data-stu-id="aa795-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="aa795-124">Program PowerShell tworzy również kilka zmiennych zdefiniowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="aa795-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="aa795-125">Możesz użyć `Remove-Variable` polecenie cmdlet do usuwania zmiennych, które nie są kontrolowane przez program PowerShell z bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="aa795-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="aa795-126">Wpisz następujące polecenie, aby wyczyścić wszystkie zmienne:</span><span class="sxs-lookup"><span data-stu-id="aa795-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="aa795-127">Po uruchomieniu poprzednie polecenie `Get-Variable` polecenie cmdlet pokazuje zmiennych systemowych programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa795-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="aa795-128">Programu PowerShell tworzy dysk zmiennej.</span><span class="sxs-lookup"><span data-stu-id="aa795-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="aa795-129">Skorzystaj z następującego przykładu, aby wyświetlić wszystkie zmienne programu PowerShell przy użyciu zmiennej dysku:</span><span class="sxs-lookup"><span data-stu-id="aa795-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="aa795-130">Używanie zmiennych Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="aa795-130">Using Cmd.exe variables</span></span>

<span data-ttu-id="aa795-131">Program PowerShell można użyć tego samego zmiennych środowiskowych dostępnych do dowolnego procesu Windows, w tym Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="aa795-131">PowerShell can use the same environment variables available to any Windows process, including Cmd.exe.</span></span> <span data-ttu-id="aa795-132">Te zmienne są udostępniane za pośrednictwem dysku o nazwie `env:`.</span><span class="sxs-lookup"><span data-stu-id="aa795-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="aa795-133">Te zmienne można wyświetlić, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="aa795-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="aa795-134">Standardowa `*-Variable` poleceń cmdlet nie są zaprojektowane do pracy ze zmiennymi środowiskowymi.</span><span class="sxs-lookup"><span data-stu-id="aa795-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="aa795-135">Zmienne środowiskowe są dostępne przy użyciu `env:` prefiksu dysku.</span><span class="sxs-lookup"><span data-stu-id="aa795-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="aa795-136">Na przykład **% SystemRoot %** zmiennej w Cmd.exe zawiera nazwę katalogu głównego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="aa795-136">For example, the **%SystemRoot%** variable in Cmd.exe contains the operating system's root directory name.</span></span> <span data-ttu-id="aa795-137">W programie PowerShell użyj `$env:SystemRoot` dostępu do tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="aa795-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="aa795-138">Można również tworzyć i modyfikować zmiennych środowiskowych z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa795-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="aa795-139">Zmienne środowiskowe w programie PowerShell, wykonaj te same zasady stosowania zmienne środowiskowe używane w innym miejscu w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="aa795-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="aa795-140">Poniższy przykład tworzy nową zmienną środowiskową:</span><span class="sxs-lookup"><span data-stu-id="aa795-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="aa795-141">Chociaż nie jest wymagane, czy jest typowe dla nazwy zmiennych środowiskowych użyć wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="aa795-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>