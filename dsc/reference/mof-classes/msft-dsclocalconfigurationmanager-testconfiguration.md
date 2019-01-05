---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048397"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager

Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.

## <a name="syntax"></a>Składnia

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametry

*configurationData* \[w\] confuguration dane środowisko.

*InDesiredState* \[się\] przy powrocie, określa, czy zarządzany węzeł jest w stanie określone przez dokumentu konfiguracji.

*ResourcesInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasę, która określa zasoby, które znajdują się w żądanym stanie.

*ResourcesNotInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasę, która określa zasoby, które nie znajdują się w żądanym stanie.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)