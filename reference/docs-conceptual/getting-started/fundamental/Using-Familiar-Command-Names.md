---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Używanie znanych nazw poleceń
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 08402aa5b959711c150fff89aa6747b6b43f8aa8
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134087"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="072a3-103">Używanie znanych nazw poleceń</span><span class="sxs-lookup"><span data-stu-id="072a3-103">Using familiar command names</span></span>

<span data-ttu-id="072a3-104">Program PowerShell obsługuje aliasów do odwoływania się do polecenia przy użyciu alternatywnych nazw.</span><span class="sxs-lookup"><span data-stu-id="072a3-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="072a3-105">Tworzenie aliasów umożliwia użytkownikom ze środowiskiem, w innych powłoki, aby używać typowych nazw poleceń, które już znasz dla podobnych działań w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="072a3-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="072a3-106">Aliasów kojarzy nazwę przy użyciu innego polecenia.</span><span class="sxs-lookup"><span data-stu-id="072a3-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="072a3-107">Na przykład programu PowerShell ma funkcji o nazwie wewnętrznej `Clear-Host` , czyści okno danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="072a3-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="072a3-108">Można wpisać `cls` lub `clear` aliasu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="072a3-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="072a3-109">Program PowerShell interpretuje te aliasy i uruchamia `Clear-Host` funkcji.</span><span class="sxs-lookup"><span data-stu-id="072a3-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="072a3-110">Ta funkcja pozwala użytkownikom, aby dowiedzieć się, programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="072a3-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="072a3-111">Po pierwsze większość użytkowników Cmd.exe i Unix ma duże dostępnych poleceń, które znanych według nazw użytkowników.</span><span class="sxs-lookup"><span data-stu-id="072a3-111">First, most Cmd.exe and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="072a3-112">Odpowiedniki w programie PowerShell nie może utworzyć takie same wyniki.</span><span class="sxs-lookup"><span data-stu-id="072a3-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="072a3-113">Wyniki są jednak Zamknij wystarczająco dużo, które użytkownicy mogą działać bez znajomości nazwa polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="072a3-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="072a3-114">"Finger pamięci" jest inny główne źródło Rozczarowanie podczas nauki nowych powłoki poleceń.</span><span class="sxs-lookup"><span data-stu-id="072a3-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="072a3-115">Jeśli używano Cmd.exe przez wiele lat, może być reflexively wpisz `cls` polecenie, aby wyczyścić ekran.</span><span class="sxs-lookup"><span data-stu-id="072a3-115">If you have used Cmd.exe for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="072a3-116">Bez alias `Clear-Host`, otrzymujesz komunikat o błędzie i nie będą wiedzieli, co należy zrobić, aby wyczyścić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="072a3-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="072a3-117">Na poniższej liście przedstawiono niektóre typowe polecenia Cmd.exe i Unix, które są dostępne w programie PowerShell:</span><span class="sxs-lookup"><span data-stu-id="072a3-117">The following list shows a few of the common Cmd.exe and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="072a3-118">CAT</span><span class="sxs-lookup"><span data-stu-id="072a3-118">cat</span></span>|<span data-ttu-id="072a3-119">dir</span><span class="sxs-lookup"><span data-stu-id="072a3-119">dir</span></span>|<span data-ttu-id="072a3-120">instalacji</span><span class="sxs-lookup"><span data-stu-id="072a3-120">mount</span></span>|<span data-ttu-id="072a3-121">Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="072a3-121">rm</span></span>|
|<span data-ttu-id="072a3-122">ciągłe dostarczanie</span><span class="sxs-lookup"><span data-stu-id="072a3-122">cd</span></span>|<span data-ttu-id="072a3-123">Echo</span><span class="sxs-lookup"><span data-stu-id="072a3-123">echo</span></span>|<span data-ttu-id="072a3-124">Przenieś</span><span class="sxs-lookup"><span data-stu-id="072a3-124">move</span></span>|<span data-ttu-id="072a3-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="072a3-125">rmdir</span></span>|
|<span data-ttu-id="072a3-126">chdir</span><span class="sxs-lookup"><span data-stu-id="072a3-126">chdir</span></span>|<span data-ttu-id="072a3-127">Wymazywanie</span><span class="sxs-lookup"><span data-stu-id="072a3-127">erase</span></span>|<span data-ttu-id="072a3-128">popd</span><span class="sxs-lookup"><span data-stu-id="072a3-128">popd</span></span>|<span data-ttu-id="072a3-129">stan uśpienia</span><span class="sxs-lookup"><span data-stu-id="072a3-129">sleep</span></span>|
|<span data-ttu-id="072a3-130">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="072a3-130">clear</span></span>|<span data-ttu-id="072a3-131">GODZ.</span><span class="sxs-lookup"><span data-stu-id="072a3-131">h</span></span>|<span data-ttu-id="072a3-132">PS</span><span class="sxs-lookup"><span data-stu-id="072a3-132">ps</span></span>|<span data-ttu-id="072a3-133">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="072a3-133">sort</span></span>|
|<span data-ttu-id="072a3-134">ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="072a3-134">cls</span></span>|<span data-ttu-id="072a3-135">Historia</span><span class="sxs-lookup"><span data-stu-id="072a3-135">history</span></span>|<span data-ttu-id="072a3-136">pushd</span><span class="sxs-lookup"><span data-stu-id="072a3-136">pushd</span></span>|<span data-ttu-id="072a3-137">Program Tee</span><span class="sxs-lookup"><span data-stu-id="072a3-137">tee</span></span>|
|<span data-ttu-id="072a3-138">Kopiuj</span><span class="sxs-lookup"><span data-stu-id="072a3-138">copy</span></span>|<span data-ttu-id="072a3-139">Zakończ</span><span class="sxs-lookup"><span data-stu-id="072a3-139">kill</span></span>|<span data-ttu-id="072a3-140">pwd</span><span class="sxs-lookup"><span data-stu-id="072a3-140">pwd</span></span>|<span data-ttu-id="072a3-141">typ</span><span class="sxs-lookup"><span data-stu-id="072a3-141">type</span></span>|
|<span data-ttu-id="072a3-142">del</span><span class="sxs-lookup"><span data-stu-id="072a3-142">del</span></span>|<span data-ttu-id="072a3-143">LP</span><span class="sxs-lookup"><span data-stu-id="072a3-143">lp</span></span>|<span data-ttu-id="072a3-144">r</span><span class="sxs-lookup"><span data-stu-id="072a3-144">r</span></span>|<span data-ttu-id="072a3-145">zapis</span><span class="sxs-lookup"><span data-stu-id="072a3-145">write</span></span>|
|<span data-ttu-id="072a3-146">diff</span><span class="sxs-lookup"><span data-stu-id="072a3-146">diff</span></span>|<span data-ttu-id="072a3-147">Ls</span><span class="sxs-lookup"><span data-stu-id="072a3-147">ls</span></span>|<span data-ttu-id="072a3-148">ren</span><span class="sxs-lookup"><span data-stu-id="072a3-148">ren</span></span>||

