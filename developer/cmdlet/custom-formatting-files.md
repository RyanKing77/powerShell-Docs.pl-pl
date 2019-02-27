---
title: Niestandardowe formatowanie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850036"
---
# <a name="custom-formatting-files"></a>Niestandardowe pliki formatujące

Format wyświetlania dla obiektów zwróconych przez polecenia cmdlet, funkcji i skryptów są definiowane za pomocą formatowania pliki (format.ps1xml). Niektóre z tych plików są dostarczane przez programu Windows PowerShell, aby zdefiniować domyślny format wyświetlania tych obiektów zwróconych przez polecenia cmdlet programu Windows PowerShell. Jednak można również utworzyć własne niestandardowe pliki formatowania, aby zastąpić domyślny format wyświetlania lub do określania sposobu wyświetlania obiektów zwróconych przez własne polecenia.

Programu Windows PowerShell wykorzystuje dane w tych plikach formatowania, aby określić, co jest wyświetlane, i jak dane są sformatowane. Dane wyświetlane może zawierać właściwości obiektu lub wartość blok skryptu.  Bloki skryptu są używane, jeśli chcesz wyświetlić niektóre wartości, która nie jest dostępna bezpośrednio z właściwości obiektu. Na przykład można ulepszyć dwie właściwości obiektu i sumy są wyświetlane jako osobne elementu danych. Podczas pisania własnego formatowania pliku, należy zdefiniować *widoków* obiektów, które mają być wyświetlane. Można zdefiniować pojedynczy widok dla każdego obiektu, można zdefiniować pojedynczy widok dla wielu obiektów lub można zdefiniować wiele widoków dla tego samego obiektu. Nie ma żadnego limitu liczby wyświetleń, które można zdefiniować.

> [!IMPORTANT]
> Pliki formatowania nie może określić elementy obiektu, które są zwracane do potoku. Gdy obiekt jest zwracany do potoku, wszystkie elementy członkowskie tego obiektu są dostępne.

## <a name="format-views"></a>Format widoków

Widoki formatowania można wyświetlić obiekty w postaci tabeli, format listy, formacie szerokim i formatu niestandardowego. W większości przypadków każdego formatowania definicja jest określana przez zbiór znaczników XML, zawierających opis widoku. Każdy widok zawiera nazwę widoku, obiekty korzystające z tego widoku i elementy widoku, takie jak informacje wierszy i kolumn w widoku tabeli.

Dostępne są następujące widoki.

Widok tabeli przedstawiono listę właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę. Każda kolumna reprezentuje właściwość obiektu lub wartość bloku skryptu. Można zdefiniować wyświetlony widok tabeli wszystkich właściwości obiektu, podzbiór właściwości obiektu lub kombinacji właściwości i wartości bloku skryptu. Każdy wiersz w tabeli reprezentuje zwrócony obiekt. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok tabeli](../format/creating-a-table-view.md).

Widok listy zawiera listę właściwości obiektu lub wartość bloku skryptu w jednej kolumnie. Każdy wiersz listy zawiera opcjonalną etykietę lub nazwę właściwości, a następnie wartość właściwości lub skrypt bloku. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok listy](../format/creating-a-list-view.md).

Szerokie wymieniono pojedynczej właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę. Nie ma etykiety lub nagłówek dla tego widoku. Aby uzyskać więcej informacji na temat tego widoku, zobacz [szerokie](../format/creating-a-wide-view.md).

Widok niestandardowy przedstawia widok można dostosować właściwości obiektów lub wartości bloku skryptu niezgodny sztywne struktury widoki tabel, widoków listy lub szerokie widoków. Można zdefiniować niestandardowy widok autonomiczny lub można zdefiniować widoku niestandardowego, który jest używany przez inny widok, takiego jak widok tabeli lub widoku listy. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok niestandardowy](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Wyświetl elementy XML

Poniższy przykład pokazuje tagów XML używanych do definiowania widoku tabeli, która zawiera dwie kolumny. [ViewDefinitions](../format/viewdefinitions-element-format.md) element jest elementem kontenera dla wszystkich widoków, które są zdefiniowane w pliku formatowania. [Widoku](../format/view-element-format.md) element definiuje określonej tabeli, lista, szeroki lub niestandardowy widok. W ramach każdego widoku [nazwa](../format/name-element-for-view-format.md) element Określa nazwę widoku, [ViewSelectedBy](../format/viewselectedby-element-format.md) element definiuje obiekty korzystające z tego widoku i elementy innej kontrolki (takie jak `TableControl` element) definiują format widoku.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Zobacz też

[Widok tabeli](../format/creating-a-table-view.md)

[Widok listy](../format/creating-a-list-view.md)

[Szerokie](../format/creating-a-wide-view.md)

[Widok niestandardowy](../format/creating-custom-controls.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
