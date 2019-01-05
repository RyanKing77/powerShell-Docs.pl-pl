---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048574"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager

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