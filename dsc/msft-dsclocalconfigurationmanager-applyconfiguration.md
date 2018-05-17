---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager

Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.

Jeśli nie istnieje konfiguracja oczekujących, ta metoda przywrócenie bieżącej konfiguracji.


## <a name="syntax"></a>Składnia
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametry
----------

*Wymuś* \[w\] Jeśli jest to **true**, stosowana bieżącej konfiguracji, nawet jeśli istnieje oczekująca konfiguracja.

## <a name="return-value"></a>Wartość zwracana
------------

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

To jest metodą statyczną.

## <a name="requirements"></a>Wymagania
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Zobacz też


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)