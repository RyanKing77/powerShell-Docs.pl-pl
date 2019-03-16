---
title: Tablecontrol — Element (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054581"
---
# <a name="tablecontrol-element-format"></a>TableControl, element (format)

Definiuje format tabeli w celu wyświetlenia.

Element ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format)

## <a name="syntax"></a>Składnia

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableControl` elementu. Należy określić wiersze z tabeli. Wszystkie inne elementy podrzędne są opcjonalne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element AutoSize tablecontrol — (w formacie)](./autosize-element-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych.|
|[Element HideTableHeaders tablecontrol — (w formacie)](./hidetableheaders-element-format.md)|Element opcjonalny.<br /><br /> Wskazuje, czy nagłówek tabeli nie jest wyświetlana.|
|[Element TableHeaders tablecontrol — (w formacie)](./tableheaders-element-format.md)|Element wymagany.<br /><br /> Definiuje etykiety, szerokości i wyrównania danych dla kolumn w widoku tabeli.|
|[Element TableRowEntries tablecontrol — (w formacie)](./tablerowentries-element-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Zawiera definicje widoku tabeli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania elementów członkowskich co najmniej jeden obiekt.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `TableControl` element, który służy do wyświetlania właściwości [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Element AutoSize tablecontrol — (w formacie)](./autosize-element-for-tablecontrol-format.md)

[Element HideTableHeaders (Format)](./hidetableheaders-element-format.md)

[Element TableHeaders (Format)](./tableheaders-element-format.md)

[Element TableRowEntries (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
