---
title: Element TypeName dla EntrySelectedBy dla WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083930"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName, element — EntrySelectedBy, WideEntry (format)

Określa typ architektury .NET w definicji. Definicja jest używana zawsze, gdy zostanie wyświetlony ten obiekt.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (w formacie) EntrySelectedBy Element konfiguracji elementu TypeName WideEntry (Format) WideEntry ( Format)

## <a name="syntax"></a>Składnia

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Uwagi

Każdy wpis szeroki należy określić co najmniej jednego typu .NET, zestaw zaznaczenia lub warunek wyboru, który musi istnieć dla definicji, który ma być używany.

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
