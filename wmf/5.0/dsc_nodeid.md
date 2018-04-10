---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Oddzielanie identyfikatorów konfiguracji i węzłów

## <a name="overview"></a>Przegląd

Aby zapewnić bardziej elastyczne i prostsze środowisko, korzystając z usługi Konfiguracja DSC w trybie ściągania, dodano wiele funkcji w tej wersji. Te funkcje są przeznaczone do może być elastyczność w prosty sposób instalacji i wdrażanie konfiguracji na wielu węzłach śledzenie stanu i indywidualnie raportowania informacji dla każdego węzła.
Te funkcje są następujące:

* Nazwa konfiguracji, który identyfikuje konfiguracji na komputerze. Ta nazwa może być współużytkowane przez wiele węzłów docelowych
* Identyfikator agenta, które jednoznacznie identyfikuje jeden węzeł
* Krok rejestracji, który występuje tylko po raz pierwszy węzeł docelowy łączy się z serwerem ściągania

**Uwaga:** te funkcje i możliwości zostały dodane, a nie zastępują istniejące funkcje ściągania i pojęcia. Możesz użyć tych nowych funkcji lub starsze z nowym serwerem ściągania wysyłania w tej wersji.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)