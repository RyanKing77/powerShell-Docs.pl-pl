---
title: Filtr parametrów wejściowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067692"
---
# <a name="input-filter-parameters"></a>Parametry filtru danych wejściowych

Polecenia cmdlet można zdefiniować `Filter`, `Include`, i `Exclude` parametry, które filtrowania zestawu danych wejściowych obiektów, które ma wpływ na polecenia cmdlet.

Zazwyczaj, zestaw danych wejściowych obiektów jest określane przez `InputObject`, `Path`, lub `Name` parametru. Na przykład można mieć polecenia cmdlet `Path` parametr, który akceptuje wiele ścieżek przy użyciu symboli wieloznacznych i poszczególnych punktów ścieżki do obiektu wejściowego. Używane wspólnie, `Filter`, `Include`, i `Exclude` dalszej parametrów kwalifikowania ścieżki, polecenie cmdlet działa na każdym razem jest wywoływana.

## <a name="include-and-exclude-parameters"></a>Dołączanie i wykluczanie parametrów

`Include` i `Exclude` parametry zidentyfikować obiekty, które są dołączone lub wykluczone z zestawu danych wejściowych obiektów przekazywane do polecenia cmdlet. Użyj tych parametrów, gdy filtr może być wyrażona w języku standardowych symboli wieloznacznych. (Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [obsługi symboli wieloznacznych w parametrach polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` Parametr zawiera wszystkie obiekty, których nazwy są zgodne z filtrem dołączania. `Exclude` Parametru nie obejmuje wszystkie obiekty, których nazwy są zgodne z filtrem.

## <a name="filter-parameter"></a>Parametr filtru

`Filter` Parametr określa filtr, który nie jest wyrażona w języku standardowych symboli wieloznacznych. Na przykład interfejsy usługi Active Directory (ADSI) lub SQL filtry mogą być przekazywane do polecenia cmdlet, za pośrednictwem jego `Filter` parametru. W poleceniach cmdlet dostarczane przez środowisko Windows PowerShell te filtry są określane przez dostawców środowiska Windows PowerShell, których należy użyć polecenia cmdlet dostępu do magazynu danych. Każdy dostawca definiuje zazwyczaj ma własny filtr.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrowanie, jeśli nie ustawiono zestawu obiektów danych wejściowych

Jeśli nie ustawiono obiektów danych wejściowych jest określony, oznacza to, zwykle do filtrowania względem wszystkich obiektów. Aby uzyskać więcej informacji, zobacz[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)