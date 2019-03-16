---
title: Polecenia cmdlet atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055176"
---
# <a name="cmdlet-attributes"></a>Atrybuty poleceń cmdlet

Program Windows PowerShell definiuje kilka atrybutów, których można użyć, aby dodać funkcje wspólne do poleceń cmdlet bez stosowania tej funkcji w obrębie własnego kodu. Obejmuje to atrybut polecenia Cmdlet, który identyfikuje klasę program Microsoft .NET Framework jako klasa polecenia cmdlet, atrybut OutputType, który określa typów programu .NET Framework, zwracany przez polecenie cmdlet atrybut Parameter, który określa właściwości publiczne jako polecenia cmdlet Parametry i więcej.

## <a name="in-this-section"></a>W tej sekcji

[Atrybuty w kodzie polecenia Cmdlet](./attributes-in-cmdlet-code.md) opisuje korzyści z używania atrybutów w kodzie polecenia cmdlet.

[Typy atrybutów](./attribute-types.md) opisano różne atrybuty, które można dekoracji klasy polecenia cmdlet.

[Deklaracji atrybutu alias](./alias-attribute-declaration.md) w tym artykule opisano sposób definiowania aliasów dla nazwy parametru polecenia cmdlet.

[Polecenia cmdlet deklaracji atrybutu](./cmdlet-attribute-declaration.md) opisuje jak definiować klasy .NET Framework jako polecenia cmdlet.

[Poświadczenie deklaracji atrybutu](./credential-attribute-declaration.md) zawiera opis sposobu dodawania obsługa dla konwertowania ciąg wejściowy w [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu.

[Atrybutu OutputType deklaracji](./outputtype-attribute-declaration.md) opisuje sposób określania typów programu .NET Framework, zwracany przez polecenie cmdlet.

[Deklaracji atrybutu parametru](./parameter-attribute-declaration.md) opisuje jak definiować parametry polecenia cmdlet.

[Deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md) w tym artykule opisano sposób definiowania, ile argumentów są dozwolone dla parametru.

[Deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md) w tym artykule opisano sposób definiowania długość (w znakach) argument parametru.

[Deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md) opisuje jak definiować prawidłowe wzorce dla argumentu parametru.

[Deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md) w tym artykule opisano sposób definiowania prawidłowy zakres dla argumentu parametru.

[Deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md) w tym artykule opisano sposób definiowania możliwe wartości dla argumentu parametru.

## <a name="reference"></a>Dokumentacja

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
