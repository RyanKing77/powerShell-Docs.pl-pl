---
title: Deklaracji atrybutu ValidateSet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850456"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet, deklaracja atrybutu

Atrybut ValidateSetAttribute określa zestaw możliwych wartości dla parametru w argumencie polecenia cmdlet. Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.

Jeśli ten atrybut jest określony, środowisko uruchomieniowe programu Windows PowerShell Określa, czy podany argument parametru polecenia cmdlet pasuje do elementu w zestawie podany element. Polecenie cmdlet jest uruchamiane tylko wtedy, gdy argument parametru pasuje do elementu w zestawie. Jeśli nie zostanie znalezione dopasowanie, błąd jest zgłaszany przez środowisko uruchomieniowe programu Windows PowerShell.

## <a name="syntax"></a>Składnia

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametry

`ValidValues` ([System.String](/dotnet/api/System.String)) wymagane. Określa wartości elementu prawidłowego parametru. Poniższy przykład pokazuje sposób określania elementu jednego lub wielu elementów.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. Wartość domyślna `true` wskazuje, że wielkość liter jest ignorowana. Wartość `false` sprawia, że polecenia cmdlet jest rozróżniana wielkość liter.

## <a name="remarks"></a>Uwagi

- Ten atrybut może służyć tylko raz dla parametru.

- Jeśli wartość tego parametru jest tablicą, każdy element tablicy muszą być zgodne z elementu zestawu atrybutów.

- Atrybut ValidateSetAttribute jest definiowany przez [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
