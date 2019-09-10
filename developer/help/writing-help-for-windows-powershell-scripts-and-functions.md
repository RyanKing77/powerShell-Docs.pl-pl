---
title: Pisanie pomocy dotyczącej skryptów i funkcji programu PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848098"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Pisanie pomocy dotyczącej skryptów i funkcji programu PowerShell

Skrypty i funkcje programu PowerShell powinny być w pełni udokumentowane, gdy są udostępniane innym osobom.
Polecenie cmdlet wyświetla tematy pomocy dotyczące skryptów i funkcji w tym samym formacie, co wyświetla pomoc dla poleceń cmdlet, a wszystkie `Get-Help` parametry działają na temat tematów pomocy dotyczących skryptów i funkcji. `Get-Help`

Skrypty programu PowerShell mogą zawierać temat pomocy dotyczący skryptu i tematów pomocy dotyczących poszczególnych funkcji w skrypcie.
Funkcje udostępniane niezależnie od skryptów mogą zawierać własne tematy pomocy.

W tym dokumencie wyjaśniono format i poprawne rozmieszczenie tematów pomocy oraz zawarto wskazówki dotyczące zawartości.

## <a name="types-of-script-and-function-help"></a>Typy pomocy dotyczącej skryptów i funkcji

### <a name="comment-based-help"></a>Pomoc oparta na komentarzach
Temat pomocy, który opisuje skrypt lub funkcję, można zaimplementować jako zestaw komentarzy w skrypcie lub funkcji.
Podczas pisania pomocy opartej na komentarzach dla skryptu i dla funkcji w skrypcie należy zwrócić szczególną uwagę na reguły dotyczące umieszczania pomocy opartej na komentarzach.
Umieszczanie określa, czy `Get-Help` polecenie cmdlet kojarzy temat pomocy ze skryptem lub funkcją.
Aby uzyskać więcej informacji na temat pisania tematów pomocy opartych na komentarzach, zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Pomoc dotycząca poleceń opartych na języku XML
Temat pomocy, który opisuje skrypt lub funkcję, można zaimplementować w pliku XML, który używa schematu pomocy poleceń.
Aby skojarzyć skrypt lub funkcję z plikiem XML, użyj `ExternalHelp` słowa kluczowego komentarza, po którym następuje ścieżka i nazwa pliku XML.

Gdy słowo kluczowe `Get-Help` `ExternalHelp` comment jest obecne, ma wyższy priorytet niż pomoc oparta na komentarzach, nawet jeśli nie można znaleźć pliku pomocy, który pasuje do wartości słowa kluczowego. `ExternalHelp`

### <a name="online-help"></a>Pomoc online
Tematy pomocy można ogłosić w Internecie, a następnie bezpośrednio `Get-Help` otworzyć tematy.
Aby uzyskać więcej informacji na temat pisania tematów pomocy opartych na komentarzach, zobacz [Obsługa pomocy online](../module/supporting-online-help.md).

Nie ma żadnej ustanowionej metody pisania tematów koncepcyjnych ("informacje") dotyczących skryptów i funkcji.
Można jednak publikować tematy pojęciowe w Internecie listę tematów i ich adresów URL w sekcji Linki pokrewne w temacie pomocy poleceń.

## <a name="content-considerations-for-script-and-function-help"></a>Uwagi dotyczące zawartości dotyczącej pomocy dotyczącej skryptów i funkcji

- Jeśli piszesz krótki temat pomocy z tylko kilkoma dostępnymi sekcjami pomocy poleceń, pamiętaj, aby dołączyć jasne opisy parametrów skryptu lub funkcji. Należy również uwzględnić jedno lub dwa przykładowe polecenia w sekcji przykładów, nawet jeśli zdecydujesz się pominąć przykładowe opisy.

- We wszystkich opisach zapoznaj się z poleceniem jako skrypt lub funkcję. Te informacje pomagają użytkownikowi zrozumieć i zarządzać poleceniem.

  Na przykład w poniższym szczegółowym opisie opisano, że polecenie New-temat jest skryptem. Przypomina to użytkownikom, że potrzebują określić ścieżkę i pełną nazwę podczas ich uruchamiania.

  > "Skrypt nowego tematu tworzy pusty temat koncepcyjny dla każdej nazwy tematu w pliku wejściowym..."

  Poniżej przedstawiono szczegółowy opis stanów `Disable-PSRemoting` funkcji. Te informacje są szczególnie przydatne dla użytkowników, gdy sesja zawiera wiele poleceń o tej samej nazwie, a niektóre z nich mogą być ukryte przez polecenie o wyższym priorytecie.

  > `Disable-PSRemoting` Funkcja wyłącza wszystkie konfiguracje sesji na komputerze lokalnym...

- W temacie pomocy skryptu Wyjaśnij, jak używać skryptu jako całości. Jeśli zapisujesz również tematy pomocy dotyczące funkcji w skrypcie, wspominaj funkcje w temacie pomocy dotyczącej skryptów i Dołącz do tematów pomocy dotyczących funkcji w sekcji Linki pokrewne w temacie pomocy skryptu. Z drugiej strony, gdy funkcja jest częścią skryptu, Wyjaśnij w temacie pomocy funkcji rola, którą ta funkcja pełni w skrypcie i jak może być używana niezależnie. Następnie utwórz listę tematów pomocy dotyczącej skryptów w sekcji Linki pokrewne w temacie dotyczącym funkcji.

- Podczas pisania przykładów dla tematu pomocy skryptu pamiętaj o uwzględnieniu ścieżki do pliku skryptu w przykładowym poleceniu. Przypomina to użytkownikom, że muszą jawnie określić ścieżkę, nawet gdy skrypt znajduje się w bieżącym katalogu.

- W temacie pomocy funkcji Przypomnij użytkownikom, że funkcja istnieje tylko w bieżącej sesji i, aby użyć jej w innych sesjach, muszą dodać ją lub dodać do niej profil programu PowerShell.

- `Get-Help`wyświetla temat pomocy dla skryptu lub funkcji tylko wtedy, gdy plik skryptu i pliki tematów pomocy są zapisywane w prawidłowych lokalizacjach. W związku z tym nie warto uwzględniać instrukcji dotyczących instalowania programu PowerShell ani zapisywania ani instalowania skryptów lub funkcji w temacie pomocy skryptu lub funkcji. Zamiast tego należy uwzględnić wszelkie instrukcje instalacji w dokumencie używanym do dystrybucji skryptu lub funkcji.

## <a name="see-also"></a>Zobacz też

[Pisanie tematów pomocy opartych na komentarzach](./writing-comment-based-help-topics.md)
