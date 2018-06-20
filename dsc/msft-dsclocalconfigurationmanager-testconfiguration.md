---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219015"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager

Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.

<a name="syntax"></a>Składnia
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parametry
----------

*configurationData* \[w\] danych środowiska dla confuguration.

*InDesiredState* \[limit\] przy powrocie, określa, czy węzeł zarządzany w stan określony w dokumencie konfiguracji.

*ResourcesInDesiredState* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasy, która określa zasoby, które są w żądanym stanie.

*ResourcesNotInDesiredState* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasy, która określa zasoby, które nie są w żądanym stanie.

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