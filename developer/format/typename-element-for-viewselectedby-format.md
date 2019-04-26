---
title: Element TypeName dla ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083760"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName, element — ViewSelectedBy (format)

Określa obiekt .NET, który jest wyświetlany w widoku.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) ViewSelectedBy — Element (Format) TypeName Element konfiguracji dla ViewSelectedBy (Format)

## <a name="syntax"></a>Składnia

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `TypeName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Definiuje obiekty .NET, które są wyświetlane w widoku.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w różnych widokach, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md), [tworzenia widoku listy](./creating-a-list-view.md), [tworzenia szerokiej widoku](./creating-a-wide-view.md), i [ Składniki widoków niestandardowych](./creating-custom-controls.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiekt widoku listy. Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Tworzenie niestandardowych formantów](./creating-custom-controls.md)

[Element ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
