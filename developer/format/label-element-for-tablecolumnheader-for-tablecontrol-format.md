---
title: Etykieta elementu dla TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054513"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label, element — TableColumnHeader, TableControl (format)

Definiuje etykietę, która jest wyświetlana w górnej części kolumny. Ten element jest używany podczas definiowania widoku tabeli.

— Element (w formacie) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji tablecontrol — (w formacie) elementu TableColumnHeader TableHeaders tablecontrol — (w formacie) etykiety elementu TableColumnHeader dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Label` elementu. Tylko jedna etykieta jest dozwolony dla każdej kolumny.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnHeader TableHeaders dla tablecontrol — (w formacie)](./tablecolumnheader-element-format.md)|Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.|

## <a name="text-value"></a>Wartość tekstowa

Podaj tekst, który jest wyświetlany w górnej części kolumny tabeli. Nie istnieją żadne znaki w etykiecie kolumny.

## <a name="remarks"></a>Uwagi

Jeśli żadna etykieta nie zostanie określona, jest używana nazwa właściwości, którego wartość jest wyświetlana w wierszach.

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `TableColumnHeader` elementu, którego etykieta jest "Kolumna 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
