---
title: Co nowego w programie PowerShell Core 6.2
description: Nowe funkcje i zmiany w programie PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750036"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="58f50-103">Co nowego w programie PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="58f50-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="58f50-104">Poniżej przedstawiono niektóre główne nowe funkcje i zmiany, które zostały wprowadzone w programie PowerShell Core 6.2 wyboru.</span><span class="sxs-lookup"><span data-stu-id="58f50-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="58f50-105">Istnieje również **tonach** "nudnych dostępu", które ułatwiają programu PowerShell, szybsze i bardziej stabilne (plus partii i wiele poprawek)!</span><span class="sxs-lookup"><span data-stu-id="58f50-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="58f50-106">Aby uzyskać pełną listę zmian, zapoznaj się z naszym [dziennika zmian w witrynie GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="58f50-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="58f50-107">I gdy czy powinniśmy zwołać kilka nazw poniżej, aby [wszystkie uczestnicy społeczności](https://github.com/PowerShell/PowerShell/graphs/contributors) , wprowadzonych w tej wersji możliwe.</span><span class="sxs-lookup"><span data-stu-id="58f50-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="58f50-108">Aparat aktualizacji i poprawek</span><span class="sxs-lookup"><span data-stu-id="58f50-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="58f50-109">Dodawać komunikaty ostrzegawcze polecenie cmdlet Włącza/wyłącza komunikacji zdalnej programu PowerShell ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="58f50-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="58f50-110">Poprawka `FormatTable` regresji deserializacji zdalnego ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="58f50-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="58f50-111">Aktualizuj opartego na zadaniach `async` interfejsów API dodane do programu PowerShell, aby zwrócić obiekt zadania bezpośrednio ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="58f50-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="58f50-112">Dodaj 5 `InvokeAsync` przeciążenia i `StopAsync` do `PowerShell` typu ([#8056][]) (Dziękuję @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="58f50-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="58f50-113">Ogólne polecenia Cmdlet aktualizacje i poprawki</span><span class="sxs-lookup"><span data-stu-id="58f50-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="58f50-114">Włącz `SecureString` poleceń cmdlet dla innych niż Windows, przechowując zwykły tekst ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="58f50-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="58f50-115">Dodaj komunikat przestarzałe `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="58f50-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="58f50-116">Napraw `Restart-Computer` pracować nad `localhost` gdy WinRM nie jest obecny ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="58f50-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="58f50-117">Wprowadź `Start-Job` zgłaszają błąd powodujący przerwanie, gdy jest hostowany program PowerShell ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="58f50-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="58f50-118">Wersja aktualizacji `PowerShell.Native` i hosting testów ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="58f50-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="58f50-119">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="58f50-119">Breaking Changes</span></span>

<span data-ttu-id="58f50-120">Napraw - NoEnumerate zachowanie w Write-Output, aby były zgodne z programu Windows PowerShell ([#9069][]) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="58f50-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
