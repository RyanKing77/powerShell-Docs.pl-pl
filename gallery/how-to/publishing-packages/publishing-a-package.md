---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Tworzenie i publikowanie elementu
ms.openlocfilehash: 0e0f871b5d43508735e396224fdfd1a29b1e91c0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055482"
---
# <a name="creating-and-publishing-an-item"></a>Tworzenie i publikowanie elementu

Galerii programu PowerShell jest używana do publikowania i udostępniania stabilne modułów programu PowerShell, skryptów i zasobów DSC z szerszego społeczność użytkowników programu PowerShell.

W tym artykule opisano mechanics i ważnych kroków przygotowania skryptu lub moduł, i publikując ją w galerii programu PowerShell. Zdecydowanie zaleca przejrzenie [wskazówki dotyczące publikowania](../../concepts/publishing-guidelines.md) zrozumienie, jak upewnić się, że elementy publikowania będzie bardziej powszechnie akceptowane przez użytkowników z galerii programu PowerShell.

Minimalne wymagania, aby opublikować element galerii programu PowerShell są:

- Mieć konto galerii programu PowerShell i skojarzony klucz interfejsu API
- Upewnij się, że wymagane metadane znajduje się w elemencie usługi
- Upewnij się, że Twoje elementu jest gotowa do opublikowania za pomocą narzędzi weryfikacji wstępnej
- Publikowanie elementu w galerii programu PowerShell przy użyciu polecenia Publish-Module i Publish-Script
- Odpowiadanie na pytań lub wątpliwości dotyczących przedmiot

Galeria programu PowerShell akceptuje modułów programu PowerShell i skryptów programu PowerShell. Nazywamy skryptów, mamy na myśli skrypt programu PowerShell, który jest pojedynczy plik, a nie jest częścią większej modułu.

## <a name="powershell-gallery-account-and-api-key"></a>Galeria programu PowerShell konta i klucz interfejsu API

Zobacz [Tworzenie konta galerii programu PowerShell](/powershell/gallery/how-to/publishing-packages/creating-an-account) dotyczące sposobu konfigurowania konta galerii programu PowerShell.

Po utworzeniu konta możesz uzyskać klucz interfejsu API niezbędnych do publikowania elementu. Po zalogowaniu się przy użyciu konta, nazwy użytkownika pojawi się w górnej części stron galerii programu PowerShell, a nie rejestru. Kliknięcie nazwy użytkownika spowoduje przejście do strony Moje konto, gdzie można znaleźć klucza interfejsu API.

Uwaga: Klucz interfejsu API muszą być traktowane jako bezpieczne jako login i hasło.
Przy użyciu tego klucza, nikogo, można zaktualizować dowolny element, którego jesteś właścicielem w galerii programu PowerShell.
Zalecamy zaktualizowanie klucz regularnie, co można zrobić za pomocą resetowania klucza na stronie Moje konto.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Wymagane metadane dla elementów opublikowanych w galerii programu PowerShell

Galeria programu PowerShell informacje użytkownikom galerii z pola metadanych, które są zawarte w manifeście skryptu lub modułu. Tworzenie lub modyfikowanie elementów dla publikacji w galerii programu PowerShell ma niewielki zestaw wymagań dotyczących informacji dostarczonych w manifeście elementu.
Zdecydowanie zaleca przejrzenie sekcji metadanych elementu [wskazówki dotyczące publikowania](../../concepts/publishing-guidelines.md) Aby dowiedzieć się, jak zapewnić informacje o najlepszych użytkowników z elementami.

[New ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) i [New ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) poleceń cmdlet spowoduje utworzenie szablonu manifestu, przy użyciu symboli zastępczych dla wszystkich elementów manifestu.

Zarówno manifesty ma dwie sekcje, które są ważne w przypadku publikowania obszaru danych klucza głównego i PSData PrivateData. Danymi klucza podstawowego w manifeście modułu programu PowerShell jest wszystko poza sekcję PrivateData. Zestaw kluczy podstawowych jest powiązany z wersji programu PowerShell w użyciu i niezdefiniowane nie są obsługiwane. PrivateData obsługuje dodawanie nowych kluczy, więc elementy, które są określone w galerii programu PowerShell są w PSData.


Manifest elementów, które są dla Ciebie najważniejsze do wypełnienia dla elementu, który publikowanie w galerii programu PowerShell są:

