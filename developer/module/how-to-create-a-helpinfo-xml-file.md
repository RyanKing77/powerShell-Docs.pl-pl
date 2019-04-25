---
title: Jak utworzyć plik HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082417"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Jak utworzyć plik XML HelpInfo

Ten temat w tej sekcji wyjaśniono, jak tworzyć i wypełniać plik informacji pomocy, powszechnie znane jako "HelpInfo plikiem XML," dla funkcji programu Windows PowerShell aktualizowalnej pomocy.

## <a name="helpinfo-xml-file-overview"></a>Omówienie plików HelpInfo XML

Plik HelpInfo XML jest podstawowym źródłem informacji na temat aktualizowalnej pomocy dla modułu. Zawiera lokalizację plików pomocy dla modułów, obsługiwanych kultur interfejsu użytkownika i numer wersji, które aktualizowalnej pomocy używa w celu ustalenia, czy użytkownik ma najnowszych plików pomocy.

Każdy moduł ma tylko jeden plik HelpInfo XML, nawet jeśli moduł zawiera wiele plików pomocy dla różnych kultur interfejsu użytkownika. Autora modułu tworzy plik HelpInfo XML i umieszcza je w lokalizacji internetowej, który jest określony przez **HelpInfoUri** klucza w manifeście modułu. Gdy moduł pliki pomocy są aktualizowane i przekazać, autora modułu aktualizuje plik HelpInfo XML i zastępuje oryginalny plik HelpInfo XML nowej wersji.

Koniecznie dokładnie utrzymania pliku HelpInfo XML. Jeśli przekazywanie nowych plików, ale nie pamięta ma zostać zwiększony wersji aktualizowalnej pomocy nie pobierze nowych plików na komputerach użytkowników. Jeśli dodasz plików pomocy dla nowych kultura interfejsu użytkownika, ale nie należy zaktualizować plik HelpInfo XML lub umieścić go w poprawnej lokalizacji, aktualizowalnej pomocy nie pobierze nowe pliki.

## <a name="in-this-section"></a>W tej sekcji

Ta sekcja zawiera następujące tematy.

- [Schemat HelpInfo XML](./helpinfo-xml-schema.md)

- [HelpInfo XML przykładowy plik](./helpinfo-xml-sample-file.md)

- [Jak nazwać plik HelpInfo XML](./how-to-name-a-helpinfo-xml-file.md)

- [Jak skonfigurować numery wersji HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Zobacz też

[Obsługa aktualizowalnej pomocy](./supporting-updatable-help.md)