<span data-ttu-id="072a3-149">`Get-Alias` Polecenie cmdlet Pokazuje rzeczywistą nazwą polecenia programu PowerShell natywnych skojarzonych z aliasem.</span><span class="sxs-lookup"><span data-stu-id="072a3-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="072a3-150">Interpretowanie standardowa aliasów</span><span class="sxs-lookup"><span data-stu-id="072a3-150">Interpreting standard aliases</span></span>

<span data-ttu-id="072a3-151">Aliasy możemy opisanego w poprzedniej zostały zaprojektowane dla nazwy — zgodność z innymi powłoki poleceń.</span><span class="sxs-lookup"><span data-stu-id="072a3-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="072a3-152">Większość aliasów utworzone w programie PowerShell są przeznaczone do skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="072a3-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="072a3-153">Krótsze nazwy są łatwiejsze do typu, ale są trudne do odczytania, jeśli nie znasz odwołują się.</span><span class="sxs-lookup"><span data-stu-id="072a3-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="072a3-154">Aliasy środowiska PowerShell próbować naruszyć między przejrzystości i skrócenia programu.</span><span class="sxs-lookup"><span data-stu-id="072a3-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="072a3-155">PowerShell używa standardowy zestaw aliasy rzeczowniki typowe i zleceń.</span><span class="sxs-lookup"><span data-stu-id="072a3-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="072a3-156">Przykład skrótów:</span><span class="sxs-lookup"><span data-stu-id="072a3-156">Example abbreviations:</span></span>

