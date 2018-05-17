---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager

Podgląd historii stanu konfiguracji.

<a name="syntax"></a>Składnia
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametry
----------

*Wszystkie* \[w\] **true** Jeśli ta metoda powinna zwrócić informacje o wszystkich konfiguracji jest uruchamiana na komputerze, w tym aplikacji konfiguracji i sprawdzanie spójności.

*configurationStatus* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasa, która definiuje ustawienia.

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