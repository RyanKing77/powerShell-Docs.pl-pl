# <a name="microsoft-open-source-code-of-conduct"></a>Kodeks postępowania firmy Microsoft dla oprogramowania typu open source

W tym projekcie jest używany [Kodeks postępowania firmy Microsoft dla oprogramowania typu open source](https://opensource.microsoft.com/codeofconduct/).
Aby uzyskać więcej informacji, zobacz [Kodeks postępowania — Często zadawane pytania](https://opensource.microsoft.com/codeofconduct/faq/) lub napisz wiadomość e-mail na adres [opencode@microsoft.com](mailto:opencode@microsoft.com) z dodatkowymi pytaniami lub komentarzami.

[![Status kompilacji:](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>Dokumentacja programu PowerShell

Witamy w repozytorium dokumentów programu PowerShell, mieszkalnictwo oficjalnej dokumentacji programu PowerShell.

## <a name="repository-structure"></a>Struktura repozytorium

Następujące foldery najwyższego poziomu, w tym repozytorium zawiera między zestawami dokumentów, które są publikowane w [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/Developer/](https://docs.microsoft.com/powershell/developer/) to miejsce, w którym został przyszłych w dokumentacji zestawu SDK programu PowerShell
  - Jesteśmy w trakcie migracji tej zawartości z witryny MSDN
- [/DSC/](https://docs.microsoft.com/powershell/dsc/) dotyczy funkcji Desired State Configuration
- [/Gallery/](https://docs.microsoft.com/powershell/gallery) dotyczy [galerii programu PowerShell](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) dotyczy funkcji Just Enough Administration
- [/Reference/](https://docs.microsoft.com/powershell/scripting/) jest przeznaczony dla tematów pojęciowych programu PowerShell i odwołania do modułu w wersjach 3.0, 4.0, 5.0, 5.1 i 6.0
  - Ta zawartość jest również źródło zawartości pomocy, pobierane przez `Get-Help` polecenia cmdlet
- [/WMF](https://docs.microsoft.com/powershell/wmf/readme) zawiera informacje o wersji dla Windows Management Framework, pakiet używane do rozpowszechniania nowe wersje programu PowerShell do poprzednich wersji systemu Windows.

## <a name="contributing"></a>Współtworzenie

Firma Microsoft aktywnie scalanie wkład w repozytorium za pomocą [żądania ściągnięcia](https://help.github.com/articles/using-pull-requests/) do *przemieszczania* gałęzi.
Należy pamiętać, że zanim prześlesz żądanie ściągnięcia należy [podpisania umowy licencyjnej udziału](https://cla.microsoft.com/) aby upewnić się, że community jest bezpłatne korzystanie z materiałów przesłanych.

Aby uzyskać więcej informacji na temat przekazywania, przeczytaj nasze [przewodnika dla współautorów](CONTRIBUTING.md).
Przewodnik współautora zawiera szczegółowe informacje dotyczące sposobu współtworzenia dokumentacji, sugerowane narzędzi i stylu i formatowania wymagania.
Użyj szablonów problemu i żądania ściągnięcia do zapewnienia dokumentacji spójny między wersjami.

## <a name="licenses"></a>Licencje

Istnieją dwa pliki licencji dla tego projektu.
Licencja MIT dotyczy kod zawarty w tym repozytorium.
Licencja Creative Commons ma zastosowanie do dokumentacji.