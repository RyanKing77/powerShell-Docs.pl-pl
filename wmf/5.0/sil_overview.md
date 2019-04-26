---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085018"
---
# <a name="software-inventory-logging-sil"></a>Rejestrowanie spisu oprogramowania (SIL)

**WAŻNE:** *Podczas instalowania programu WMF 5.0 na serwerem systemu Windows Server 2012 R2, który jest już uruchomiony program SIL, jest niezbędne do uruchomienia polecenia cmdlet Start-SilLogging raz po zainstalowaniu programu WMF, ponieważ proces instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.*

Rejestrowanie spisu oprogramowania pozwala zmniejszyć koszty operacyjne uzyskiwania dokładnych informacji na temat oprogramowania firmy Microsoft zainstalowane lokalnie na serwerze, a zwłaszcza na wielu serwerach w środowisku INFORMATYCZNYM (zakładając, że oprogramowanie jest zainstalowane i uruchomione w środowisku INFORMATYCZNYM). Pod warunkiem jeden jest skonfigurowana, możesz przekazywanie tych danych do serwera agregacji i zbieranie danych dziennika w jednym miejscu przy użyciu procesu jednolite, automatyczne.

Gdy danych spisu oprogramowania można również rejestrować przez bezpośrednie wysyłanie zapytań każdego komputera, rejestrowanie spisu oprogramowania przez wprowadzenie przekazywania (przez sieć) inicjowanego przez poszczególne serwery pozwala uniknąć wyzwania dotyczące odnajdywania serwera, które są typowe dla wielu scenariuszach inwentaryzacji oprogramowania i zasobów zarządzania. Rejestrowanie spisu oprogramowania używa protokołu SSL do zabezpieczania danych, który jest przekazywany za pośrednictwem protokołu HTTPS do serwera agregacji. Przechowywanie danych w jednym miejscu ułatwia analizowanie, manipulowanie i udostępniania, gdy jest to konieczne.

Żadne z tych danych są wysyłane do firmy Microsoft w ramach działania tej funkcji. Dane i funkcje Rejestrowania spisu oprogramowania są przeznaczone wyłącznie do użytku administratorów i licencjonowanych właścicieli oprogramowania serwera.

Aby uzyskać więcej informacji oraz dokumentacji dotyczącej poleceń cmdlet funkcji rejestrowania spisu oprogramowania, zobacz zasoby online w systemie Windows Server 2012 R2 w <http://technet.microsoft.com/library/dn383584.aspx>.
