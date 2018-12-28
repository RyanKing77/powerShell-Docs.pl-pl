---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404711"
---
>Dotyczy: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Klucz rejestru DSCAutomationHostEnabled

Zastosowań DSC **DSCAutomationHostEnabled** klucza rejestru w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** umożliwiające konfigurację maszyny podczas początkowego rozruchu.
DSCAutomationHostEnabled obsługuje trzy tryby:

|  Wartość DSCAutomationHostEnabled  |  Opis   |
|---|---|
0 | Wyłącz Konfigurowanie maszyny podczas rozruchu. |
1 | Włączanie, konfigurowanie maszyny podczas rozruchu. |
2 | Włączanie, konfigurowanie maszyny, tylko wtedy, gdy trwa DSC oczekujące na zatwierdzenie lub bieżącego stanu. Jest to wartość domyślna. |

## <a name="see-also"></a>Zobacz też

Na przykład jak ta funkcja służy do konfiguracji uruchamiania podczas początkowego rozruchu zobacz [skonfigurować maszyny wirtualnej podczas początkowego rozruchu przy użyciu DSC](bootstrapDsc.md).