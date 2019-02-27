---
title: Element WideEntries WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844905"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries, element — WideControl (format)

Zawiera definicje szerokie. Szerokie, należy określić co najmniej jedną definicję.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu WideControl (Format) WideEntries elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideEntries` elementu. Należy określić co najmniej jeden element podrzędny elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Zawiera definicję szerokie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideControl (Format)](./widecontrol-element-format.md)|Definiuje całej (pojedyncza wartość) format listy dla widoku.|

## <a name="remarks"></a>Uwagi

Szerokie jest format listy, który wyświetla wartość właściwości jednego lub wartość skryptu dla każdego obiektu. Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szeroki składniki widoków](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `WideEntries` element, który definiuje pojedynczy `WideEntry` elementu. `WideEntry` Element zawiera pojedynczy `WideItem` element, który definiuje, jakie wartości właściwości lub skryptu jest wyświetlany w widoku.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Element WideControl (Format)](./widecontrol-element-format.md)

[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
