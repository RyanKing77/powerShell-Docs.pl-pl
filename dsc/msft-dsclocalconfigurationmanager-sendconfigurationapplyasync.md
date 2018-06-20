---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186681"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager

Asynchronicznie wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.

<a name="syntax"></a>Składnia
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Parametry
----------

*ConfigurationData* \[w\] danych środowiska w konfiguracji.

*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.

*Identyfikator zadania* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.

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