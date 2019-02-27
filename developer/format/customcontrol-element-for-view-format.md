---
title: Formant niestandardowy Element widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850491"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl, element — View (format)

Definiuje format formantu niestandardowego dla widoku.

Konfiguracji elementu (w formacie) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) formant niestandardowy Element (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControl` elementu. Należy określić jeden element podrzędny.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntries formant niestandardowy dla widoku (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Element wymagany.<br /><br /> Zawiera definicje widoku formantu niestandardowego.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.|

## <a name="remarks"></a>Uwagi

W większości przypadków tylko jedną definicję, jest wymagana dla każdego widoku kontroli, ale istnieje możliwość określenia wiele definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku. W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Element CustomEntries formant niestandardowy dla widoku (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
