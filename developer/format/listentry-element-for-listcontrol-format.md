---
title: Element ListEntry dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065227"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListEntry, element — ListControl (format)

Zawiera definicję widoku listy.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListEntry` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Definiuje obiekty .NET, korzystające z tej listy definicji widoku lub warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Element wymagany.<br /><br /> Definiuje właściwości i skrypty, których wartości są wyświetlane w widoku listy.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListEntries (Format)](./listentries-element-for-listcontrol-format.md)|Zawiera definicje w widoku listy.|

## <a name="remarks"></a>Uwagi

Widok listy jest format listy, która wyświetla wartości właściwości lub wartości skryptu dla każdego obiektu. Aby uzyskać więcej informacji na temat widoki list zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Elementy XML, które określają widok listy w tym przykładzie [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Element EntrySelectedBy ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Element ListEntries (Format)](./listentries-element-for-listcontrol-format.md)

[Element ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
