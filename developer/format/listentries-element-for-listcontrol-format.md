---
title: Element ListEntries dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847362"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries, element — ListControl (format)

Zawiera definicje w widoku listy. Widok listy, należy określić co najmniej jedną definicję.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (w formacie) ListEntries elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListEntries` elementu. Należy określić co najmniej jeden element podrzędny elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListEntry (Format)](./listentry-element-for-listcontrol-format.md)|Zawiera definicję widoku listy.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element elementu ListControl (Format)](./listcontrol-element-format.md)|Definiuje format listy dla widoku.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat widoki list zobacz [widok listy](./creating-a-list-view.md).

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

[Element elementu ListControl (Format)](./listcontrol-element-format.md)

[Element ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Widok listy](./creating-a-list-view.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
