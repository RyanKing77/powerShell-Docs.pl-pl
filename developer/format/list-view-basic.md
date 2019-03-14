---
title: Widok (Basic) listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794165"
---
# <a name="list-view-basic"></a>Widok listy (podstawowy)

W tym przykładzie pokazano, jak zaimplementować wyświetlony widok listy podstawowe [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów zwróconych przez [Get-Service](/powershell/module/microsoft.powershell.management/get-service) polecenia cmdlet. Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Aby załadować ten plik formatowania

1. Skopiuj plik XML z sekcji przykład tego tematu do pliku tekstowego.

2. Zapisz plik tekstowy. Pamiętaj dodać `format.ps1xml` rozszerzenie pliku, aby zidentyfikować go jako plik formatowania.

3. Otwórz program Windows PowerShell i uruchom następujące polecenie, aby załadować plik formatowania do bieżącej sesji: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Ten plik formatowania definiuje wyświetlanie obiektu, który jest już zdefiniowana w pliku formatowania programu Windows PowerShell. Należy użyć `prependPath` parametru po uruchomieniu polecenia cmdlet, a nie można załadować to formatowanie pliku jako moduł.

## <a name="demonstrates"></a>Przedstawiono

Ten plik formatowania pokazuje następujące elementy XML:

- [Nazwa](./name-element-for-view-format.md) elementu widoku.

- [ViewSelectedBy](./viewselectedby-element-format.md) element, który definiuje, jakie obiekty są wyświetlane w widoku.

- [Elementu ListControl](./listcontrol-element-format.md) element, który definiuje, jakie właściwości jest wyświetlany w widoku.

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element, który definiuje, co jest wyświetlane w wierszu w widoku listy.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element, który definiuje, w którym właściwość jest wyświetlana.

## <a name="example"></a>Przykład

Następujący kod XML definiuje widok listy zostaną wyświetlone cztery właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu. W każdym wierszu jest wyświetlana nazwa właściwości, następuje wartość właściwości.

```xml
<Configuration>
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
</Configuration>
```

W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów po załadowaniu tego formatu pliku.

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Zobacz też

[Przykłady formatowania plików](./examples-of-formatting-files.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
