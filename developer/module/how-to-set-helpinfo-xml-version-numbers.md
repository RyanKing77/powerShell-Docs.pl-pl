---
title: Jak skonfigurować numery wersji HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851933"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Jak konfigurować numery wersji pliku XML HelpInfo

W tym temacie wyjaśniono, jak ustawić i zwiększyć numery wersji w pliku nadaje się do aktualizacji informacji pomocy, powszechnie znane jako "plik HelpInfo XML".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Jak konfigurować numery wersji pliku XML HelpInfo

Numery wersji w pliku HelpInfo XML są krytyczne dla działania aktualizowalnej pomocy. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) poleceń cmdlet Pobierz nowe pliki pomocy, tylko wtedy, gdy jest to numer wersji dla kultury interfejsu użytkownika w pliku HelpInfo XML zdalnego jest większy niż numer wersji dla tej kultury interfejsu użytkownika w lokalne HelpInfo XML, lub nie ma pliku lokalnego HelpInfo XML.
Numery wersji w pliku HelpInfo XML są krytyczne dla działania aktualizowalnej pomocy. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) poleceń cmdlet Pobierz nowe pliki pomocy, tylko wtedy, gdy jest to numer wersji dla kultury interfejsu użytkownika w pliku HelpInfo XML zdalnego jest większy niż numer wersji dla tej kultury interfejsu użytkownika w lokalne HelpInfo XML, lub nie ma pliku lokalnego HelpInfo XML.

Plik HelpInfo XML używa numeru wersji część 4, która jest zdefiniowana w **System.Version** klasy programu Microsoft .NET Framework. Format jest `N1.N2.N3.N4`. Autorzy modułów można użyć dowolnej wersji schematu, który jest dozwolony przez numerowania **System.Version** klasy. Aktualizowalnej pomocy wymaga tylko numer wersji do zwiększenia kultury interfejsu użytkownika po przekazaniu nowej wersji pliku CAB dla tej kultury interfejsu użytkownika do lokalizacji, która jest określona przez **HelpContentURI** elementu w pliku HelpInfo XML.

Poniższy kod przedstawia elementów pliku HelpInfo XML dla kultury niemiecki (de-DE) interfejsu użytkownika, gdy wersja jest 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Numer wersji, kultury interfejsu użytkownika odzwierciedla wersję pliku CAB dla tej kultury interfejsu użytkownika. Numer wersji ma zastosowanie do całego pliku CAB. Numery wersji różne dla różnych plików nie można ustawić w pliku CAB. Numer wersji dla każdej kultury interfejsu użytkownika jest szacowana osobno i nie muszą być związane z numerami wersji dla innych języków interfejsu użytkownika, obsługiwanych przez moduł.