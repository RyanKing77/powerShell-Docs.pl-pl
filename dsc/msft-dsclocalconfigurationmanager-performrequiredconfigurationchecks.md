---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager

Uruchamia sprawdzanie spójności za pomocą harmonogramu zadań.

<a name="syntax"></a>Składnia
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parametry
----------

*Flagi* \[w\]  
Maska bitowa określający typ uruchamianie sprawdzania spójności. Następujące wartości są prawidłowe i mogą być łączone przy użyciu bitowej **lub** operacji:

|Wartość |Opis |
|:--- |:---|
|**1** | Sprawdzanie spójności normalnego. |
|**2** | Kontynuacja sprawdzania spójności po ponownym rozruchu. Tej wartości nie powinny być połączone z innych wartości. |
|**4** | Konfiguracja powinna pobierane z serwera ściągania określone w metakonfigurację dla węzła. Ta wartość powinna być zawsze połączone z **1**, dla wartości **5**. |
|**8** | Wyślij stanu na serwerze raportów. |

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


 

 



