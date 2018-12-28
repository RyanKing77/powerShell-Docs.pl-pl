---
ms.date: 08/23/2018
keywords: polecenia cmdlet programu PowerShell
title: Opis ważnych pojęć związanych z programu PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404664"
---
# <a name="understanding-important-powershell-concepts"></a>Opis ważnych pojęć związanych z programu PowerShell

Projekt programu PowerShell integruje pojęcia z wielu różnych środowiskach. Niektóre pojęcia będą niczym nowym do osoby z doświadczeniem w środowiskach programowania i powłoki. Jednak kilka osób będzie wiadomo o wszystkich z nich. Zapoznawanie się z niektórymi z tych koncepcji omówienie przydatne powłoki.

## <a name="output-is-object-based"></a>Dane wyjściowe są oparte na obiektach

W przeciwieństwie do tradycyjnych interfejsów z wierszem polecenia poleceń cmdlet programu PowerShell są przeznaczone do czynienia z obiektami.
Obiekt to ustrukturyzowanych informacji, która jest więcej niż tylko ciąg znaków, które pojawiają się na ekranie. Zawsze danych wyjściowych polecenia niesie ze sobą dodatkowych informacji, które można użyć, jeśli jest potrzebna.

Jeśli używano narzędzia przetwarzanie tekstu do przetwarzania danych w przeszłości, przekonasz się, że działają inaczej stosowania w programie PowerShell. W większości przypadków nie trzeba narzędzia przetwarzanie tekstu, aby wyodrębnić szczegółowe informacje. Możesz uzyskać bezpośredni dostęp do części danych przy użyciu standardowej składni obiekt programu PowerShell.

## <a name="the-command-family-is-extensible"></a>Rodzina poleceń jest rozszerzalny

Interfejsy, takie jak **cmd.exe** nie umożliwiają zwiększenie bezpośrednio zestawu wbudowanego polecenia. Można utworzyć zewnętrzne narzędzia wiersza polecenia, które działają w **cmd.exe**. Ale tych narzędzi zewnętrznych nie ma usług, takich jak integracja pomocy. **cmd.exe** automatycznie nie wie, że te narzędzia zewnętrzne są prawidłowych poleceń.

Natywne poleceń w programie PowerShell, są znane jako *poleceń cmdlet* (Wymowa komand-). Można tworzyć własne moduły poleceń cmdlet i funkcji przy użyciu skompilowany kod lub skrypty. Moduły można dodać polecenia cmdlet i dostawców, powłoki. Program PowerShell obsługuje również skrypty, które są analogiczne do skryptów powłoki systemu UNIX i **cmd.exe** pliki wsadowe.

## <a name="powershell-handles-console-input-and-display"></a>Program PowerShell obsługuje dane wejściowe konsoli i wyświetlanie

Po wpisaniu polecenia, programu PowerShell zawsze przetwarza dane wejściowe wiersza polecenia bezpośrednio. PowerShell również formaty danych wyjściowych, które widzą na ekranie. Różnica ta jest istotne, ponieważ jego zmniejsza nakład pracy potrzebny każdego polecenia cmdlet. Zapewnia, że można zawsze wykonywać takie czynności ten sam sposób, korzystając z każdego polecenia cmdlet. Polecenia cmdlet deweloperów trzeba napisać kod, aby przeanalizować argumenty wiersza polecenia lub formatowania danych wyjściowych.

Tradycyjne narzędzia wiersza polecenia mają własne systemy dla żądania i wyświetlanie pomocy. Niektóre narzędzia wiersza polecenia użyj **/?** Aby wyzwolić Wyświetlanie pomocy; inne korzystają **-?**, **/h**, lub nawet **//**. Niektóre wyświetli pomocy w oknie graficznego interfejsu użytkownika, a nie w oknie konsoli. Jeśli nieprawidłowy parametr jest używany, narzędzie może zignorować co wpisany i rozpoczyna się ich automatyczne wykonywanie zadania.
Od czasu programu PowerShell automatycznie analizowania i przetwarzania wiersza polecenia **-?** Parametr zawsze oznacza, że "Pokaż Pomoc dla tego polecenia".

> [!NOTE]
> Po uruchomieniu aplikacji grafiki w programie PowerShell zostanie otwarta w oknie aplikacji.
> Program PowerShell interwencji, tylko gdy przetwarzania wiersza polecenia dane wejściowe możesz dostaw lub dane wyjściowe aplikacji powrót do okna konsoli. Nie dotyczy to, jak działa aplikacja wewnętrznie.

## <a name="powershell-uses-some-c-syntax"></a>Niektóre przypadki składni języka C# korzysta z programu PowerShell

Program PowerShell jest oparta na .NET Framework. Współużytkuje niektóre funkcje składni i słów kluczowych z języka programowania C#. Poznawania programu PowerShell mogą ułatwić znacznie poznawać język C#. Jeśli znasz już C#, te podobieństwa wprowadzać poznawania programu PowerShell jest łatwiejsze.
