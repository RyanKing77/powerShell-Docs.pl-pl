---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania usługi Konfiguracja DSC
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurowanie klienta ściągania usługi Konfiguracja DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

> [!IMPORTANT]
> Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości. Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL lub pliku w lokalizacji, gdzie można skontaktować się z serwerem ściągania można pobrać konfiguracji i zasobów, a ma wysyłać dane raportu.

W poniższych tematach opisano sposób skonfigurować klientów ściągania:

* [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)
* [Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)

> **Uwaga**: te tematy dotyczą PowerShell 5.0. Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).