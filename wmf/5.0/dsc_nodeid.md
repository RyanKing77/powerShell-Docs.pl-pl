---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188289"
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
