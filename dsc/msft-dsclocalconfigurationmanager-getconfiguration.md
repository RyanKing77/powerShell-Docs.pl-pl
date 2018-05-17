---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager

Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.

<a name="syntax"></a>Składnia
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Parametry
----------

*configurationData* \[w\] Określa dane konfiguracji do wysłania.

*konfiguracje* \[limit\] przy powrocie, zawiera osadzony wystąpienia konfiguracji.

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