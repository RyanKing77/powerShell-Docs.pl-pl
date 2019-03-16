---
title: Omówienie aktualizowalnej pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057607"
---
# <a name="updatable-help-overview"></a>Omówienie aktualizowalnej pomocy

Ten dokument zawiera wstęp do projektowania i działania funkcji aktualizowalnej pomocy Windows PowerShell. Jest ona przeznaczona dla autorzy modułów i innych użytkowników, którzy dostarczają tematy Pomocy programu Windows PowerShell dla użytkowników.

## <a name="introduction"></a>Wprowadzenie

Tematy Pomocy programu Windows PowerShell są integralną częścią środowiska programu Windows PowerShell. Takie jak moduły programu Windows PowerShell tematy pomocy są stale aktualizowane i ulepszona przez autorów i wkład w społeczności użytkowników programu Windows PowerShell.

*Aktualizowalnej pomocy* wprowadzonej w programie Windows PowerShell 3.0 zapewnia użytkownikom najnowszych wersji tematów pomocy w wierszu polecenia, nawet w przypadku wbudowanych poleceń programu Windows PowerShell, bez pobierania nowych modułów lub System Windows Update. Aktualizowalnej pomocy upraszcza aktualizacji, podając poleceń cmdlet, które pobieranie najnowszych wersji tematy Pomocy z Internetu i zainstalować je w prawidłowy podkatalogów na komputerze lokalnym użytkownika. Nawet użytkownicy, którzy znajdują się za zaporami umożliwia korzystanie z wewnętrznego udziału plików pomocy zaktualizowane nowe polecenia cmdlet.

Aktualizowalnej pomocy jest w pełni obsługiwana przez wszystkie moduły programu Windows PowerShell w systemie Windows® 8 i Windows Server® 2012 i jego funkcje są dostępne dla wszystkich autorów modułu programu Windows PowerShell. Aktualizowalnej pomocy obsługuje tylko pliki pomocy opartych na języku XML. Pomoc oparta na komentarzach nie obsługuje.

Aktualizowalnej pomocy zawiera następujące funkcje.

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia cmdlet, który określa, czy użytkownicy mają najnowszą Pomoc pliki modułu i, jeśli nie, pliki do pobrania najnowszych plików pomocy z Internetu, wypakowuje je i instaluje je w podkatalogach do modułu na komputerze użytkownika.
  Użytkownicy mogą używać [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, aby natychmiast wyświetlić tematy pomocy nowo zainstalowany.
  One nie trzeba ponownie uruchamiać programu PowerShell.

- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) polecenia cmdlet, który pobiera najnowszą Pomoc plików z Internetu i zapisuje je w katalogu w systemie plików. Użytkownicy mogą używać `Update-Help` polecenia cmdlet, aby pobrać pliki pomocy z katalogu system plików i Rozpakowywanie i zainstalować je w podkatalogach modułu na komputerze użytkownika. `Save-Help` Polecenia cmdlet jest przeznaczona dla użytkowników, którzy mają ograniczoną lub Brak dostępu do Internetu i w przedsiębiorstwach, którzy wolą, aby ograniczyć dostęp do Internetu.

- **Pomoc dla modułu**. Pliki pomocy dla modułu zarządzanych i dostarczane jako zespół, dzięki czemu użytkownicy mogą uzyskać wszystkie pliki pomocy dla modułów, których używają. Aktualizowalnej pomocy jest obsługiwana tylko dla modułów, nie dla przystawek programu Windows PowerShell.

- **Obsługa wersji**. Aktualizowalnej pomocy używa standardu czterech pozycji (N1. N2. N3. Numery wersji N4). Aktualizowalnej pomocy pobiera pliki pomocy, gdy numer wersji pomocy pliki z komputera użytkownika (lub `Save-Help` katalogu) jest niższa niż numer wersji plików pomocy w lokalizacji internetowej.

- **Obsługa wielu języków**. Aktualizowalnej pomocy obsługuje pliki pomocy modułu w wielu kulturach interfejsu użytkownika. Aktualizowalnej pomocy nazwy plików zawierają kody standardowych języków, takich jak "en US" i "ja-JP" i `Update-Help` i `Save-Help` poleceń cmdlet umieścić pliki pomocy podkatalogi specyficzny dla języka w katalogu modułu.

- **Wygenerowany automatycznie pomocy**. [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenie cmdlet Wyświetla podstawowe tematy Pomocy dotyczące poleceń, które nie mają plików pomocy. Wygenerowany automatycznie pomocy zawiera składni poleceń i aliasy i instrukcje dotyczące korzystania z pomocy online i aktualizowalnej pomocy.

- **Ulepszone pomocy Online**. Łatwy dostęp do pomocy online nie wymaga już pliki pomocy. **Online** parametru `Get-Help` teraz polecenie cmdlet pobiera adres URL tematu Pomocy online od wartości **HelpUri** właściwości dowolnego polecenia pomocy online adres URL nie można znaleźć w pliku pomocy. Możesz wypełnić **HelpUri** właściwości, dodając **HelpUri** atrybutu w kodzie polecenia cmdlet, funkcji i poleceń CIM lub za pomocą **. Link** dyrektywy Pomoc oparta na komentarz w przepływami pracy a skryptami.

  Aby naszych plików pomocy nadaje się do aktualizacji, moduły programu Windows PowerShell w systemie Windows 8 i Windows Server vNext nie są dostarczane z plików pomocy. Użytkownicy mogą używać aktualizowalnej pomocy do zainstalowania plików pomocy i zaktualizuj je. Autorzy inne moduły można dołączyć pliki pomocy w modułach lub Pomiń je. Obsługa aktualizowalnej pomocy jest opcjonalne, ale zalecane.
