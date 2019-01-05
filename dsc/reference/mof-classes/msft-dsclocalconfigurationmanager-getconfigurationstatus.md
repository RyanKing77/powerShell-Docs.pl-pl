---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048505"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager

Pobieranie historii stanu konfiguracji.

## <a name="syntax"></a>Składnia

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parametry

*Wszystkie* \[w\] **true** Jeśli ta metoda powinna zwrócić informacje na temat wszystkich konfiguracji jest uruchamiana na komputerze, łącznie z konfiguracji aplikacji i sprawdzanie spójności.

*configurationStatus* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasę, która definiuje ustawienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)