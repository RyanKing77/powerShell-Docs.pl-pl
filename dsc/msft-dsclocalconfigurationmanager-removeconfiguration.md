---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager

Usuwa pliki konfiguracji.

<a name="syntax"></a>Składnia
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parametry
----------

*Etap* \[w\] Określa, który dokument konfiguracji do usunięcia. Prawidłowe są następujące wartości:

|Wartość |Opis |
|:--- |:---|
|**1** | **Bieżącego** dokumentu konfiguracji (current.mof). |
|**2** | **Oczekujące** dokumentu konfiguracji (pending.mof).  |
|**4** | **Wstecz** dokumentu konfiguracji (previous.mof). |

*Wymuś* \[w\] **true** wymuszenie usunięcia konfiguracji.

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