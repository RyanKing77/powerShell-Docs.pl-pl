---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685991"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager

Bezpośrednio wywołuje **testu** metod zasobów DSC.

## <a name="syntax"></a>Składnia

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parametry

*Typ zasobu* \[w\] nazwę zasobu do wywołania.

*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.

*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio. Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.

*InDesiredState* \[się\] przy powrocie, właściwość ta jest równa **true** Jeśli węzeł docelowy jest w żądanym stanie.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

Jest to metoda statyczna.

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zobacz też

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)