---
title: Deklaracji atrybutu alias | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846144"
---
# <a name="alias-attribute-declaration"></a>Alias, deklaracja atrybutu

Atrybut Alias umożliwia użytkownikowi określenie różnych nazw parametrów polecenia cmdlet. Aliasy może służyć do zapewnienia skróty dla nazwy parametru lub zapewniają różne nazwy, które są odpowiednie dla różnych scenariuszy.

## <a name="syntax"></a>Składnia

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametry

`aliasName` (Ciąg[]) Wymagane. Określa zestaw nazw rozdzielonych przecinkami aliasu dla parametru polecenia cmdlet.

## <a name="remarks"></a>Uwagi

- Atrybut Alias jest używany z atrybutem parametru, w przypadku określenia parametru polecenia cmdlet. Aby uzyskać więcej informacji o tym, jak zadeklarować tych atrybutów, zobacz [jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Każda nazwa aliasu musi być unikatowa w obrębie polecenia cmdlet. Nie sprawdza programu Windows PowerShell dla nazw duplikacji aliasu.

- Atrybut Alias jest używany jeden raz dla każdego z parametrów polecenia cmdlet.

- Ten atrybut aliasu jest definiowany przez [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[Parametr aliasów](./parameter-aliases.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
