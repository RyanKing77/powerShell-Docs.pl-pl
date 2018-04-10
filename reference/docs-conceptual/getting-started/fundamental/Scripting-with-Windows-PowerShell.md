---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obsługa skryptów w programie Windows PowerShell
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: 9bb420a3d725d3fa925b79452bbbcc542bf9f4db
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="scripting-with-windows-powershell"></a>Obsługa skryptów w programie Windows PowerShell

Windows PowerShell® jest powłoką wiersza polecenia opartą na zadaniach oraz językiem skryptowym opracowanym specjalnie w celu administrowania systemami. Wbudowane w program .NET Framework, programu Windows PowerShell umożliwia informatykom i sterowanie zasilaniem użytkowników i zautomatyzować administracji systemu operacyjnego i aplikacji działających w systemie Windows.

Polecenia programu Windows PowerShell, nazywane *poleceń cmdlet*, umożliwiają zarządzanie komputerami z poziomu wiersza polecenia. Środowisko Windows PowerShell *dostawców* pozwalają na dostęp do magazynów danych, takich jak rejestr i magazyn certyfikatów, łatwo dostęp do systemu plików. Ponadto środowisko Windows PowerShell jest analizatora składni wyrażeń i w pełni rozwinięty język skryptów.

Program Windows PowerShell zawiera następujące funkcje:

- Polecenia cmdlet do wykonywania typowych zadań administracyjnych, takich jak zarządzanie rejestru, usług, procesów i dzienniki zdarzeń i przy użyciu Instrumentacji zarządzania Windows (WMI).
- Oparty na zadaniach językiem skryptowym i obsługę istniejące skrypty i narzędzia wiersza polecenia.
- Spójne projektu. Ponieważ przechowuje dane polecenia cmdlet i systemu należy użyć składni typowe i konwencje nazewnictwa, można łatwo udostępniać dane i dane wyjściowe z jednego polecenia cmdlet mogą być używane jako dane wejściowe inne polecenie cmdlet bez ponownego formatowania lub manipulowania.
- Uproszczony, opartego na poleceniu nawigacji systemu operacyjnego, który umożliwia użytkownikom Przejdź rejestru i innych magazynach danych przy użyciu tych samych metod, używające poruszać się w systemie plików.
- Obiekt zaawansowanych możliwości manipulowanie. Bezpośrednio manipulować obiektów lub wysyłane do innych narzędzi lub baz danych.
- Interfejs Extensible. Niezależni dostawcy oprogramowania i deweloperów w przedsiębiorstwach, można tworzyć niestandardowe narzędzia i narzędzia do administrowania ich oprogramowania.