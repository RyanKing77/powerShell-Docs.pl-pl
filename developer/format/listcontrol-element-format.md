---
title: Element elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847831"
---
# <a name="listcontrol-element-format"></a>ListControl, element (format)

Definiuje format listy dla widoku.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListControl` elementu. Ten element musi zawierać tylko jeden typ elementów podrzędnych.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListEntries (Format)](./listentries-element-for-listcontrol-format.md)|Element wymagany.<br /><br /> Zawiera definicje w widoku listy.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania elementów członkowskich co najmniej jeden obiekt.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o tworzeniu widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono widok listy dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zobacz też

[Widok elementu (w formacie)](./view-element-format.md)

[Element ListEntries (Format)](./listentries-element-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
