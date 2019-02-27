---
title: Deklaracji atrybutu parametru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "56852143"
---
# <a name="parameter-attribute-declaration"></a>Parameter, deklaracja atrybutu

Atrybut parametru identyfikuje właściwość publiczna klasy polecenia cmdlet jako parametr polecenia cmdlet.

## <a name="syntax"></a>Składnia

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parametry

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` Wskazuje, że parametr polecenia cmdlet jest wymagany. Jeśli wymagany parametr nie zostanie podany, po wywołaniu polecenia cmdlet, programu Windows PowerShell monitu o wartości parametru. Wartość domyślna to `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) o nazwie parametr opcjonalny. Określa, że parametr wartość, należy dla tego parametru polecenia cmdlet. Jeśli nie ustawiono parametru jest określona, parametr należy do wszystkich zestawów parametrów.

`Position` ([System.Integer](/dotnet/api/System.Integer)) o nazwie parametr opcjonalny. Określa pozycję parametru w ramach polecenia programu Windows PowerShell.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` Wskazuje, że parametr polecenia cmdlet trwa jego wartość z obiektu procesu. Określ to słowo kluczowe, jeśli polecenie cmdlet uzyskuje dostęp do pełnego obiektu i nie tylko właściwości obiektu. Wartość domyślna to `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` Wskazuje, że parametr polecenia cmdlet trwa jego wartość z właściwości obiektu potoku, który ma taką samą nazwę lub tego samego aliasu jako parametr. Na przykład, jeśli polecenie cmdlet ma `Name` parametr oraz obiekt potoku ma również `Name` właściwości, wartość `Name` właściwość jest przypisany do `Name` parametru polecenia cmdlet. Wartość domyślna to `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny. `True` Wskazuje, że parametr polecenia cmdlet akceptuje wszystkie pozostałe argumenty, które są przekazywane do polecenia cmdlet. Wartość domyślna to `false`.

`HelpMessage` Opcjonalne, o nazwie parametru. Określa krótki opis parametru. Po uruchomieniu polecenia cmdlet i obowiązkowy parametr nie zostanie określony, program Windows PowerShell wyświetla ten komunikat.

`HelpMessageBaseName` Opcjonalne, o nazwie parametru. Określa lokalizację, w którym są przechowywane identyfikatory zasobów. Na przykład ten parametr można określić zestaw zasobów, który zawiera komunikaty Pomocy, które chcesz zlokalizować.

`HelpMessageResourceId` Opcjonalne, o nazwie parametru. Określa identyfikator zasobu komunikat pomocy.

## <a name="remarks"></a>Uwagi

- Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Polecenie cmdlet może mieć dowolną liczbę parametrów. Jednak dla wygody użytkowników, należy ograniczyć liczbę tych parametrów.

- Parametry musi być zadeklarowany w publicznych niestatycznego pola lub właściwości. Parametry powinny być zadeklarowane we właściwościach. Właściwość musi mieć metodę dostępu publicznego zestawu i, jeśli `ValueFromPipeline` lub `ValueFromPipelineByPropertyName` — słowo kluczowe jest określony, właściwość musi mieć metodę dostępu get publicznych.

- Po określeniu parametry pozycyjne, należy ograniczyć liczbę parametry pozycyjne w parametrze mniej niż pięć. I parametry pozycyjne nie muszą być ciągłe. Pozycje 5, 100 i 250 działać tak samo, jak pozycje 0, 1 i 2.

- Gdy `Position` — słowo kluczowe nie zostanie określona, parametr polecenia cmdlet muszą być przywoływane przez jego nazwę.

- Korzystając z zestawów parametrów, pamiętaj o następujących kwestiach:

    - Każdy zestaw parametrów musi mieć co najmniej jeden parametr unikatowy. Projekt dobre polecenia cmdlet oznacza, że ten unikatowy parametr należy również wymagane, jeśli jest to możliwe. Jeśli Twojego polecenia cmdlet jest przeznaczony do uruchamiania bez parametrów, unikatowy parametr nie może być wymagane.

    - Nie ustawiono parametru może zawierać więcej niż jeden parametr pozycyjne, z tym samym położeniu.

    - Tylko jeden parametr w zestawie parametrów powinny deklarować `ValueFromPipeline = true`. Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName = true`.

    - Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName = true`.

- Aby uzyskać więcej informacji na temat wytycznych dotyczących nazwy parametrów, zobacz [nazwy parametrów polecenia Cmdlet](standard-cmdlet-parameter-names-and-types.md).

- Atrybut parametru jest definiowany przez [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klasy.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nazwy parametrów polecenia cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
