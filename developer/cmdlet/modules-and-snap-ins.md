---
title: Modułów i przystawek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849959"
---
# <a name="modules-and-snap-ins"></a>Moduły i przystawki

Polecenia cmdlet można dodać do sesji przy użyciu przystawki lub modułów (rozpoczętymi przez program Windows PowerShell 2.0). Gdy polecenie cmdlet jest dodawany do sesji, która może być uruchamiane programowo przez aplikację hosta lub interaktywnie w wierszu polecenia.

Zaleca się używać modułów jako metodę dostarczania dodanie polecenia cmdlet w sesji z następujących powodów:

- Moduły umożliwiają dodanie polecenia cmdlet, ładując zestaw gdzie polecenie cmdlet został zdefiniowany. Nie ma potrzeby wdrażania klasy przystawki.

- Moduły umożliwiają dodanie innych zasobów, takich jak zmienne, funkcje, skrypty, typy i formatowania plików i inne.

- Przystawki można jedynie dodać polecenia cmdlet i dostawców do sesji.

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
