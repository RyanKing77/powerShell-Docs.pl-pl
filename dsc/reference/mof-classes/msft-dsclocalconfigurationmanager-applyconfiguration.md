---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048366"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager

Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.

Jeśli nie ma nic do czasu, ta metoda przywrócenie bieżącej konfiguracji.

## <a name="syntax"></a>Składnia

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametry

*Wymuś* \[w\] Jeśli jest to **true**, bieżąca konfiguracja jest ponownie stosowana, nawet jeśli istnieje oczekująca konfiguracja.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)