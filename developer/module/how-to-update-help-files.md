---
title: Jak zaktualizować pliki pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846480"
---
# <a name="how-to-update-help-files"></a>Jak zaktualizować pliki pomocy

W tym temacie wyjaśniono, jak można zaktualizować pliki pomocy dla modułu, który obsługuje aktualizowalnej pomocy.

## <a name="updating-help-files"></a>Aktualizowanie plików pomocy

Istnieje wiele powodów, aby zaktualizować pliki pomocy, takich jak usuwanie błędów, wyjaśnienia koncepcji, udzielenie odpowiedzi na często zadawane pytania, dodanie nowych plików lub dodanie nowych i lepszych przykłady.

Aby zaktualizować plik pomocy:

1. Zmiana plików.

2. Pliki przekłada się na inne kultury interfejsu użytkownika.

3. Zbieraj wszystkie pliki pomocy (nowych, zmiany i niezmienione) dla modułu w każda kultura interfejsu użytkownika.

4. Sprawdź poprawność plików względem schematu XML.

5. Ponownie skompiluj pliki CAB każda kultura interfejsu użytkownika.

6. W pliku HelpInfo XML zwiększyć numery wersji pliku CAB każda kultura interfejsu użytkownika.

7. Przekaż nowe pliki CAB do lokalizacji, który jest określony przez wartość **HelpContentUri** elementu w pliku HelpInfo XML. Zastąp starsze pliki CAB nowych plików CAB.

8. Przekaż zaktualizowany plik HelpInfo XML do lokalizacji, która jest określona przez **HelpInfoUri** klucza w manifeście modułu. Zastąp starszy plik HelpInfo XML za pomocą nowego pliku.