- Skrypt lub modułu nazwa — te są pobierane z nazwy. PS1, aby uzyskać skrypt lub. PSD1 dla modułu.
- Wersja — jest wymagany klucz podstawowy, format powinien być zgodny z wytycznymi SemVer. Aby uzyskać szczegółowe informacje, zobacz najważniejsze wskazówki.
- Autor - to jest wymagany klucz podstawowy i zawiera nazwę, która ma zostać skojarzony z elementem.
Zobacz twórcy i właściciele poniżej.
- Opis — jest wymagany klucz podstawowy używany do krótko opisano, co robi ten element, a także wymagania dotyczące korzystania z niego
- ProjectURI — jest to zdecydowanie zalecane pole identyfikatora URI w PSData, która zawiera link do repozytorium Github lub podobne lokalizacji, w których wykonują rozwoju w elemencie
- Tagi — silne zalecane jest tagowanie pakietu oparte na zgodności z elementami Psedition i platform. Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące publikowania](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Elementy twórcy i właściciele galerii programu PowerShell to pojęcia pokrewne, ale nie zawsze być zgodna. Właścicielami elementów znajdują się użytkownicy z kontami w galerii programu PowerShell, które ma uprawnienia do zachowania elementu. Może istnieć wiele właścicieli, które mogą aktualizować dowolnego elementu. Właściciel jest dostępna tylko z galerii programu PowerShell i zostaną utracone, jeśli element zostanie skopiowany z jednego systemu do innego. Autor jest ciąg, który ma wbudowaną manifestu dane, dzięki czemu zawsze jest częścią elementu. Zalecenia dotyczące elementów z produktów firmy Microsoft są:

- Mieć wielu właścicieli z co najmniej jednym jest nazwa zespołu, który tworzy element
- Autor nazwa dobrze znanych team (na przykład zespół zestawu SDK platformy Azure) lub Microsoft Corporation


## <a name="pre-validate-your-item"></a>Wstępna weryfikacja przedmiot

Istnieje kilka narzędzi, które są potrzebne w celu uruchomienia kodu przed opublikowaniem z elementu w galerii programu PowerShell:

- [Analizator skrypt programu PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), która znajduje się w galerii programu PowerShell
- Dla modułów, ModuleManifest testu, który jest częścią programu PowerShell
- W przypadku skryptów ScriptFileInfo testu, który jest dostarczany za pomocą programu PowerShell Get

[Analizator skrypt programu PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) jest narzędzie do analizy kodu statycznego, które będą skanować swój kod, aby upewnić się, że spełnia PowerShell podstawowe wytyczne dotyczące kodowania. To narzędzie będzie identyfikowała najczęstszych i najpoważniejszych problemów w kodzie i powinien być uruchamiany regularnie w czasie projektowania, aby pomóc Ci przedmiot gotowe do opublikowania. Analizator skrypt programu PowerShell udostępni listę problemy zidentyfikowane jako błędy, ostrzeżenia i informacje. Muszą być kierowane wszystkie błędy, przed opublikowaniem w galerii programu PowerShell. Ostrzeżenia, które wymagają przejrzenia i powinny być kierowane większość. Analizator skrypt programu PowerShell jest uruchamiany za każdym razem, gdy element jest opublikowane lub zaktualizowane w galerii programu PowerShell. Zespół operacyjny Galeria będzie kontaktować się z właścicielami elementów, aby usunąć błędy, które znajdują się.

Jeśli nie można odczytać informacji o manifeście w przedmiot przez infrastrukturę galerii programu PowerShell, nie można opublikować.
[Test ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) będzie przechwytywać typowe problemy, które mogłoby spowodować modułu nie będzie można używać podczas instalacji. Musi być uruchamiane dla każdego modułu, przed jej opublikowaniem w galerii programu PowerShell.

Podobnie [ScriptFileInfo testu](/powershell/module/PowerShellGet/test-scriptfileinfo) weryfikuje metadanych w skrypcie i muszą zostać uruchomione na każdy skrypt (opublikowanych oddzielonym od modułu) przed jej opublikowaniem w galerii programu PowerShell.


## <a name="publishing-items"></a>Publikowanie elementów

Należy użyć [Publish-Script](/powershell/module/PowerShellGet/publish-script) lub [Publish-Module](/powershell/module/PowerShellGet/publish-module) do publikowania elementów w galerii programu PowerShell. Te polecenia, które wymaga:

- Ścieżka do elementu, który będzie publikować. Dla modułu należy użyć folder wyznaczony dla modułu. W przypadku określenia folderu, który zawiera wiele wersji tego samego modułu, należy określić RequiredVersion.
- Klucz interfejsu API Nuget. Jest to klucz interfejsu API znajdujący się na stronie Moje konto w galerii programu PowerShell.

Większość innych opcji wiersza polecenia powinny być manifestu danych dla elementu, który jest publikowany, więc nie należy je określić w poleceniu.

Aby uniknąć błędów, zalecane jest, spróbuj poleceń przy użyciu - WhatIf-Verbose, przed opublikowaniem. Spowoduje to zapisanie znaczną ilość czasu od momentu za każdym razem, gdy opublikujesz w galerii programu PowerShell, należy zaktualizować numer wersji w sekcji manifestu elementu.

Przykładami mogą być następujące:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -WhatIf -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -WhatIf -Verbose`

Uważnie przejrzyj dane wyjściowe, a Jeśli widzisz nie ostrzeżeń ani błędów, powtórz polecenie bez - WhatIf.

Wszystkie elementy, które są publikowane w galerii programu PowerShell ma zostać przeprowadzone skanowanie w poszukiwaniu wirusów i będą analizowane za pomocą analizatora skryptu programu PowerShell. Wszelkie problemy, które pojawiły się w tym czasie zostanie odesłana do wydawcy, do rozpoznania.

Po opublikowaniu elementu w galerii programu PowerShell należy do obserwacji opinie na temat Twojego towaru.

- Upewnij się, można monitorować adres e-mail skojarzony z kontem, używany do publikowania. Użytkownicy i zespół operacyjny galerii programu PowerShell zapewni opinii za pośrednictwem tego konta, takie jak problemy z PSSA lub skanowanie antywirusowe. Jeśli konto e-mail jest nieprawidłowy lub w przypadku poważnych problemów są zgłaszane do konta i po lewej stronie nierozpoznanych przez długi czas, elementy mogą być uznane za porzucone i zostanie usunięty z galerii programu PowerShell, zgodnie z opisem w naszym [warunki użytkowania](https://www.powershellgallery.com/policies/Terms).
- Firma Microsoft zaleca subskrybować komentarzy dla każdego elementu w galerii programu PowerShell, którą publikujesz. Dzięki temu można otrzymywać powiadomienia, gdy każda osoba komentarze dotyczące elementów w galerii programu PowerShell. Jest to opcjonalne, ponieważ wymaga ona, tworząc konto LiveFyre.
