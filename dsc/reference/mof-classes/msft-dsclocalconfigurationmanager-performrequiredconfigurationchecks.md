---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda PerformRequiredConfigurationChecks
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734407"
---
# <a name="performrequiredconfigurationchecks-method"></a>Metoda PerformRequiredConfigurationChecks

Uruchamia kontrolę spójności przy użyciu harmonogramu zadań.

## <a name="syntax"></a>Składnia

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parametry

*Flagi* \[w\] maski bitów, który określa typ uruchamianie sprawdzania spójności. Następujące wartości są prawidłowe i mogą być połączone za pomocą bitowej **lub** operacji:

|Wartość |Opis |
|:--- |:---|
|**1** | Sprawdzanie spójności normalny. |
|**2** | Kontynuacja sprawdzania spójności po ponownym uruchomieniu. Ta wartość nie powinny być połączone z inne wartości. |
|**4** | Konfigurację powinny zostać pobrane z serwera ściągania określone w metaconfiguration dla węzła. Wartość ta zawsze powinny być połączone z **1**, dla wartości **5**. |
|**8** | Wyślij stanu na serwerze raportów. |

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
