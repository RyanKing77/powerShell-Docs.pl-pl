---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager

Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.

<a name="syntax"></a>Składnia
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parametry
----------

*Typ zasobu* \[w\] nazwę zasobu do wywołania.

*Nazwa modułu* \[w\] nazwę modułu, który zawiera zasób do wywołania.

*Właściwość resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów jako klucz i wartość, odpowiednio. Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.

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