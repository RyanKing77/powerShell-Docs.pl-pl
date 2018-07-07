---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893947"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager

Pobiera dane wyjściowe agenta konfiguracji skojarzone z określonego zadania.

## <a name="syntax"></a>Składnia

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parametry

*jobId* \[w\] identyfikator zadania, dla którego należy pobrać dane wyjściowe.

*resumeOutputBookmark* \[w\] Określa, że dane wyjściowe powinny być kontynuacji poprzedniej zakładki.

*dane wyjściowe* \[się\] danych wyjściowych dla określonego zadania.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**Plik MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)