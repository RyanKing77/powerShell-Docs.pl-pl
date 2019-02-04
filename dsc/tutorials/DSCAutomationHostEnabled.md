---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684801"
---
>Dotyczy: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Klucz rejestru DSCAutomationHostEnabled

Zastosowań DSC **DSCAutomationHostEnabled** klucza rejestru w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** umożliwiające konfigurację na komputerze pod adresem początkowym rozruchu.
**DSCAutomationHostEnabled** obsługuje trzy tryby:

|  Wartość DSCAutomationHostEnabled  |  Opis   |
|---|---|
0 | Wyłącz Konfigurowanie maszyny podczas rozruchu. |
1 | Włączanie, konfigurowanie maszyny podczas rozruchu. |
2 | Włączanie, konfigurowanie maszyny, tylko wtedy, gdy trwa DSC oczekujące na zatwierdzenie lub bieżącego stanu. Jest to wartość domyślna. |

## <a name="see-also"></a>Zobacz też

Na przykład jak ta funkcja służy do konfiguracji uruchamiania podczas początkowego rozruchu zobacz [skonfigurować maszyny wirtualnej podczas początkowego rozruchu przy użyciu DSC](bootstrapDsc.md).
