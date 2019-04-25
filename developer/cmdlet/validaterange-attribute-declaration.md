---
title: Deklaracji atrybutu ValidateRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067114"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange, deklaracja atrybutu

Atrybut ValidateRange określa minimalne i maksymalne wartości (zakres) dla argumentu parametru polecenia cmdlet. Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.

## <a name="syntax"></a>Składnia

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametry

`MinRange` ([System.Object](/dotnet/api/system.object)) wymagane. Określa minimalna dozwolona wartość.

`MaxRange` ([System.Object](/dotnet/api/system.object)) wymagane. Określa maksymalną dozwoloną wartość.

## <a name="remarks"></a>Uwagi

- Środowisko wykonawcze programu Windows PowerShell zgłasza błąd budowy po wartości `MinRange` parametru jest większa niż wartość `MaxRange` parametru.

- Środowisko wykonawcze programu Windows PowerShell zgłasza błąd sprawdzania poprawności w następujących warunkach:

    - Gdy wartość argumentu jest mniejsza niż `MinRange` limit lub większa niż `MaxRange` limit.

    - Jeśli argument nie jest tego samego typu co `MinRange` i `MaxRange` parametrów.

- Atrybut ValidateRange jest definiowany przez [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
