---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058203"
---
# <a name="separation-of-node-and-configuration-ids"></a>Oddzielanie identyfikatorów konfiguracji i węzłów

## <a name="overview"></a>Omówienie

Aby zapewnić bardziej elastyczne i usprawnione środowisko, gdy usługi DSC w trybie ściągnięcia, dodaliśmy wiele funkcji w tej wersji. Funkcje te mają na celu umożliwiają elastyczne łatwe konfigurowanie i wdrażanie konfiguracji w wielu węzłach stan śledzenia i raportowania informacji dla każdego węzła indywidualnie.
Te funkcje są następujące:

* Nazwa konfiguracji, który identyfikuje konfiguracji na komputerze. Ta nazwa może być współużytkowany przez wiele węzłów docelowych
* Identyfikator agenta, które jednoznacznie identyfikuje jeden węzeł
* Krok rejestracji, który występuje tylko po raz pierwszy węzeł docelowy łączy się z serwerem ściągania

**Uwaga:** Te funkcje i możliwości zostały dodane, a nie zastępują istniejące ściągnięcia funkcje i pojęcia. Można użyć tych nowych funkcji lub starsze z nowym serwerem ściągania wysyłania w tej wersji.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
