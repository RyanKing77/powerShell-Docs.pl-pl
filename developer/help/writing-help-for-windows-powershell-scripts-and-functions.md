---
title: Pisanie tematów Pomocy dotyczących skryptów programu PowerShell i funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083114"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Pisanie tematów Pomocy dotyczących skryptów programu PowerShell i funkcji

Funkcje i skryptów programu PowerShell należy w pełni udokumentowane w każdym przypadku, gdy są one udostępniane innym osobom.
`Get-Help` Polecenie cmdlet wyświetla tematy pomocy skryptów i funkcji w tym samym formacie jak Wyświetla Pomoc dotyczącą poleceń cmdlet i wszystkie `Get-Help` parametry pracować nad skrypt i funkcja tematy Pomocy.

Skrypty programu PowerShell mogą obejmować tematu Pomocy dotyczące skryptu i tematów Pomocy dotyczących poszczególnych funkcji w skrypcie.
Funkcje, które są udostępniane niezależnie od skryptów mogą zawierać własne tematy Pomocy.

W tym dokumencie wyjaśniono format i poprawne umieszczania tematów pomocy a sugerują one wskazówki dotyczące zawartości.

## <a name="types-of-script-and-function-help"></a>Typy skryptu i pomocy — funkcja

### <a name="comment-based-help"></a>Pomoc oparta na komentarz
Temat pomocy, który opisano w skrypcie lub funkcji można zaimplementować jako zbiór komentarzy w skrypcie lub funkcji.
Podczas zapisywania pomocy komentarz skryptu i funkcji w skrypcie, płacisz uważnego reguły umieszczania Pomoc oparta na komentarz.
Określa położenie czy `Get-Help` polecenia cmdlet kojarzy tematu pomocy za pomocą skryptu lub funkcji.
Aby uzyskać więcej informacji na temat pisania oparta na komentarzach tematy pomocy, zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Pomoc dla polecenia opartego na języku XML
Temat pomocy, który opisano w skrypcie lub funkcji może być implementowany w pliku XML, który używa schematu pomocy polecenia.
Aby skojarzyć skryptu lub funkcji z pliku XML, należy użyć `ExternalHelp` komentarz — słowo kluczowe, a następnie ścieżka i nazwa pliku XML.

Gdy `ExternalHelp` komentarz, słowo kluczowe, ma pierwszeństwo przed Pomoc oparta na komentarz, nawet wtedy, gdy `Get-Help` nie można odnaleźć pliku pomocy, który dopasowuje wartość `ExternalHelp` — słowo kluczowe.

### <a name="online-help"></a>Pomoc online
Możesz publikować tematy pomocy przez Internet, a następnie przekierowanie `Get-Help` otworzyć tematy.
Aby uzyskać więcej informacji na temat pisania oparta na komentarzach tematy pomocy, zobacz [Obsługa pomocy Online](../module/supporting-online-help.md).

Nie istnieje ustanowionych metoda zapisu koncepcyjnej ("o") tematy dotyczące skryptów i funkcji.
Jednak możesz zadać tematów pojęciowych na liście Internet ich adresy URL i tematy w sekcji linki powiązane tematu pomocy polecenia.

## <a name="content-considerations-for-script-and-function-help"></a>Pomoc zawartości zagadnienia dotyczące skryptów i funkcji

- Jeśli piszesz bardzo krótki tematu pomocy przy użyciu tylko kilka sekcji Pomoc dostępne polecenia, należy uwzględnić wyczyść opisy parametrów skryptu lub funkcji. Także jeden lub dwa przykładowe polecenia w sekcji przykłady, nawet jeśli zdecydujesz pominąć przykładowe opisy.

- W opisach wszystkich zapoznaj się z poleceniem w skrypcie lub funkcji. Informacje te pomagają użytkownikowi zrozumieć i zarządzanie nimi polecenia.

  Na przykład następujące szczegółowy opis stwierdza, czy polecenie New-tematu jest skrypt. Przypomina o tym użytkowników, które są im niezbędne do określania ścieżki i imię i nazwisko, gdy są uruchamiane.

  > "Skrypt nowy temat tworzy pustą tematu pojęciowego, dla każdej nazwy tematu w pliku wejściowym..."

  Następujące szczegółowy opis stwierdza, że `Disable-PSRemoting` jest funkcją. Te informacje są szczególnie przydatne dla użytkowników, gdy sesja zawiera wiele poleceń o takiej samej nazwie, z których część może być ona ukryta za pomocą polecenia o wyższym priorytecie.

  > `Disable-PSRemoting` Funkcja wyłącza wszystkie konfiguracje sesji na komputerze lokalnym...

- W temacie Pomocy skryptu wyjaśniają jak używać skryptu jako całości. Jeśli piszesz także tematy pomocy dla funkcji w skrypcie, wspomnieć o funkcje tematu Pomocy skryptu i zawierają odwołania do funkcji tematów pomocy w sekcji linki powiązane tematu Pomocy skryptu. Z drugiej strony gdy funkcja jest część skryptu, opisano w temacie Pomocy — funkcja roli, funkcji odtwarzany w skrypcie i jak ją mogą być używane niezależnie. Następnie utwórz listę tematu Pomocy skryptu w sekcji linki powiązane tematu pomocy funkcji.

- Podczas pisania przykłady skryptów tematu pomocy, pamiętaj, że zawiera ścieżkę do pliku skryptu w przykładzie polecenia. Przypomina użytkownikom, że muszą oni określić ścieżkę jawnie, nawet wtedy, gdy skrypt znajduje się w bieżącym katalogu.

- W temacie pomocy funkcji Przypomnij, które funkcja istnieje tylko w bieżącej sesji, a następnie ich wykorzystania w innych sesjach, należy dodać go lub dodać profil programu PowerShell.

- `Get-Help` Wyświetla tematu Pomocy dotyczącego skryptu lub funkcji, tylko wtedy, gdy plik skryptu i plików tematów pomocy są zapisywane w odpowiednich lokalizacjach. W związku z tym nie jest przydatna podczas dołączania instrukcje dotyczące instalowania programu PowerShell, zapisywanie lub instalowanie skryptu lub funkcji w skrypcie lub funkcji tematu Pomocy. Zamiast tego należy umieścić wszystkie instrukcje w dokumencie, używanego do dystrybuowania skryptu lub funkcji.

## <a name="see-also"></a>Zobacz też

 [Pisanie tematów pomocy oparty na składni XML dla skryptów i funkcji](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Pisanie tematów pomocy opartych na języku XML dla polecenia](./writing-xml-based-help-topics-for-commands.md)

 [Pisanie tematów pomocy oparta na komentarzach](./writing-comment-based-help-topics.md)
