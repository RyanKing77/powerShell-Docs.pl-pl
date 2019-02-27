---
title: Windows PowerShell programisty&#39;przewodnik s | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 1f7b5b60b202f4de0cf3d44b65057f5edd41f2b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849644"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell programisty&#39;przewodnik s

Ten przewodnik jest przeznaczona dla deweloperów, którzy są zainteresowani zapewnienie środowiska wiersza polecenia do zarządzania dla administratorów systemów. Windows PowerShell udostępnia prosty sposób tworzenia poleceń zarządzania, które uwidaczniają obiektów platformy .NET, pozwalając Windows PowerShell, aby wykonać większość pracy za Ciebie.

Podczas tworzenia tradycyjnych polecenia są wymagane do zapisania analizatora parametru, obiekt wiążący parametr, filtry i wszystkie inne funkcje udostępniane przez każde polecenie. Program Windows PowerShell udostępnia następujące polecenie, aby ułatwić pisanie poleceń:

- Zaawansowane środowiska Windows PowerShell aparatu plików wykonywalnych (aparat wykonywania) swój własny analizator i mechanizm automatycznie wiązania parametrów polecenia.

- Narzędzia do formatowania i wyświetlania wyników polecenia za pomocą interpretera wiersza polecenia (CLI).

- Obsługa wysokiej poziomów funkcjonalności (za pośrednictwem dostawcy programu Windows PowerShell), które ułatwiają dostęp do danych przechowywanych.

  Przy niewielkim koszcie może reprezentować obiektu platformy .NET, rozbudowane polecenia lub zestaw poleceń, które zapewnia kompleksowe środowisko wiersza polecenia do administratora.

  Następna sekcja obejmuje podstawowe pojęcia programu Windows PowerShell i warunki. Zapoznaj się z tych pojęć i terminów przed rozpoczęciem projektowania.

## <a name="about-windows-powershell"></a>Informacje o programie Windows PowerShell

Programu Windows PowerShell definiuje kilka typów poleceń, które są dostępne w trakcie opracowywania. Są to: funkcje, filtry, skrypty, aliasy i pliki wykonywalne (aplikacje). Wpisz polecenie główne omówione w tym przewodniku jest proste, małe polecenie o nazwie "polecenie cmdlet". Program Windows PowerShell przedstawia zestaw poleceń cmdlet i w pełni obsługuje polecenie cmdlet dostosowania do potrzeb środowiska. Środowisko wykonawcze programu Windows PowerShell przetwarza wszystkie typy, tak jak polecenia cmdlet, za pomocą potoków.

