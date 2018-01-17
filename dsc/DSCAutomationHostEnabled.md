---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Klucz rejestru DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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


