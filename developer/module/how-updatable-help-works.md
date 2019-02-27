---
title: Jaki aktualizowalnej pomocy działa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 8874cc18416937c4d3cb30d801f2714410304c8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850225"
---
# <a name="how-updatable-help-works"></a>Jaki działa pomoc aktualizowalna

W tym temacie wyjaśniono, jak aktualizowalnej pomocy procesy plik HelpInfo XML i CAB plików dla każdego modułu, a także instaluje zaktualizowano Pomoc dla użytkowników.

## <a name="the-update-help-process"></a>Proces Update-Help

Na poniższej liście opisano akcje [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia cmdlet, gdy użytkownik uruchamia polecenie, aby zaktualizować pliki pomocy dla modułu w danej kultury interfejsu użytkownika.
Na poniższej liście opisano akcje [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia cmdlet, gdy użytkownik uruchamia polecenie, aby zaktualizować pliki pomocy dla modułu w danej kultury interfejsu użytkownika.

1. `Update-Help` pobiera zdalny plik HelpInfo XML w lokalizacji określonej przez wartość **HelpInfoURI** klucza w manifeście modułu i sprawdza poprawność pliku względem schematu. (Aby wyświetlić schemat, zobacz [schematu XML HelpInfo](./helpinfo-xml-schema.md).) Następnie `Update-Help` szuka lokalnego pliku HelpInfo XML modułu w katalogu modułu na komputerze użytkownika.

2. `Update-Help` porównuje numer wersji plików pomocy dla określonej kultury interfejsu użytkownika w plikach HelpInfo XML zdalnych i lokalnych dla modułu. Czy numer wersji pliku zdalnego jest większy niż numer wersji w lokalnym pliku, czy obowiązuje ma HelpInfo XML pliku lokalnego dla modułu, `Update-Help` przygotowuje pobieranie nowe pliki pomocy.

3. `Update-Help` Wybiera plik CAB dla modułu z lokalizacji określonej przez **HelpContentUri** elementu w pliku HelpInfo XML zdalnego. Używa nazwy modułu, moduł identyfikator GUID i kultura interfejsu użytkownika do identyfikowania pliku CAB.

4. `Update-Help` Pobieranie pliku CAB, wypakowuje go, sprawdza poprawność plików zawartości pomocy i zapisuje pomocy plików zawartości w podkatalogu specyficzny dla języka w katalogu modułu na komputerze użytkownika.

5. `Update-Help` Tworzy plik lokalny HelpInfo XML przez skopiowanie pliku HelpInfo XML zdalnego. Edytuje lokalnego pliku HelpInfo XML, aby obejmowała elementów tylko dla pliku CAB, który on zainstalowany. Następnie go zapisuje lokalnego pliku HelpInfo XML w katalogu modułu i nie zawiera aktualizacji.

## <a name="the-save-help-process"></a>Proces Save-Help

Na poniższej liście opisano akcje [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) i [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) poleceń cmdlet, gdy użytkownik uruchamia polecenia, aby zaktualizować pliki pomocy w udziale plików, a następnie użyć tych plików, aby zaktualizować pliki pomocy na na komputerze użytkownika.
Na poniższej liście opisano akcje [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) i [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) poleceń cmdlet, gdy użytkownik uruchamia polecenia, aby zaktualizować pliki pomocy w udziale plików, a następnie użyć tych plików, aby zaktualizować pliki pomocy na na komputerze użytkownika.

`Save-Help` Polecenia cmdlet wykonuje następujące akcje w odpowiedzi na polecenie, aby zapisać pliki pomocy dla modułu w udziale plików, który jest określony przez **Ścieżka_docelowa** parametru.

1. `Save-Help` pobiera zdalny plik HelpInfo XML w lokalizacji określonej przez wartość **HelpInfoURI** klucza w manifeście modułu i sprawdza poprawność pliku względem schematu. (Aby wyświetlić schemat, zobacz [schematu XML HelpInfo](./helpinfo-xml-schema.md).) Następnie `Save-Help` szuka lokalnego pliku HelpInfo XML w katalogu, który jest określony przez **Ścieżka_docelowa** parametru w `Save-Help` polecenia.

2. `Save-Help` porównuje numer wersji plików pomocy dla określonej kultury interfejsu użytkownika w plikach HelpInfo XML zdalnych i lokalnych dla modułu. Czy numer wersji pliku zdalnego jest większy niż numer wersji w lokalnym pliku, czy obowiązuje ma HelpInfo XML pliku lokalnego dla modułu w **Ścieżka_docelowa** katalogu `Save-Help` przygotowuje pobieranie nowe pliki pomocy.

3. `Save-Help` Wybiera plik CAB dla modułu z lokalizacji określonej przez **HelpContentUri** elementu w pliku HelpInfo XML zdalnego. Używa nazwy modułu, moduł identyfikator GUID i kultura interfejsu użytkownika do identyfikowania pliku CAB.

4. `Save-Help` Pobieranie pliku CAB i zapisuje go w **Ścieżka_docelowa** katalogu. (Nie tworzy żadnych podkatalogi specyficzny dla języka.)

5. `Save-Help` Tworzy plik lokalny HelpInfo XML przez skopiowanie pliku HelpInfo XML zdalnego. Edytuje lokalnego pliku HelpInfo XML, aby obejmowała elementów tylko dla pliku CAB, który można go zapisać. A następnie zapisuje lokalny plik HelpInfo XML **Ścieżka_docelowa** katalogu i nie zawiera aktualizacji.

   `Update-Help` Polecenia cmdlet wykonuje następujące akcje w odpowiedzi na polecenie, aby zaktualizować pliki pomocy, na komputerze użytkownika z plików w udziale plików, który jest określony przez **Ścieżka_źródłowa** parametru.

1. `Update-Help` pobiera zdalny plik HelpInfo XML z **Ścieżka_źródłowa** katalogu. Następnie szuka pliku lokalnego HelpInfo XML w katalogu modułu na komputerze użytkownika.

2. `Update-Help` porównuje numer wersji plików pomocy dla określonej kultury interfejsu użytkownika w plikach HelpInfo XML zdalnych i lokalnych dla modułu. Czy numer wersji pliku zdalnego jest większy niż numer wersji w lokalnym pliku, czy obowiązuje nie lokalnego pliku HelpInfo XML `Update-Help` przygotowuje instalację nowe pliki pomocy.

3. `Update-Help` Wybiera plik CAB dla modułu z **Ścieżka_źródłowa** katalogu. Używa nazwy modułu, moduł identyfikator GUID i kultura interfejsu użytkownika do identyfikowania pliku CAB.

4. `Update-Help` wypakowuje plik CAB, sprawdza poprawność plików zawartości pomocy, a następnie zapisuje pomocy pliki zawartości w podkatalogu specyficzny dla języka w katalogu modułu na komputerze użytkownika.

5. `Update-Help` Tworzy plik lokalny HelpInfo XML przez skopiowanie pliku HelpInfo XML zdalnego. Edytuje lokalnego pliku HelpInfo XML, aby obejmowała elementów tylko dla pliku CAB, który on zainstalowany. Następnie go zapisuje lokalnego pliku HelpInfo XML w katalogu modułu i nie zawiera aktualizacji.