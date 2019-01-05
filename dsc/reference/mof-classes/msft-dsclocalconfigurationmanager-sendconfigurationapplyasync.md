---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048452"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager

Wysyła asynchronicznie zarządzany węzeł dokumentu konfiguracji i używa agenta konfiguracji, aby zastosować konfigurację.

## <a name="syntax"></a>Składnia

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametry

*ConfigurationData* \[w\] danych środowiska dla konfiguracji.

*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.

*jobId* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)