Oprócz poleceń programu Windows PowerShell obsługuje różnych dostawców środowiska Windows PowerShell można dostosować, składających się na konkretnych zestawów dostępnych poleceń cmdlet. Powłoki działa w aplikacji hosta dostarczone do programu Windows PowerShell (Windows PowerShell.exe), ale nie jest równie dostępny aplikacji niestandardowego hosta, w której można tworzyć w celu spełnienia określonych wymagań. Aby uzyskać więcej informacji, zobacz [sposób działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Polecenia cmdlet programu Windows PowerShell

Polecenie cmdlet jest uproszczone polecenia, który jest używany w środowisku Windows PowerShell. Środowisko wykonawcze programu Windows PowerShell wywołuje te polecenia cmdlet w kontekście skryptów automatyzacji, które znajdują się w wierszu polecenia, a środowisko wykonawcze programu Windows PowerShell wywołuje również je programowo za pośrednictwem interfejsów API programu Windows PowerShell.

Aby uzyskać więcej informacji na temat poleceń cmdlet, zobacz [pisania polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell dostawców

Wykonywanie zadań administracyjnych, użytkownik może być konieczne zbadanie danych przechowywanych w magazynie danych (na przykład system plików, rejestru Windows lub magazynu certyfikatów). Aby ułatwić te operacje, programu Windows PowerShell definiuje moduł o nazwie dostawcy środowiska Windows PowerShell, który może służyć dostępu do magazynu danych z konkretnych, takich jak rejestr Windows. Każdy dostawca obsługuje zestaw powiązanych poleceń cmdlet, aby przyznać użytkownikowi symetryczne widok danych w magazynie.

Program Windows PowerShell udostępnia kilka domyślne dostawcy środowiska Windows PowerShell. Na przykład dostawca rejestru obsługuje nawigacji i manipulowania nimi rejestru Windows. Klucze rejestru są reprezentowane jako elementy, a wartości rejestru są traktowane jako właściwości.

Jeśli należy udostępnić magazyn danych, który użytkownik będzie musiał uzyskać dostęp, może być konieczne zapisać własnego dostawcę środowiska Windows PowerShell zgodnie z opisem w [Tworzenie dostawcy programu Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Aby uzyskać więcej informacji o aboutWindows dostawcy programu PowerShell, zobacz [sposób działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Aplikacja hosta

Środowisko Windows PowerShell zawiera domyślne powershell.exe aplikacji hosta, czyli aplikację konsolową która wchodzi w interakcję z użytkownikiem i hostuje środowisko wykonawcze programu Windows PowerShell, za pomocą okna konsoli.

Tylko rzadko będzie należy napisać własną aplikację hosta dla środowiska Windows PowerShell, mimo że Dostosowywanie jest obsługiwane. Jeden przypadek, w którym może być konieczne jego własnej aplikacji jest, gdy interfejs graficzny interfejs użytkownika, który jest bogatszy niż interfejs dostarczony przez aplikację hosta domyślnego. Możesz również niestandardowych aplikacji, gdy będzie tworzony interfejs graficzny w wierszu polecenia. Aby uzyskać więcej informacji, zobacz[jak utworzyć aplikację hosta programu Windows PowerShell](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Środowisko uruchomieniowe programu Windows PowerShell

Środowisko uruchomieniowe programu Windows PowerShell jest aparatem wykonywania, który implementuje przetwarzanie poleceń. Zawiera klasy, które zapewniają interfejs między aplikacją hosta i poleceń programu Windows PowerShell i dostawców. Środowisko wykonawcze programu Windows PowerShell jest zaimplementowana jako obiekt obszaru działania dla bieżącej sesji programu Windows PowerShell, czyli środowisku operacyjnym, w którym wykonywanie polecenia i powłoki. Aby uzyskać szczegółowe informacje operacyjne, zobacz [sposób działania programu Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Języka programu Windows PowerShell

Język programu Windows PowerShell udostępnia skryptów funkcje i mechanizmy do wywołania poleceń. Aby uzyskać pełne informacje skryptów Zobacz dokumentacja języka programu Windows PowerShell dostarczane za pomocą programu Windows PowerShell.

### <a name="extended-type-system-ets"></a>Typ rozszerzony systemu (ETS)

Program Windows PowerShell umożliwia dostęp do szeregu różnych obiektów, takich jak .NET i obiektów XML. W rezultacie aby przedstawić typowe abstrakcji dla wszystkich typów obiektów powłoki używa jego typie rozszerzonym system (ETS). Większość funkcji ETS jest niewidoczne dla użytkownika, ale skryptu lub dla deweloperów .NET używa go do następujących celów:

- Wyświetlanie podzestaw elementów członkowskich określonych obiektów. Program Windows PowerShell zawiera "dostosowane" Widok kilku określonych typów obiektów.

- Dodawanie członków do istniejących obiektów.

- Dostęp do serializacji obiektów.

- Zapisywanie dostosowanego obiektów.

  Za pomocą ETS, możesz utworzyć nowe "typy elastyczne", są zgodne z językiem programu Windows PowerShell. Jeśli jesteś deweloperem platformy .NET, jesteś w stanie, aby pracować z obiektami za pomocą tej samej semantyki jako język programu Windows PowerShell dotyczy skryptów, na przykład, aby określić, jeśli obiekt daje w wyniku `true`.

  Aby uzyskać więcej informacji na temat ETS i używaniu programu Windows PowerShell na obiekty, zobacz [pojęcia programu Windows PowerShell obiektu](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programowanie dla środowiska Windows PowerShell

Program Windows PowerShell definiuje jego kod dla polecenia, dostawców i innych modułów programu przy użyciu programu .NET Framework. Użytkownik są nie ogranicza się do korzystania z programu Microsoft Visual Studio podczas tworzenia niestandardowych modułów środowiska Windows PowerShell, mimo że przykładów podanych w tym przewodniku są znane, aby uruchomić to narzędzie. Możesz użyć dowolnego języka .NET, który obsługuje dziedziczenie klas i używanie atrybutów. W niektórych przypadkach interfejsów API programu Windows PowerShell wymagają języka programowania, aby można było uzyskiwać dostęp do typów ogólnych.

## <a name="programmers-reference"></a>Podręcznik programisty

Odwołanie podczas tworzenia środowiska Windows PowerShell, zobacz [zestawu SDK programu Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Rozpoczynanie pracy przy użyciu programu Windows PowerShell

Aby uzyskać więcej informacji na temat korzystania z powłoki programu Windows PowerShell, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) dostarczane za pomocą programu Windows PowerShell. Dokument potrójne krótki przewodnik jest również podana jako podstawowe informacje dotyczące użycia polecenia cmdlet.

## <a name="contents-of-this-guide"></a>Zawartość tego przewodnika

|Temat|Definicja|
|-----------|----------------|
|[Jak utworzyć dostawcę Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Ta sekcja zawiera opis sposobu tworzenia dostawcy środowiska Windows PowerShell dla programu Windows PowerShell.|
|[Jak utworzyć aplikację hosta programu PowerShell Windows](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|W tej sekcji opisano sposób pisania aplikacji hosta, która manipuluje obszarem działania oraz sposobu pisania aplikacji hosta, który implementuje własnego niestandardowego hosta.|
|[Jak utworzyć przystawki Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|W tej sekcji opisano sposób tworzenia przystawki, który służy do rejestrowania wszystkich poleceń cmdlet i dostawców w zestawie oraz jak utworzyć niestandardowe przystawki.|
|[Jak utworzyć powłoki konsoli](./how-to-create-a-console-shell.md)|Ta sekcja zawiera opis sposobu tworzenia powłoki konsoli, który nie jest rozszerzalny.|
|[Pojęcia dotyczące programu Windows PowerShell](./windows-powershell-concepts.md)|Ta sekcja zawiera ogólne informacje, które pomoże Ci zrozumieć programu Windows PowerShell z punktu widzenia dewelopera.|

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)