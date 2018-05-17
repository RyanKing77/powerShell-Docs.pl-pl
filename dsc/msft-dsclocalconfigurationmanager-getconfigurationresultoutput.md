---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager

Pobiera dane wyjściowe Agent konfiguracji skojarzone z danego zadania.

<a name="syntax"></a>Składnia
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parametry
----------

*Identyfikator zadania* \[w\] identyfikator zadania, dla którego można pobrać danych wyjściowych.

*resumeOutputBookmark* \[w\] Określa, czy dane wyjściowe powinny być kontynuacja z poprzedniej zakładki.

*dane wyjściowe* \[limit\] produktu wyjściowego dla określonego zadania.

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