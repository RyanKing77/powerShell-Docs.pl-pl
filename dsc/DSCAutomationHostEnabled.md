---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221973"
---
>Dotyczy: środowiska Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Klucz rejestru DSCAutomationHostEnabled

Używa DSC **DSCAutomationHostEnabled** klucza rejestru w kluczu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** umożliwiające konfigurację na komputerze pod adresem początkowego rozruchu w górę.
DSCAutomationHostEnabled obsługuje trzy tryby:

|  Wartość DSCAutomationHostEnabled  |  Opis   |
|---|---|
0 | Wyłącz Konfigurowanie komputera na rozruchowego. |
1 | Włącz konfigurowanie komputera na rozruchowego. |
2 | Włącz konfigurowanie maszyny tylko wtedy, gdy trwa DSC oczekujące lub bieżącego stanu. Jest to wartość domyślna. |

## <a name="see-also"></a>Zobacz też

Na przykład sposobu używania tej funkcji do jednocześnie konfiguracje początkowego rozruchu w górę zobacz [Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC](bootstrapDsc.md).