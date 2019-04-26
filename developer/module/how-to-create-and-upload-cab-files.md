---
title: Jak utworzyć i przekazać pliki CAB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082383"
---
# <a name="how-to-create-and-upload-cab-files"></a>Jak utworzyć i przekazać pliki CAB

W tym temacie opisano sposób tworzenia plików CAB pomocy nadaje się do aktualizacji i przekazać je do lokalizacji, w którym aktualizowalnej pomocy polecenia cmdlet można je znaleźć.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Jak utworzyć i przekazać pliki CAB aktualizowalnej pomocy

Funkcja aktualizowalnej pomocy umożliwia dostarczanie plików nowych lub zaktualizowanych pomocy dla modułu w wielu języków i kultur. Pakiet aktualizowalnej pomocy dla modułu zawiera jeden plik HelpInfo XML i co najmniej jeden plik cabinet (. Pliki CAB). Każdy plik CAB zawiera pliki pomocy dla modułu w jednej kultury interfejsu użytkownika. Użyj poniższej procedury, aby utworzyć pliki CAB dla aktualizowalnej pomocy.

1. Organizowanie plików pomocy dla modułu przez kulturę interfejsu użytkownika. Każdy plik CAB pomocy można aktualizować zawiera pliki pomocy jeden moduł w jednej kultury interfejsu użytkownika. Można dostarczać pomocy wiele plików CAB dla modułu, każdy dla innego kultura interfejsu użytkownika.

2. Sprawdź ułatwiające plików obejmują tylko typy plików, które są dozwolone dla aktualizowalnej pomocy i je zweryfikować względem schematu pliku pomocy. Jeśli `Update-Help` polecenia cmdlet napotka pliku, który jest nieprawidłowy lub nie jest dozwolony typ, nie można zainstalować nieprawidłowy plik i zatrzymuje się instalowanie plików z zespół zarządzający zmianami. Aby uzyskać listę typów plików dozwolonych zobacz [pliku typy dozwolone w nadaje się do aktualizacji pliku CAB pomocy](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Cyfrowe podpisywanie plików pomocy. Podpisy cyfrowe nie są wymagane, ale są one najlepszym rozwiązaniem.

4. Obejmuje wszystkie pomocy kultury i nie tylko te pliki, które są nowe lub zostały zmienione w plikach dla modułu w interfejsie użytkownika. Jeśli plik CAB jest niekompletna, użytkownicy, którzy pobrać pliki pomocy po raz pierwszy lub nie pobieraj Każda aktualizacja nie ma wszystkich plików pomocy modułu.

5. Przy użyciu narzędzia, która tworzy pliki cab, takie jak MakeCab.exe. Programu Windows PowerShell nie obejmuje polecenia cmdlet, które tworzenia plików CAB.

6. Nazwy plików CAB. Aby uzyskać więcej informacji, zobacz [sposobu nazywania nadaje się do aktualizacji pliku CAB pomocy](./how-to-name-an-updatable-help-cab-file.md).

7. Przekaż pliki CAB modułu do lokalizacji, która jest określona przez **HelpContentUri** elementu w pliku HelpInfo XML dla modułu. Następnie przekaż plik HelpInfo XML do lokalizacji, która jest określona przez **HelpInfoUri** klucza manifestu modułu. **HelpContentUri** i **HelpInfoUri** można wskazać w tej samej lokalizacji.

> [!CAUTION]
> Wartość **HelpInfoUri** klucza i **HelpContentUri** element musi zaczynać się od "http" lub "https". Wartość musi wskazywać lokalizacji internetowej i nie może zawierać nazwę pliku.