---
title: Wyrównanie elementu TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845241"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment, element — TableColumnHeader, TableControl (format)

Definiuje sposób wyświetlania danych w nagłówkach kolumn.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders — Element (Format) TableColumnHeader — Element (Format) wyrównanie Element konfiguracji dla TableColumnHeader (Format)

## <a name="syntax"></a>Składnia

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Alignment` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.|

## <a name="text-value"></a>Wartość tekstowa

Określ jedną z następujących wartości. Te wartości nie jest rozróżniana wielkość liter.

Lewy Wyrównuje dane wyświetlane w kolumnie po lewej stronie jest to wartość domyślna, jeśli nie określono tego elementu.

Prawy Wyrównuje dane wyświetlane w kolumnie po prawej stronie.

Centra centrum danych wyświetlanych w kolumnie.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `TableColumnHeader` elementu, którego dane są wyrównane po lewej stronie.

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
