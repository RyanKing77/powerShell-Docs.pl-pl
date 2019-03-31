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
# <a name="whats-new-in-powershell-core-62"></a>Co nowego w programie PowerShell Core 6.2

Poniżej przedstawiono niektóre główne nowe funkcje i zmiany, które zostały wprowadzone w programie PowerShell Core 6.2 wyboru.

Istnieje również **tonach** "nudnych dostępu", które ułatwiają programu PowerShell, szybsze i bardziej stabilne (plus partii i wiele poprawek)!
Aby uzyskać pełną listę zmian, zapoznaj się z naszym [dziennika zmian w witrynie GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

I gdy czy powinniśmy zwołać kilka nazw poniżej, aby [wszystkie uczestnicy społeczności](https://github.com/PowerShell/PowerShell/graphs/contributors) , wprowadzonych w tej wersji możliwe.

## <a name="engine-updates-and-fixes"></a>Aparat aktualizacji i poprawek

- Dodawać komunikaty ostrzegawcze polecenie cmdlet Włącza/wyłącza komunikacji zdalnej programu PowerShell ([#9203][])
- Poprawka `FormatTable` regresji deserializacji zdalnego ([#9116][])
- Aktualizuj opartego na zadaniach `async` interfejsów API dodane do programu PowerShell, aby zwrócić obiekt zadania bezpośrednio ([#9079][])
- Dodaj 5 `InvokeAsync` przeciążenia i `StopAsync` do `PowerShell` typu ([#8056][]) (Dziękuję @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Ogólne polecenia Cmdlet aktualizacje i poprawki

- Włącz `SecureString` poleceń cmdlet dla innych niż Windows, przechowując zwykły tekst ([#9199][])
- Dodaj komunikat przestarzałe `Send-MailMessage` ([#9178][])
- Napraw `Restart-Computer` pracować nad `localhost` gdy WinRM nie jest obecny ([#9160][])
- Wprowadź `Start-Job` zgłaszają błąd powodujący przerwanie, gdy jest hostowany program PowerShell ([#9128][])
- Wersja aktualizacji `PowerShell.Native` i hosting testów ([#8983][])

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Napraw - NoEnumerate zachowanie w Write-Output, aby były zgodne z programu Windows PowerShell ([#9069][]) (Dziękuję @vexx32!)

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
