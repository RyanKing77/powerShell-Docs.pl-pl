---
title: GroupBy — Element dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849280"
---
# <a name="groupby-element-for-view-format"></a>GroupBy, element — View (format)

Definiuje sposób wyświetlania nowej grupy obiektów. Ten element jest używany podczas definiowania tabel, list, szeroki lub niestandardowe kontrolki widoku.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

Poniżej opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element formant niestandardowy do grupowania (w formacie)](./customcontrol-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Definiuje kontrolki niestandardowej, która wyświetlanie nowych grup.|
|[Element CustomControlName GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa nazwę formant, który służy do wyświetlania nowej grupy.|
|[Element LABEL dla grupowania (w formacie)](./label-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa etykietę, która jest wyświetlana, gdy zostanie osiągnięty nowej grupy.|
|[Element PropertyName GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET tak, rozpoczyna się nowa grupa zmianie wartości.|
|[Element ScriptBlock GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który uruchamia nową grupę, zmianie wartości.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który zawiera jeden lub więcej obiektów platformy .NET.|

## <a name="remarks"></a>Uwagi

Podczas definiowania sposobu wyświetlania nowej grupy obiektów, należy określić właściwość lub skryptu, który rozpocznie się do nowej grupy; jednak nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Element CustomControlName GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Element LABEL dla grupowania (w formacie)](./label-element-for-groupby-format.md)

[Element PropertyName GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[Element ScriptBlock GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
