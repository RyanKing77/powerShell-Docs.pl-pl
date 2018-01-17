---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio. Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.

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


 

 



