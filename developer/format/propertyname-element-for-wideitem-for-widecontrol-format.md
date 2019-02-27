---
title: Element PropertyName WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850281"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName, element — WideItem, WideControl (format)

Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) WideItem — Element (Format) PropertyName Element konfiguracji dla WideItem (Format)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w szerokim oknie.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości, którego wartość jest wyświetlana.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

Ten przykład przedstawia szerokie, który wyświetla wartość właściwości ProcessName [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Zobacz też

[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
