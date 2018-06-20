---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189741"
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