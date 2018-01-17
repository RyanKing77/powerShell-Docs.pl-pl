---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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

*Etap* \[w\]  
Określa, który dokument konfiguracji do usunięcia. Prawidłowe są następujące wartości:

|Wartość |Opis |
|:--- |:---|
|**1** | **Bieżącego** dokumentu konfiguracji (current.mof). |
|**2** | **Oczekujące** dokumentu konfiguracji (pending.mof).  |
|**4** | **Wstecz** dokumentu konfiguracji (previous.mof). |

*Wymuś* \[w\]  
**wartość true,** wymuszenie usunięcia konfiguracji.

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


 

 



