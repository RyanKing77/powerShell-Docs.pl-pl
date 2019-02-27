---
title: Formatowanie plików — omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851919"
---
# <a name="formatting-file-overview"></a>Omówienie plików formatujących

Format wyświetlania dla obiektów, które są zwracane przez polecenia (polecenia cmdlet, funkcji i skryptów) są definiowane za pomocą formatowania pliki (format.ps1xml). Niektóre z tych plików są dostarczane przez programu PowerShell, aby określić format wyświetlania tych obiektów zwróconych przez polecenia programu PowerShell — pod warunkiem, takich jak [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu zwróconego przez `Get-Process` polecenia cmdlet. Możesz również utworzyć własne niestandardowe pliki formatowania, aby zastąpić domyślny format wyświetlania lub, można napisać niestandardowy plik formatowania do określania sposobu wyświetlania obiektów zwróconych przez własne polecenia.

> [!IMPORTANT]
> Pliki formatowania nie może określić elementy obiektu, które są zwracane do potoku. Gdy obiekt jest zwracany do potoku, wszystkie elementy członkowskie tego obiektu są dostępne, nawet jeśli niektóre nie są wyświetlane.

Programu PowerShell używa danych w tych plikach formatowania, aby określić, co jest wyświetlane i sposobu formatowania wyświetlanych danych. Dane wyświetlane może zawierać właściwości obiektu lub wartość skryptu. Skrypty są używane, jeśli chcesz wyświetlić niektóre wartości, która nie jest dostępna bezpośrednio z właściwości obiektu, takie jak dodanie wartości dwie właściwości obiektu, a następnie wyświetlając Suma jako część danych. Formatowanie wyświetlanych danych odbywa się przez definiowanie widoków dla obiektów, które mają być wyświetlane. Można zdefiniować pojedynczy widok dla każdego obiektu, można zdefiniować pojedynczy widok dla wielu obiektów lub można zdefiniować wiele widoków dla tego samego obiektu. Nie ma żadnego limitu liczby wyświetleń, które można zdefiniować.

## <a name="common-features-of-formatting-files"></a>Często używane funkcje pliki formatowania

Każdy plik formatowania można zdefiniować następujące składniki, które mogą być współużytkowane przez wszystkie widoki zdefiniowane w pliku:

- Domyślne ustawienia konfiguracji, takich jak tego, czy dane wyświetlane w wierszach tabel będą wyświetlane w następnym wierszu, jeśli danych jest dłuższa niż szerokość kolumny. Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Definiowanie wspólne ustawienia konfiguracyjne](./defining-common-configuration-features.md).

- Ustawia obiekty, które mogą być wyświetlane przez jeden z widoków formatowania pliku. Aby uzyskać więcej informacji na temat tych zestawów (nazywane *zestawami zaznaczenia*), zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

- Wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku. Formanty zapewniają bardziej precyzyjną kontrolę na sposób wyświetlania danych. Aby uzyskać więcej informacji na temat formantów, zobacz [Definiowanie kontrolek niestandardowych](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formatowanie widoków

Widoki formatowania można wyświetlić obiekty w formacie tabeli, format listy, formacie szerokim i formatu niestandardowego. W większości przypadków każdego formatowania definicja jest określana przez zbiór znaczników XML, które opisują widoku. Każdy widok zawiera nazwę widoku, obiekty korzystające z tego widoku i elementy widoku, takie jak informacje wierszy i kolumn w widoku tabeli.

Tabela Wyświetl listę właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę. Każda kolumna reprezentuje pojedynczej właściwości obiektu lub wartość skryptu. Można zdefiniować wyświetlony widok tabeli wszystkich właściwości obiektu, podzbiór właściwości obiektu lub kombinacji właściwości i wartości skryptu. Każdy wiersz w tabeli reprezentuje zwrócony obiekt. Tworzenie widoku tabeli jest bardzo podobny do kiedy przekazać obiekt, do którego `Format-Table` polecenia cmdlet. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok tabeli](./creating-a-table-view.md).

Wyświetl listę widok zawiera listę właściwości obiektu lub wartość skryptu w jednej kolumnie. Każdy wiersz listy zawiera opcjonalną etykietę lub nazwę właściwości, a następnie według wartości właściwości lub skryptu. Tworzenie widoku listy jest bardzo podobny do przekazanie w potoku obiektu `Format-List` polecenia cmdlet. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok listy](./creating-a-list-view.md).

Szerokie wymieniono pojedynczej właściwości obiektu lub wartość skryptu w co najmniej jedną kolumnę. Nie ma etykiety lub nagłówek dla tego widoku. Tworzenie szerokiej widoku jest bardzo podobny do przekazanie w potoku obiektu `Format-Wide` polecenia cmdlet. Aby uzyskać więcej informacji na temat tego widoku, zobacz [szerokie](./creating-a-wide-view.md).

Widok niestandardowy przedstawia widok można dostosować właściwości obiektów lub wartości skryptu niezgodny sztywne struktury widoki tabel, widoków listy lub szerokie widoków. Można zdefiniować autonomiczny widok niestandardowy, lub można zdefiniować widoku niestandardowego, który jest używany przez inny widok, takiego jak widok tabeli lub widoku listy. Tworzenie widoku niestandardowego jest bardzo podobny do przekazanie w potoku obiektu `Format-Custom` polecenia cmdlet. Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok niestandardowy](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Składnikami widoku

Poniższe przykłady XML pokazują podstawowe składniki XML w widoku. Poszczególne elementy XML różnią się w zależności od tego, w którym widok ma zostać utworzona, ale podstawowe składniki widoków są takie same.

Na początek z każdego widoku ma `Name` element, który określa przyjazną dla użytkownika nazwę służący do odwoływać się do widoku. `ViewSelectedBy` element, który definiuje obiekty .NET, które są wyświetlane w widoku i *kontroli* element, który definiuje widoku.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

W elemencie kontrolki można zdefiniować co najmniej jeden *wpis* elementów. Jeśli używasz wielu definicjach, należy określić, które obiekty .NET Użyj Każda definicja. Tylko jeden wpis z tylko jedną definicję, jest potrzebna dla każdego formantu.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

W ramach każdego wpisu elementu widoku, należy określić *elementu* elementy, które definiują właściwości platformy .NET lub skrypty, które są wyświetlane w tym widoku.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Jak pokazano w poprzednich przykładach, formatowania plik może zawierać wiele widoków, widok może zawierać wiele definicji i każda definicja może zawierać wiele elementów.

## <a name="example-of-a-table-view"></a>Przykładowy widok tabeli

Poniższy przykład pokazuje tagów XML używanych do definiowania widoku tabeli, która zawiera dwie kolumny. [ViewDefinitions](./viewdefinitions-element-format.md) element jest elementem kontenera dla wszystkich widoków, które są zdefiniowane w pliku formatowania. [Widoku](./view-element-format.md) element definiuje określonej tabeli, lista, szeroki lub niestandardowy widok. W ramach każdej [widoku](./view-element-format.md) elementu [nazwa](./name-element-for-view-format.md) element Określa nazwę widoku, [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty korzystające z tego widoku i różnic kontroluje elementy (takie jak `TableControl` pokazano w poniższym przykładzie element) określ typ widoku.

```xml
<ViewDefinitions>
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

[Tworzenie widoku listy](./creating-a-list-view.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Tworzenie niestandardowych formantów](./creating-custom-controls.md)

[Pisanie programu PowerShell, formatowanie i typy plików](./writing-a-powershell-formatting-file.md)
