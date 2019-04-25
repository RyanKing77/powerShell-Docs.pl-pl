---
title: Tworzenie widoku tabeli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066842"
---
# <a name="creating-a-table-view"></a>Tworzenie widoku tabeli

Widok tabeli wyświetla dane w co najmniej jedną kolumnę. Każdy wiersz w tabeli reprezentuje obiekt .NET, a każda kolumna w tabeli reprezentuje właściwość obiektu lub wartość skryptu. Można zdefiniować widoku tabeli, powoduje wyświetlenie wszystkich właściwości obiektu lub podzbiór właściwości obiektu.

## <a name="a-table-view-display"></a>Wyświetlanie widoku tabeli

W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu, który jest zwracany przez [Get-Service](/powershell/module/microsoft.powershell.management/get-service) polecenia cmdlet. Dla tego obiektu, programu Windows PowerShell został zdefiniowany widok tabeli, która wyświetla `Status` właściwości `Name` właściwości (Ta właściwość jest właściwością aliasu dla `ServiceName` właściwości), a `DisplayName` właściwości. Każdy wiersz w tabeli reprezentuje obiekt zwracany przez polecenie cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definiowanie widoku tabeli

Następujący kody XML pokazuje schemat tabeli widok do wyświetlania [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu. Należy określić każdej właściwości, które mają być wyświetlane w widoku tabeli.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Następujące elementy XML są używane do definiowania widoku listy:

- [Widoku](./view-element-format.md) element jest elementem nadrzędnym w widoku tabeli. (Jest to tego samego elementu nadrzędnego dla listy, widoki kontrolne szerokiej i niestandardowych).

- [Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku. Ten element jest wymagany dla wszystkich widoków.

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku. Ten element jest wymagany.

- [GroupBy](./groupby-element-for-view-format.md) definiuje element (nie pokazane w tym przykładzie), gdy zostanie wyświetlona nowa grupa obiektów. Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu. Ten element jest opcjonalne.

- [Formantów](./controls-element-for-view-format.md) — element (nie pokazane w tym przykładzie) definiuje niestandardowe formanty, które są zdefiniowane w widoku tabeli. Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych. Ten element jest opcjonalne. Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku. Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).

- [HideTableHeaders](./hidetableheaders-element-format.md) — element (nie show w tym przykładzie) Określa tabelę nie będą widoczne dla wszystkich etykiet w górnej części tabeli. Ten element jest opcjonalne.

- [Tablecontrol —](./tablecontrol-element-format.md) element, który definiuje informacje o nagłówku i wierszu tabeli. Podobnie jak w innych widoków, widok tabeli wyświetlić wartości właściwości obiektu lub wartości generowanych przez skrypty.

## <a name="defining-column-headers"></a>Definiowanie nagłówków kolumn

1. [TableHeaders](./tableheaders-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w górnej części tabeli.

2. [TableColumnHeader](./tablecolumnheader-element-format.md) element definiuje, co jest wyświetlane w górnej części kolumny tabeli. Należy określić te elementy w kolejności, nagłówki wyświetlane.

   Nie ma żadnego limitu liczba tych elementu, którego można używać, ale liczba [TableColumnHeader](./tablecolumnheader-element-format.md) elementy w widoku tabeli musi być równa liczbie [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementów, których używasz.

3. [Etykiety](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element Określa tekst, który jest wyświetlany. Ten element jest opcjonalne.

4. [Szerokość](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element Określa szerokość (w znakach) kolumny. Ten element jest opcjonalne.

5. [Wyrównanie](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element określa sposób wyświetlania etykiety. Etykiety można wyrównane do lewej, z prawej strony lub wyśrodkowany. Ten element jest opcjonalne.

## <a name="defining-the-table-rows"></a>Definiowanie wiersze tabeli

Widoki tabel może zapewnić co najmniej jedną definicję, które określają, jakie dane są wyświetlane w wierszach tabeli przy użyciu elementów podrzędnych [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementu. Należy zauważyć, że można określić wiele definicji dla wierszy w tabeli, ale nagłówki wierszy pozostają takie same, niezależnie od tego, jakie definicji wiersza jest używany. Zazwyczaj tabela będzie mieć tylko jedną definicję.

W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla wartości kilka właściwości [System.Diagnostics.Process? Displayproperty = imię i nazwisko](/dotnet/api/System.Diagnostics.Process) obiektu. Widok tabeli można wyświetlić wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), w jej wiersze.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Następujące elementy XML może służyć do zapewnienia definicje dla wiersza:

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w wierszach tabeli.

- [TableRowEntry](./listentry-element-for-listcontrol-format.md) element zawiera definicję wiersza. Co najmniej jeden [TableRowEntry](./listentry-element-for-listcontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać. W większości przypadków widok będzie mieć tylko jedną definicję.

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych. Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementy wyświetlające różnych obiektów.

- [Opakować](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element określa, że tekst przekraczający szerokość kolumny są wyświetlane w następnym wierszu. Domyślnie tekst przekraczający szerokość kolumny zostały obcięte.

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza. Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu. Ten element jest opcjonalne.

- [Wyrównanie](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa sposób wyświetlania wartości właściwości lub skryptu. Wartość można wyrównane do lewej, z prawej strony lub wyśrodkowany. Ten element jest opcjonalne.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definiowanie obiektów, które widok tabeli

Istnieją dwa sposoby, aby zdefiniować, które obiekty platformy .NET przy użyciu widoku tabeli. Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku. W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.

Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu widoku tabeli [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów. Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok tabeli:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.

- [TypeName](./typename-element-for-viewselectedby-format.md) element określa obiekt .NET, który jest wyświetlany w widoku. W pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów. Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania widoku listy i widok tabeli dla tych samych obiektów. Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku. Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez określonej definicji widoku tabeli za pomocą [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementu. Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji. Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Podczas tworzenia wiele definicji widoku tabeli nie można określić innej kolumny nagłówków. Można określić, co wyświetlane w wierszach tabeli, na przykład które obiekty są wyświetlane.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji widoku listy:

- [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element definiuje obiekty, które są wyświetlane przez definicję.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element określa obiekt .NET, który jest wyświetlany przez definicję. Korzystając z tego elementu, w pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone. Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Za pomocą ciągów formatu

Ciągi formatowania można dodać do widoku, aby lepiej zdefiniować sposób wyświetlania danych. Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Następujące elementy XML może służyć do określania wzorca format:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza. Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.

W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu. Skrypty można wywołać dowolnej metody obiektu. W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Następujący element XML może służyć do wywołania `ToString` metody:

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza. Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
