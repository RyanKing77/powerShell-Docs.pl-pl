---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Rejestrowanie spisu oprogramowania (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856168"
---
# <a name="software-inventory-logging-sil"></a>Rejestrowanie spisu oprogramowania (SIL)

> [!IMPORTANT]
> Podczas instalacji programu WMF 5.x na serwerem systemu Windows Server 2012 R2, który jest już uruchomiony program SIL, należy uruchomić polecenie cmdlet Start-SilLogging raz po zakończeniu instalacji programu WMF zgodnie z procesem instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.

Rejestrowanie spisu oprogramowania pozwala zmniejszyć koszty operacyjne uzyskiwania dokładnych informacji na temat oprogramowania firmy Microsoft zainstalowane lokalnie na serwerze, a zwłaszcza na wielu serwerach w środowisku INFORMATYCZNYM (zakładając, że oprogramowanie jest zainstalowane i uruchomione w środowisku INFORMATYCZNYM). Pod warunkiem jeden jest skonfigurowana, możesz przekazywanie tych danych do serwera agregacji i zbieranie danych dziennika w jednym miejscu przy użyciu procesu jednolite, automatyczne.

Gdy danych spisu oprogramowania można również rejestrować przez bezpośrednie wysyłanie zapytań każdego komputera, rejestrowanie spisu oprogramowania przez wprowadzenie przekazywania (przez sieć) inicjowanego przez poszczególne serwery pozwala uniknąć wyzwania dotyczące odnajdywania serwera, które są typowe dla wielu scenariuszach inwentaryzacji oprogramowania i zasobów zarządzania. Rejestrowanie spisu oprogramowania używa protokołu SSL do zabezpieczania danych, który jest przekazywany za pośrednictwem protokołu HTTPS do serwera agregacji. Przechowywanie danych w jednym miejscu ułatwia analizowanie, manipulowanie i udostępniania, gdy jest to konieczne.

Żadne z tych danych są wysyłane do firmy Microsoft w ramach działania tej funkcji. Dane i funkcje Rejestrowania spisu oprogramowania są przeznaczone wyłącznie do użytku administratorów i licencjonowanych właścicieli oprogramowania serwera.

Aby uzyskać więcej informacji oraz dokumentacji dotyczącej poleceń cmdlet funkcji rejestrowania spisu oprogramowania, zobacz [Zarządzanie rejestrowanie spisu oprogramowania w systemie Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
