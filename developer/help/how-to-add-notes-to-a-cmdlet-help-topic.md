---
title: Jak dodawać notatki do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851198"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Jak dodać notatki do tematu pomocy dotyczącego polecenia cmdlet

W tej sekcji opisano sposób dodawania sekcja uwagi do tematu pomocy polecenia cmdlet Windows PowerShell®. Sekcję uwag służy do wyjaśnienia szczegółowe informacje, które nie mieszczą się łatwo na inne strukturalne sekcje, takie jak uzyskać bardziej szczegółowy opis parametru. Ta zawartość można dołączyć komentarze dotyczące działania polecenia cmdlet przy użyciu określonego dostawcy, do niektórych zastosowań unikatowy, ale ważne jest, polecenia cmdlet lub sposobów uniknięcia wyświetlania możliwe warunki wystąpienia błędu.

Nie ma ograniczeń liczby uwagi, które można dodać do sekcji Uwagi. Dla każdego notatki, Dodaj parę \<maml:alert > tagi \<maml:alertset > węzła. Zawartość każdego uwaga zostanie dodany w ramach zestawu \<MAML: para > tagów. Użyj pustego \<MAML: para > Znaczniki odstępy.

Pokazano w poniższym XML \<maml:alertset > węzeł o dwie notatki. Zwróć uwagę, że każdy Uwaga ma opcjonalny \<MAML: TITLE > tag (tytuły może służyć do grupowania dowolny zbiór \<maml:alert > tagi), i że każdy Uwaga ma pusty wiersz po zawartości do rozdzielenia.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



