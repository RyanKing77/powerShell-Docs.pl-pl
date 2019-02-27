---
title: Typy atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852276"
---
# <a name="attribute-types"></a>Typy atrybutów

Polecenia cmdlet atrybuty mogą być grupowane według funkcji.
W poniższych sekcjach opisano dostępne atrybuty i opisują, jakie środowisko uruchomieniowe wykonuje, gdy ten atrybut jest wywoływana.

## <a name="cmdlet-attributes"></a>Atrybuty poleceń cmdlet

### <a name="cmdlet"></a>Polecenie cmdlet

Określa klasę .NET Framework jako polecenia cmdlet.
Jest to wymaganego atrybutu podstawowego.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Atrybuty parametru

### <a name="parameter"></a>Parametr

Identyfikuje właściwość publiczna w klasie polecenia cmdlet jako parametr polecenia cmdlet.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Określa jeden lub więcej aliasów dla parametru.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu Alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Argument atrybutów sprawdzania poprawności

### <a name="validatecount"></a>ValidateCount

Określa minimalną i maksymalną liczbę argumentów, które są dozwolone dla parametru polecenia cmdlet.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Określa minimalną i maksymalną liczbę znaków dla parametru w argumencie polecenia cmdlet.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Określa wzorzec wyrażenia regularnego, który argument parametru polecenia cmdlet muszą być zgodne.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Określa minimalne i maksymalne wartości dla argumentu parametru polecenia cmdlet.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Określa zestaw prawidłowych wartości dla argumentu parametru polecenia cmdlet.
Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
