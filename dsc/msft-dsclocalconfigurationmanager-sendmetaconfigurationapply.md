---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager

Konfiguruje ustawienia lokalny program Configuration Manager, które są używane do sterowania agenta konfiguracji.

<a name="syntax"></a>Składnia
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parametry
----------

*ConfigurationData* \[w\] danych środowiska w konfiguracji.

*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.

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