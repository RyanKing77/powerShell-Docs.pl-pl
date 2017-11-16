---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 4a2dfd651f1c74e7441e5f5e357c1c26453adc07
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="software-inventory-logging-sil"></a>Spis oprogramowania Logging (SIL)

** Ważne: ** *podczas instalowania WMF 5.0 na serwerem systemu Windows Server 2012 R2, który jest już uruchomiona SIL, jest trzeba uruchomić polecenie cmdlet Start-SilLogging raz po zainstalowaniu pakietu WMF, ponieważ proces instalacji błędnie przestanie oprogramowania Funkcja rejestrowania spisu.*

Rejestrowanie spisu oprogramowania pozwala zmniejszyć koszty operacyjne uzyskiwania dokładnych informacji o oprogramowaniu firmy Microsoft zainstalowane lokalnie na serwerze, a zwłaszcza na wielu serwerach w środowisku INFORMATYCZNYM (zakładając, że oprogramowanie jest zainstalowane i uruchomione w środowisku INFORMATYCZNYM). Podany został on skonfigurowany, można przekazywanie tych danych na serwer agregujący i zbieranie danych dziennika w jednym miejscu przy użyciu procesu jednolite, automatyczne.

Choć można również rejestrować dane spisu oprogramowania przez bezpośrednie wysyłanie zapytań każdego komputera, rejestrowania spisu oprogramowania wykorzystanie przekazywania (przez sieć) inicjowanego przez poszczególne serwery pozwala uniknąć przez serwer odnajdywania wyzwania, które są typowe dla wielu scenariuszach inwentaryzacji oprogramowania i zasobów zarządzania. Rejestrowanie spisu oprogramowania używa protokołu SSL do zabezpieczania danych, który jest przekazywany za pośrednictwem protokołu HTTPS na serwer agregujący. Przechowywanie danych w jednym miejscu sprawia, że dane ułatwiają analizowanie, manipulowanie nimi oraz udostępniania, gdy jest to konieczne.

Żadne z tych danych nie są przesyłane do firmy Microsoft w ramach działania tej funkcji. Dane i funkcje Rejestrowania spisu oprogramowania są przeznaczone wyłącznie do użytku administratorów i licencjonowanych właścicieli oprogramowania serwera.

Aby uzyskać więcej informacji oraz dokumentację poleceń cmdlet z rejestrowania spisu oprogramowania, zobacz zasoby online Windows Server 2012 R2 w <http://technet.microsoft.com/library/dn383584.aspx>.

