---
title: Tworzenie szerokie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848559"
---
# <a name="creating-a-wide-view"></a>Tworzenie widoku szerokiego

Szerokie Wyświetla pojedynczą wartość dla każdego obiektu, który jest wyświetlany. Wartość właściwości obiektu platformy .NET lub wartość skryptu, może być wyświetlana wartość. Domyślnie istnieje etykiety lub nagłówek dla tego widoku.

## <a name="a-wide-view-display"></a>Wyświetlanie szerokie

W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu, który jest zwracany przez [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet, gdy jego dane wyjściowe w potoku do [ Format całej](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) polecenia cmdlet. (Domyślnie [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca widok tabeli.) W tym przykładzie dwie kolumny są używane do wyświetlania nazwę procesu dla każdego zwróconego obiektu. Nazwa właściwości obiektu nie jest wyświetlana, tylko wartości właściwości.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definiowanie szerokie

Następujący kody XML pokazuje schemat szerokie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Następujące elementy XML są używane do definiowania szerokie:

- [Widoku](./view-element-format.md) element jest elementem nadrzędnym szerokiego widoku. (Jest to ten sam element nadrzędny dla tabeli, listy i widoki kontrolki niestandardowej).

- [Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku. Ten element jest wymagany dla wszystkich widoków.

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku. Ten element jest wymagany.

- [GroupBy](./groupby-element-for-view-format.md) element definiuje, gdy zostanie wyświetlona nowa grupa obiektów. Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu. Ten element jest opcjonalne.

- [Formantów](./controls-element-for-view-format.md) elementy definiuje niestandardowe formanty, które są definiowane przez szerokie. Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych. Ten element jest opcjonalne. Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku. Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).

- [WideControl](./widecontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku. W powyższym przykładzie widok służy do wyświetlania [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) właściwości.

Na przykład kompletny plik formatowania, który definiuje prosty szerokie zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Zapewnianie definicje dla szerokiego widoku

Szerokie widoków może zapewnić co najmniej jedna definicja przy użyciu elementów podrzędnych [WideControl](./widecontrol-element-format.md) elementu. Zazwyczaj widok będzie mieć tylko jedną definicję. W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla wartość [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) właściwości. Wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), można wyświetlić szerokie.

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Następujące elementy XML może służyć do zapewnienia definicje szerokie:

- [WideControl](./widecontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku.

- [AutoSize](./autosize-element-for-widecontrol-format.md) element określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych. Ten element jest opcjonalne.

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element określa liczbę kolumn wyświetlanych w szerokim oknie. Ten element jest opcjonalne.

- [WideEntries](./wideentries-element-for-widecontrol-format.md) element udostępnia definicji widoku. W większości przypadków widok będzie mieć tylko jedną definicję. Ten element jest wymagany.

- [WideEntry](./wideentry-element-for-widecontrol-format.md) element zawiera definicję widoku. Co najmniej jeden [WideEntry](./wideentry-element-for-widecontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać. W większości przypadków widok będzie mieć tylko jedną definicję.

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych. Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [WideEntry](./wideentry-element-for-widecontrol-format.md) elementy wyświetlające różnych obiektów.

- [WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku. W przeciwieństwie do innych rodzajów widoków szerokości kontrolki można wyświetlić tylko jeden element.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w widoku. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element określa wzorzec, który służy do wyświetlania danych. Ten element jest opcjonalne.

Na przykład kompletny plik formatowania, który definiuje definicji szerokie zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definiowanie obiektów, które szerokie

Istnieją dwa sposoby, aby zdefiniować, które obiekty .NET przy użyciu szerokiej widoku. Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku. W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.

Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu szerokie [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów. Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez szerokie:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane przez szerokie.

- [TypeName](./typename-element-for-viewselectedby-format.md) element określa platformy .NET, który jest wyświetlany w widoku. W pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

Na przykład cały plik formatowania zobacz [szerokie (Basic)](./wide-view-basic.md).

W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów. Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania szerokie i widoku tabeli dla tych samych obiektów. Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez szerokie:

- [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane przez szerokie.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku. Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.

Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez definicję określonej za pomocą szerokie [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementu. Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji. Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji szerokie:

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element definiuje obiekty, które są wyświetlane przez definicję.

- [TypeName](./typename-element-for-viewselectedby-format.md) element określa platformy .NET, który jest wyświetlany przez definicję. Korzystając z tego elementu w pełni kwalifikowana nazwa typu .NET jest wymagana. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone. Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Wyświetlanie grup obiektów w szerokim oknie

Można oddzielić obiektów, które są wyświetlane przez szerokie w grupach. Nie oznacza to, że zdefiniowanie grupy, tylko program Windows PowerShell rozpoczyna nową grupę, w każdym przypadku, gdy zmieni się wartość określoną właściwość lub skryptu. W poniższym przykładzie tworzona nowa grupa zawsze wtedy, gdy wartość [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.

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

Na przykład kompletny plik formatowania, który definiuje grupy zobacz [szerokie (grupowania)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Za pomocą ciągów formatu

Ciągi formatowania można dodać do szerokie, aby lepiej zdefiniować sposób wyświetlania danych. Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Następujące elementy XML może służyć do określania wzorca format:

- [WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku. Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu. Skrypty można wywołać dowolnej metody obiektu. W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Następujący element XML może służyć do wywołania `ToString` metody:

- [WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku. Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Szerokie (Basic)](./wide-view-basic.md)

[Szerokie (grupowania)](./wide-view-groupby.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
