---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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

*Typ zasobu* \[w\]  
Nazwa zasobu do wywołania.

*Nazwa modułu* \[w\]  
Nazwa modułu, który zawiera zasób do wywołania.

*Właściwość resourceProperty* \[w\]  
Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio. Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.

*konfiguracje* \[out\]  
Przy powrocie zawiera osadzony wystąpienia konfiguracji.

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


 

 



