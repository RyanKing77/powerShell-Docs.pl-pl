---
title: Element TableColumnItem TableColumnItems dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851303"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem, element — TableColumnItems, TableControl (format)

Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie) Element TableColumnItems TableControlEntry tablecontrol — (w formacie) elementu TableColumnItem TableColumnItems dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnItem` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Definiuje sposób wyświetlania danych w kolumnie wiersza.|
|[Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Określa wzorzec formatu, który jest używany do formatowania danych w kolumnie wiersza.|
|[Element PropertyName TableColumnItem dla tablecontrol — (w formacie)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa nazwę właściwości, którego wartość jest wyświetlana.|
|[Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlana w kolumnie wiersz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnItems TableControlEntry dla tablecontrol — (w formacie)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.|

## <a name="remarks"></a>Uwagi

Można określić właściwości obiektu lub skryptu w każdej kolumnie wiersza. Jeśli nie określono żadnych elementów podrzędnych, element jest symbolem zastępczym, a nie zostaną wyświetlone dane.

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `TableColumnItem` element, który wyświetla wartość `Status` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Element TableColumnItems (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Element PropertyName TableColumnItem dla tablecontrol — (w formacie)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
