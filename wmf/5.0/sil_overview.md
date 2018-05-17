---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4bfedd585958f84889954bd9ee022ea47ac191b2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="software-inventory-logging-sil"></a>Rejestrowanie spisu oprogramowania (SIL)

** Ważne: ** *podczas instalowania WMF 5.0 na serwerem systemu Windows Server 2012 R2, który jest już uruchomiona SIL, jest trzeba uruchomić polecenie cmdlet Start-SilLogging raz po zainstalowaniu pakietu WMF, ponieważ proces instalacji błędnie przestanie oprogramowania Funkcja rejestrowania spisu.*

Rejestrowanie spisu oprogramowania pozwala zmniejszyć koszty operacyjne uzyskiwania dokładnych informacji o oprogramowaniu firmy Microsoft zainstalowane lokalnie na serwerze, a zwłaszcza na wielu serwerach w środowisku INFORMATYCZNYM (zakładając, że oprogramowanie jest zainstalowane i uruchomione w środowisku INFORMATYCZNYM). Podany został on skonfigurowany, można przekazywanie tych danych na serwer agregujący i zbieranie danych dziennika w jednym miejscu przy użyciu procesu jednolite, automatyczne.

Choć można również rejestrować dane spisu oprogramowania przez bezpośrednie wysyłanie zapytań każdego komputera, rejestrowania spisu oprogramowania wykorzystanie przekazywania (przez sieć) inicjowanego przez poszczególne serwery pozwala uniknąć przez serwer odnajdywania wyzwania, które są typowe dla wielu scenariuszach inwentaryzacji oprogramowania i zasobów zarządzania. Rejestrowanie spisu oprogramowania używa protokołu SSL do zabezpieczania danych, który jest przekazywany za pośrednictwem protokołu HTTPS na serwer agregujący. Przechowywanie danych w jednym miejscu sprawia, że dane ułatwiają analizowanie, manipulowanie nimi oraz udostępniania, gdy jest to konieczne.

Żadne z tych danych nie są przesyłane do firmy Microsoft w ramach działania tej funkcji. Dane i funkcje Rejestrowania spisu oprogramowania są przeznaczone wyłącznie do użytku administratorów i licencjonowanych właścicieli oprogramowania serwera.

Aby uzyskać więcej informacji oraz dokumentację poleceń cmdlet z rejestrowania spisu oprogramowania, zobacz zasoby online Windows Server 2012 R2 w <http://technet.microsoft.com/library/dn383584.aspx>.
