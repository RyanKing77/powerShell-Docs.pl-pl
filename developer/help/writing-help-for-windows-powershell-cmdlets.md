---
title: Pisanie tematów Pomocy dotyczących poleceń cmdlet programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848111"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Zapisywanie Pomoc dla poleceń cmdlet programu PowerShell

Polecenia cmdlet programu PowerShell może być przydatna, ale chyba, że tematy pomocy wyjaśniają, działanie polecenia cmdlet i jak z niej korzystać, polecenie cmdlet nie może pobrać używane, lub gorsza, może frustrować użytkowników.
Format pliku pomocy polecenia cmdlet opartego na XML zwiększa spójność, ale bardzo pomóc wymaga znacznie więcej.

Jeśli nigdy nie zostały zapisane pomocy polecenia cmdlet, należy rozważyć następujące wskazówki.
Schemat XML, wymagane do tworzenia tematu pomocy polecenia cmdlet jest opisane w poniższej sekcji.
Rozpoczynać [tworzenia pliku pomocy dotyczącej poleceń Cmdlet](./how-to-create-the-cmdlet-help-file.md).
Ten temat zawiera opis węzłów XML najwyższego poziomu.

## <a name="writing-guidelines-for-cmdlet-help"></a>Wskazówki dotyczące pisania w celu uzyskania pomocy polecenia Cmdlet

### <a name="write-well"></a>Dobrze zapisu
Nic nie zastępuje dobrze napisane tematu.
Jeśli nie jesteś Edytor professional, znaleźć moduł zapisujący lub edytora, aby.
Innym sposobem jest, aby skopiować tekst pomocy do programu Microsoft Word i użyć gramatykę i pisownię sprawdza, aby zwiększyć swoją pracę.

### <a name="write-simply"></a>Po prostu zapisu
Użyj prostych słów i fraz.
Należy unikać żargonu.
Należy wziąć pod uwagę, że wielu czytników są wyposażone w tylko obcego słownika i tematu Pomocy.

### <a name="write-consistently"></a>Stale zapisu
Pomoc dla powiązane polecenia cmdlet powinny być podobne (na przykład get-x i set-x).
Na użytek standardowe opisy standardowe parametry, takie jak **życie** i **InputObject**.
(Je skopiować z pomocy dla podstawowych poleceń cmdlet środowiska.) Użyj standardowych warunków.
Na przykład użyj "parametr", nie "argument" i użyj "polecenie cmdlet" nie "polecenie" lub "command-let".

### <a name="start-the-synopsis-with-a-verb"></a>Streszczenie rozpoczynać się zlecenia
Pole streszczenie informuje użytkownika, jakie polecenia cmdlet nie, co to jest ani nie jak to działa.
Czasowniki Utwórz instrukcję opartego na zadaniach informuje użytkowników, jeśli to polecenie cmdlet spełnia ich wymagań.
Użyj prostych zleceń, takich jak "get", "Utwórz" i "Zmień".
Należy unikać "set", który może być niejasna i ozdobnych wyrazy, takie jak "Modyfikuj".

### <a name="focus-on-objects"></a>Skup się na obiekty
Większość "get" wyświetlania poleceń cmdlet coś, ale ich podstawową funkcją jest pobranie obiektu.
W pomocy skupić się na obiekt, tak że użytkownicy wiedzą, że domyślnym wyświetlaniem jest jednym z wielu i czy można użyć metod i właściwości obiektu, który uzyskano, wykonując je na różne sposoby.

### <a name="write-detailed-descriptions"></a>Szczegółowy opis zapisu
Krótko listę wszystko, co zrobić w szczegółowy opis polecenia cmdlet.
Jeśli jest funkcja main, aby zmienić jedną właściwość, ale polecenia cmdlet można zmienić wszystkie właściwości, Wyświetl listę to w szczegółowy opis.

### <a name="use-conventional-syntax"></a>Należy użyć składni konwencjonalne
Użyj standardowego formatu notacji Backusa-Naura, który jest wspólny dla Windows i pomoc w wierszu polecenia systemu UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Używanie typów programu Microsoft .NET Framework o wprowadzenie wartości parametrów
Symbole zastępcze wartości parametrów (w składnia i opisy parametrów) Pokaż typy obiektów, które akceptują parametr dla programu .NET Framework.
Zespół programu PowerShell opracowany niniejszej Konwencji, aby ułatwić pomagać innym użytkownikom dotyczące programu .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Zapis opisy parametrów ukończone
Opisy parametrów, należy poinformować użytkowników o dwie rzeczy: jakie parametru nie (jego działanie), a co wpisanie wartości parametrów.

### <a name="write-practical-examples"></a>Zapis praktyczne przykłady
W przykładach powinien pokazano, jak używać wszystkich parametrów, ale ważne jest pokazują, jak użyć polecenia cmdlet w rzeczywistych warunkach zadania.
Rozpocznij od prostego przykładu i zapisu przykłady coraz bardziej złożonych.
W ostatnim przykładzie pokazano, jak użyć polecenia cmdlet w potoku.

### <a name="use-the-notes-field"></a>Użyj pola notatki
Pole uwagi umożliwia opisano pojęcia, które użytkownicy muszą zrozumieć polecenia cmdlet.
Informacje o umożliwia również pomóc użytkownikom w unikaniu typowych błędów.
Należy unikać adresy URL w miarę jak ulegają zmianom.
Zamiast tego Podaj użytkownikom terminy do wyszukania.

### <a name="test-your-help"></a>Testowanie Twojej pomocy
Przetestuj pomocy, tak samo, jak testować kod.
Mieć przyjaciół i współpracowników odczytywanie zawartości pomocy i opinii.
Można również poproś o opinię z grup dyskusyjnych.

## <a name="see-also"></a>Zobacz też

 [Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Jak dodać nazwę polecenia Cmdlet i streszczenie do tematu pomocy polecenia Cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Jak dodać szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Jak dodać składnię do tematu pomocy polecenia Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Jak dodać parametry do tematu pomocy polecenia Cmdlet](./how-to-add-parameter-information.md)

 [Jak dodać typy danych wejściowych do tematu pomocy polecenia Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Jak dodać wartości zwracane do tematu pomocy polecenia Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Jak dodać uwagi tematu pomocy polecenia Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Jak dodawać przykłady do tematu pomocy polecenia Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Jak dodać powiązane linki do tematu pomocy polecenia Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)