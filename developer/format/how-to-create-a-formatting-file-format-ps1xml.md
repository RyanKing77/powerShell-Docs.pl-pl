---
title: Jak utworzyć plik formatowania (. format.ps1xml) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851688"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Jak utworzyć plik formatujący (.format.ps1xml)

W tym temacie opisano sposób tworzenia pliku formatowania (. format.ps1xml).

> [!NOTE]
> Można również utworzyć plik formatowania przez skopiowanie jednego z plików udostępniane przez środowisko Windows PowerShell. Możesz utworzyć kopię istniejącego pliku, Usuń istniejące podpisu cyfrowego ale dodanie własnego podpisu do nowego pliku.

### <a name="to-create-a-formatps1xml-file"></a>Aby utworzyć. format.ps1xml pliku.

1. Utwórz plik tekstowy (txt) przy użyciu tekstu edytora, takiego jak Notatnik.

2. Skopiuj następujące wiersze do formatowania pliku.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - \<Konfiguracji >\</Configuration > Znaczniki określają główne `Configuration` węzła. Wszystkie dodatkowe znaczniki XML będzie ujęte w ramach tego węzła.

   - <ViewDefinitions> </ViewDefinitions> Tagi definiują `ViewDefinitions` węzła. Wszystkie widoki są definiowane w tym węźle.

3. Zapisz plik do folderu instalacyjnego programu Windows PowerShell, do folderu modułu lub podfolder folderu modułu. Użyj następującego formatu nazwy, podczas zapisywania pliku: `MyFile.format.ps1xml`. Należy użyć plików formatowania `.format.ps1xml` rozszerzenia.

   Teraz można przystąpić do dodawania widoków do formatowania pliku. Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania. Aby dodać pojedynczego widoku dla każdego obiektu, wielu widoków do tego samego obiektu lub pojedynczy widok, który jest używany przez wielu obiektów.

## <a name="see-also"></a>Zobacz też

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
