---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
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


 

 



