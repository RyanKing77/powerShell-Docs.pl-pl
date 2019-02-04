---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania DSC
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687258"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurowanie klienta ściągania DSC

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podanej lokalizacji adresu URL lub pliku, gdzie można skontaktować się z serwera ściągania konfiguracji i zasobów, a jego powinien wysyłać dane raportu.

W poniższych tematach opisano sposób konfigurowania klientów ściągnięcia:

* [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)
* [Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)

> **Uwaga**: Następujące tematy dotyczą PowerShell 5.0. Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).