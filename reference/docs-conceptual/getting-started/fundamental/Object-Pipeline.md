---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt potoku
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a>Obiekt potoku
Potoki działać tak jak seria połączonych segmentów potoku. Przenoszenie do potoku elementów przechodzą przez każdy z segmentów. Aby utworzyć potok w programie Windows PowerShell, należy połączyć polecenia wraz z operatora potoku "|". Dane wyjściowe każdego polecenia jest używane jako dane wejściowe do następnego polecenia.

Potoki są raczej pojęcie najbardziej przydatna używane w interfejsach wiersza polecenia. Poprawnie potoki nie tylko zmniejszyć nakład wprowadzania złożonych poleceń, jednak również ułatwić Zobacz przepływ pracy w poleceniach. Powiązane, przydatne cech potoki jest, że ponieważ działają na każdym elemencie oddzielnie, nie trzeba zmodyfikować je na podstawie tego, czy będzie mają wartość zero, jeden lub wiele elementów w potoku. Ponadto każdy polecenie w potoku (nazywane element potoku) zwykle przekazuje dane wyjściowe do następne polecenie w potoku elementu elemencie. To zwykle powoduje zmniejszenie zapotrzebowania na zasoby złożonych poleceń oraz umożliwia można zacząć od razu uzyskiwanie danych wyjściowych.

W tym rozdziale firma Microsoft będzie opisano, jak potoku środowiska Windows PowerShell różni się od potoki w liczbie najpopularniejszych powłok i pokazują, niektóre podstawowe narzędzia umożliwiające pomocy formantu potoku w danych wyjściowych i zobacz, jak działa potoku.

