---
title: Wyświetlanie elementu (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846914"
---
# <a name="view-element-format"></a>View, element (format)

Określa widok, który zawiera jeden lub więcej obiektów platformy .NET. Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania.

Element widoku elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `View` elementu. Należy określić jeden i tylko jeden z elementów podrzędnych kontrolki, a następnie należy określić nazwę tego widoku i obiekty przez nie przy użyciu widoku. Definiowanie kontrolek niestandardowych, jak należy zgrupować obiekty i określanie, czy widok jest poza pasmem są opcjonalne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Kontrolki elementu widoku (Format)](./controls-element-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje zestaw elementów sterujących, które mogą być przywoływane przez ich nazwy z w widoku.|
|[Formant niestandardowy, Element (Format)](./customcontrol-element-for-groupby-format.md)|Element opcjonalny.<br /><br /> Definiuje format formantu niestandardowego dla widoku.|
|[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje sposób grupowania elementów członkowskich obiektów platformy .NET.|
|[Element elementu ListControl (Format)](./listcontrol-element-format.md)|Element opcjonalny.<br /><br /> Definiuje format listy dla widoku.|
|[Name — Element dla widoku (Format)](./name-element-for-view-format.md)|Element wymagany.<br /><br /> Określa nazwę używaną do odwoływać się do widoku.|
|[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)|Element opcjonalny.<br /><br /> Definiuje format tabeli, widoku.|
|[Element ViewSelectedBy widoku (Format)](./viewselectedby-element-format.md)|Element wymagany.<br /><br /> Definiuje obiekty .NET, które ten widok przedstawia.|
|[Element WideControl (Format)](./widecontrol-element-format.md)|Element opcjonalny.<br /><br /> Definiuje całej (pojedyncza wartość) format listy dla widoku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Zawiera definicje widoków, używany do wyświetlania obiektów.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach z różnych widoków i kontrolek niestandardowych zobacz następujące tematy:

- [Składniki widoków tabeli](./creating-a-table-view.md)

- [Składniki widoków list](./creating-a-list-view.md)

- [Szerokie składników](./creating-a-wide-view.md)

- [Formanty niestandardowe](./creating-custom-controls.md)

## <a name="example"></a>Przykład

W tym przykładzie `View` element, który definiuje widoku tabeli dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Zobacz też

[Element ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Name — Element dla widoku (Format)](./name-element-for-view-format.md)

[Element ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Kontrolki elementu widoku (Format)](./controls-element-for-view-format.md)

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)

[Element elementu ListControl (Format)](./listcontrol-element-format.md)

[Element WideControl (Format)](./widecontrol-element-format.md)

[Formant niestandardowy, Element (Format)](./customcontrol-element-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
