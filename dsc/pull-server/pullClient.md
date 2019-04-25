---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania platformy DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079646"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurowanie klienta ściągania platformy DSC

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podanej lokalizacji adresu URL lub pliku, gdzie można skontaktować się z serwera ściągania konfiguracji i zasobów, a jego powinien wysyłać dane raportu.

W poniższych tematach opisano sposób konfigurowania klientów ściągnięcia:

* [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)
* [Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)

> [!NOTE]
> Następujące tematy dotyczą PowerShell 5.0. Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).