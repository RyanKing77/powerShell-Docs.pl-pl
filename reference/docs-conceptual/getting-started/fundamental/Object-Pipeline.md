---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Potok obiektów
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948214"
---
# <a name="object-pipeline"></a>Potok obiektów
Potoki działać tak jak seria połączonych segmentów potoku. Przenoszenie do potoku elementów przechodzą przez każdy z segmentów. Aby utworzyć potok w programie Windows PowerShell, należy połączyć polecenia wraz z operatora potoku "|". Dane wyjściowe każdego polecenia jest używane jako dane wejściowe do następnego polecenia.

Potoki są raczej pojęcie najbardziej przydatna używane w interfejsach wiersza polecenia. Poprawnie potoki nie tylko zmniejszyć nakład wprowadzania złożonych poleceń, jednak również ułatwić Zobacz przepływ pracy w poleceniach. Powiązane, przydatne cech potoki jest, że ponieważ działają na każdym elemencie oddzielnie, nie trzeba zmodyfikować je na podstawie tego, czy będzie mają wartość zero, jeden lub wiele elementów w potoku. Ponadto każdy polecenie w potoku (nazywane element potoku) zwykle przekazuje dane wyjściowe do następne polecenie w potoku elementu elemencie. To zwykle powoduje zmniejszenie zapotrzebowania na zasoby złożonych poleceń oraz umożliwia można zacząć od razu uzyskiwanie danych wyjściowych.

W tym rozdziale firma Microsoft będzie opisano, jak potoku środowiska Windows PowerShell różni się od potoki w liczbie najpopularniejszych powłok i pokazują, niektóre podstawowe narzędzia umożliwiające pomocy formantu potoku w danych wyjściowych i zobacz, jak działa potoku.