---
title: Tworzenie widoku listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066859"
---
# <a name="creating-a-list-view"></a>Tworzenie widoku listy

Widok listy wyświetla dane w jednej kolumnie (w kolejności sekwencyjnej). Dane wyświetlane na liście można wartość właściwości platformy .NET lub wartość skryptu.

## <a name="a-list-view-display"></a>Wyświetlanie widoku listy

Następujące dane wyjściowe pokazują, jak środowiska Windows PowerShell Wyświetla właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiekty, które są zwracane przez [Get-Service](/powershell/module/microsoft.powershell.management/get-service) polecenia cmdlet. W tym przykładzie trzy obiekty zostały zwrócone z każdym obiektem oddzielone z poprzednim obiektu pusty wiersz.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Definiowanie widoku listy

Następujący kody XML pokazuje schematu widok listy do wyświetlania kilka właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu. Należy określić każdej właściwości, które mają być wyświetlane w widoku listy.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Następujące elementy XML są używane do definiowania widoku listy:

- [Widoku](./view-element-format.md) element jest elementem nadrzędnym elementu widoku listy. (Jest to tego samego elementu nadrzędnego dla tabeli, widoki kontrolne szerokiej i niestandardowych).

- [Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku. Ten element jest wymagany dla wszystkich widoków.

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku. Ten element jest wymagany.

- [GroupBy](./groupby-element-for-view-format.md) element definiuje, gdy zostanie wyświetlona nowa grupa obiektów. Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu. Ten element jest opcjonalne.

- [Formantów](./controls-element-for-view-format.md) element definiuje niestandardowe formanty, które są zdefiniowane w widoku listy. Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych. Ten element jest opcjonalne. Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku. Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).

- [Elementu ListControl](./listcontrol-element-format.md) element definiuje, co jest wyświetlane w widoku oraz sposób jego sformatowania. Podobnie jak w innych widoków, widok listy lub można wyświetlić wartości właściwości obiektu wartości generowane przez skrypt.

Na przykład kompletny plik formatowania, który definiuje widoku prostej listy zobacz [widok listy (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Podając w definicji widoku listy

Widoki list można podać jeden lub więcej definicji przy użyciu elementów podrzędnych [elementu ListControl](./listcontrol-element-format.md) elementu. Zazwyczaj widok będzie mieć tylko jedną definicję. W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla kilka właściwości [System.Diagnostics.Process? Displayproperty = imię i nazwisko](/dotnet/api/System.Diagnostics.Process) obiektu. Wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), można wyświetlić widoku listy.

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Następujące elementy XML może służyć do zapewnienia definicji widoku listy:

- [Elementu ListControl](./listcontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku.

- [ListEntries](./listentries-element-for-listcontrol-format.md) element udostępnia definicji widoku. W większości przypadków widok będzie mieć tylko jedną definicję. Ten element jest wymagany.

- [ListEntry](./listentry-element-for-listcontrol-format.md) element zawiera definicję widoku. Co najmniej jeden [ListEntry](./listentry-element-for-listcontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać. W większości przypadków widok będzie mieć tylko jedną definicję.

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych. Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [ListEntry](./listentry-element-for-listcontrol-format.md) elementy wyświetlające różnych obiektów.

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element określa właściwości i skrypty, których wartości są wyświetlane w wierszach widoku listy.

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element Określa właściwość lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy. Widok listy, należy określić co najmniej jedną właściwość lub skryptu. Nie ma żadnego limitu maksymalną liczbę wierszy, które można określić.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

- [Etykiety](./label-element-for-listitem-for-listcontrol-format.md) element Określa etykietę, która jest wyświetlana po lewej stronie wartości właściwości lub skryptu w wierszu. Ten element jest opcjonalne. Jeśli etykieta nie zostanie określony, jest wyświetlana nazwa właściwości lub skryptu. Aby uzyskać kompletny przykład, zobacz [widok listy (etykiety)](./list-view-labels.md).

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element określa warunek, który musi istnieć dla wiersza, które mają być wyświetlane. Aby uzyskać więcej informacji o dodawaniu warunków do widoku listy, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md). Ten element jest opcjonalne.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element określa wzorzec, który służy do wyświetlania wartości właściwości lub skryptu. Ten element jest opcjonalne.

Na przykład kompletny plik formatowania, który definiuje widoku prostej listy zobacz [widok listy (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definiowanie obiektów, które w widoku listy

Istnieją dwa sposoby, aby zdefiniować, które obiekty platformy .NET przy użyciu widoku listy. Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku. W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.

Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu widoku listy [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów. Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.

- [TypeName](./typename-element-for-viewselectedby-format.md) element określa obiekt .NET, który jest wyświetlany w widoku. W pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

Na przykład cały plik formatowania zobacz [widok listy (Basic)](./list-view-basic.md).

W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów. Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania widoku listy i widok tabeli dla tych samych obiektów. Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku. Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez określonej definicji widoku listy przy użyciu [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu. Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji. Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji widoku listy:

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element definiuje obiekty, które są wyświetlane przez definicję.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element określa obiekt .NET, który jest wyświetlany przez definicję. Korzystając z tego elementu, w pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone. Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Wyświetlanie grup obiektów w widoku listy

Można oddzielić obiektów, które są wyświetlane w widoku listy do grup. Nie oznacza to, że zdefiniowanie grupy, tylko program Windows PowerShell rozpoczyna nową grupę, w każdym przypadku, gdy zmieni się wartość określoną właściwość lub skryptu. W poniższym przykładzie tworzona nowa grupa zawsze wtedy, gdy wartość [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Następujące elementy XML są używane do definiowania, gdy tworzona jest grupa:

- [GroupBy](./groupby-element-for-view-format.md) element definiuje właściwość lub skrypt, który uruchamia nową grupę i definiuje sposób wyświetlania grupy.

- [PropertyName](./propertyname-element-for-groupby-format.md) element Określa właściwość, która uruchamia nową grupę, zmianie wartości. Należy określić właściwość lub skrypt, aby rozpocząć grupy, ale nie możesz określić jednocześnie.

- [ScriptBlock](./scriptblock-element-for-groupby-format.md) element określa skrypt, który uruchamia nową grupę, zmianie wartości. Należy określić skrypt lub właściwości, które można uruchomić grupy, ale nie możesz określić jednocześnie.

- [Etykiety](./label-element-for-groupby-format.md) element definiuje etykietę, która jest wyświetlana na początku każdej grupy. Oprócz tekstu określonego przez ten element programu Windows PowerShell Wyświetla wartość, która wyzwolone nową grupę, a następnie dodaje pusty wiersz, przed i po etykiecie. Ten element jest opcjonalne.

- [Formant niestandardowy](./customcontrol-element-for-groupby-format.md) element definiuje formant, który służy do wyświetlania danych. Ten element jest opcjonalne.

- [CustomControlName](./customcontrolname-element-for-groupby-format.md) element określa wspólny lub wyświetlić formant, który służy do wyświetlania danych. Ten element jest opcjonalne.

Na przykład kompletny plik formatowania, który definiuje grupy zobacz [widok listy (grupowania)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Za pomocą ciągów formatu

Ciągi formatowania można dodać do widoku, aby lepiej zdefiniować sposób wyświetlania danych. Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Następujące elementy XML może służyć do określania wzorca format:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element określa dane, które jest wyświetlane w widoku.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu. Skrypty można wywołać dowolnej metody obiektu. W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Następujący element XML może służyć do wywołania `ToString` metody:

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element określa dane, które jest wyświetlane w widoku.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