| <span data-ttu-id="072a3-157">Rzeczownik lub zlecenie</span><span class="sxs-lookup"><span data-stu-id="072a3-157">Noun or Verb</span></span> | <span data-ttu-id="072a3-158">Skrót</span><span class="sxs-lookup"><span data-stu-id="072a3-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="072a3-159">Pobranie</span><span class="sxs-lookup"><span data-stu-id="072a3-159">Get</span></span>          | <span data-ttu-id="072a3-160">G</span><span class="sxs-lookup"><span data-stu-id="072a3-160">g</span></span>            |
| <span data-ttu-id="072a3-161">Ustaw</span><span class="sxs-lookup"><span data-stu-id="072a3-161">Set</span></span>          | <span data-ttu-id="072a3-162">s</span><span class="sxs-lookup"><span data-stu-id="072a3-162">s</span></span>            |
| <span data-ttu-id="072a3-163">Element</span><span class="sxs-lookup"><span data-stu-id="072a3-163">Item</span></span>         | <span data-ttu-id="072a3-164">i</span><span class="sxs-lookup"><span data-stu-id="072a3-164">i</span></span>            |
| <span data-ttu-id="072a3-165">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="072a3-165">Location</span></span>     | <span data-ttu-id="072a3-166">l</span><span class="sxs-lookup"><span data-stu-id="072a3-166">l</span></span>            |
| <span data-ttu-id="072a3-167">Polecenie</span><span class="sxs-lookup"><span data-stu-id="072a3-167">Command</span></span>      | <span data-ttu-id="072a3-168">Menedżer certyfikatów</span><span class="sxs-lookup"><span data-stu-id="072a3-168">cm</span></span>           |
| <span data-ttu-id="072a3-169">Alias</span><span class="sxs-lookup"><span data-stu-id="072a3-169">Alias</span></span>        | <span data-ttu-id="072a3-170">Al</span><span class="sxs-lookup"><span data-stu-id="072a3-170">al</span></span>           |

<span data-ttu-id="072a3-171">Te aliasy są zrozumiałe, gdy wiadomo, skrócone nazwy.</span><span class="sxs-lookup"><span data-stu-id="072a3-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="072a3-172">Nazwa polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="072a3-172">Cmdlet name</span></span>    | <span data-ttu-id="072a3-173">Alias</span><span class="sxs-lookup"><span data-stu-id="072a3-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="072a3-174">GI</span><span class="sxs-lookup"><span data-stu-id="072a3-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="072a3-175">SI</span><span class="sxs-lookup"><span data-stu-id="072a3-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="072a3-176">GL</span><span class="sxs-lookup"><span data-stu-id="072a3-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="072a3-177">SL</span><span class="sxs-lookup"><span data-stu-id="072a3-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="072a3-178">usługi gcm</span><span class="sxs-lookup"><span data-stu-id="072a3-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="072a3-179">GAL</span><span class="sxs-lookup"><span data-stu-id="072a3-179">gal</span></span>   |

<span data-ttu-id="072a3-180">Po zapoznaniu się z programu PowerShell aliasów się, jest łatwe do odgadnięcia, **sal** alias odwołuje się do `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="072a3-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="072a3-181">Tworzenie nowego aliasów</span><span class="sxs-lookup"><span data-stu-id="072a3-181">Creating new aliases</span></span>

<span data-ttu-id="072a3-182">Możesz utworzyć własne aliasy, za pomocą `Set-Alias` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="072a3-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="072a3-183">Na przykład poniższe instrukcje tworzenia aliasów standardowe polecenia cmdlet omówionych wcześniej:</span><span class="sxs-lookup"><span data-stu-id="072a3-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="072a3-184">Wewnętrznie programu PowerShell używa podobnych poleceń podczas uruchamiania, ale te aliasy nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="072a3-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="072a3-185">Jeśli spróbujesz wykonać jedną z tych poleceń, otrzymasz błąd z informacją, że alias nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="072a3-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="072a3-186">Przykład:</span><span class="sxs-lookup"><span data-stu-id="072a3-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```