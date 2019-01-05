---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048458"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager

Usuwa pliki konfiguracji.

## <a name="syntax"></a>Składnia

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parametry

*Etap* \[w\] Określa, które dokumentu konfiguracji do usunięcia. Następujące wartości są prawidłowe:

|Wartość |Opis |
|:--- |:---|
|**1** | **Bieżącego** dokumentu konfiguracji (current.mof). |
|**2** | **Oczekujące** dokumentu konfiguracji (pending.mof).  |
|**4** | **Wstecz** dokumentu konfiguracji (previous.mof). |

*Wymuś* \[w\] **true** wymusić usunięcie konfiguracji.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)