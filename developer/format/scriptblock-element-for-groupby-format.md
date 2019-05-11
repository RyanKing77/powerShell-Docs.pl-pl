---
title: Element ScriptBlock GroupBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229313"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock, element — GroupBy (format)

Określa skrypt, który uruchamia nową grupę, zmianie wartości.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu ScriptBlock widoku (w formacie) dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)|Definiuje sposób wyświetlania grupy obiektów platformy .NET.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, który jest oceniany.

## <a name="remarks"></a>Uwagi

Zawsze wtedy, gdy zmieni się wartość ten skrypt programu PowerShell rozpoczyna się nowej grupy.

Gdy ten element jest określony, nie można określić [PropertyName](propertyname-element-for-groupby-format.md) element, aby rozpocząć nową grupę.

## <a name="see-also"></a>Zobacz też

[Element PropertyName GroupBy (Format)](propertyname-element-for-groupby-format.md)

[GroupBy — Element dla widoku (Format)](groupby-element-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](writing-a-powershell-formatting-file.md)
