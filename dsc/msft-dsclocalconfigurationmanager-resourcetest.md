---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager

Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.

<a name="syntax"></a>Składnia
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a>Parametry
----------

*Typ zasobu* \[w\]  
Nazwa zasobu do wywołania.

*Nazwa modułu* \[w\]  
Nazwa modułu, który zawiera zasób do wywołania.

*Właściwość resourceProperty* \[w\]  
Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio. Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.

*InDesiredState* \[out\]  
Przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy jest w żądanym stanie.

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


 

 



