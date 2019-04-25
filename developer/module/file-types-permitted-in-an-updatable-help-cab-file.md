---
title: Plik CAB pomocy typów plików dozwolonych w aktualizowalnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082451"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Typy plików dozwolonych w pliku CAN aktualizowalnej pomocy

Ten temat wymieniono i opisano wymagania zawartości plików CAB pomocy nadaje się do aktualizacji.

## <a name="updatable-help-cab-file-requirements"></a>Wymagania pliku CAB aktualizowalnej pomocy

Zawartość pliku CAB bez kompresji jest ograniczona do 1 GB domyślnie. Aby obejść to ograniczenie, użytkownicy muszą użyć **życie** parametru [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) polecenia cmdlet.

Aby zapewnić bezpieczeństwo plików pomocy, które są pobierane z Internetu, plik CAB pomocy nadaje się do aktualizacji może zawierać tylko typy plików, które są wymienione poniżej. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia cmdlet sprawdza wszystkie pliki względem schematów tematu Pomocy. Jeśli `Update-Help` polecenia cmdlet napotka pliku, który jest nieprawidłowy lub nie jest dozwolony typ, nie można zainstalować nieprawidłowy plik i zatrzymuje się instalowanie plików z pliku CAB na komputerze użytkownika.

- Oparte na języku XML tematy pomocy dla poleceń cmdlet.

- Oparte na języku XML tematy pomocy dla skryptów i funkcji.

- Oparte na języku XML tematy pomocy dla dostawców środowiska Windows PowerShell.

- Oparte na tekście tematy pomocy, takich jak tematy.

[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) sprawdza zawartość pliku CAB, które go wypakowuje zespół zarządzający zmianami. Jeśli `Update-Help` umożliwia znalezienie pliku niezgodne typy w pliku CAB pomocy nadaje się do aktualizacji, generuje błąd i zatrzymuje operację. Nie instaluje żadnych plików pomocy z pliku CAB, nawet te o typach zgodnych plików.