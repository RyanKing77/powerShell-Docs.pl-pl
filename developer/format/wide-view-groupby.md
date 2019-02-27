---
title: Szerokie (grupowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850750"
---
# <a name="wide-view-groupby"></a>Widok szeroki (GroupBy)

W tym przykładzie pokazano, jak zaimplementować szerokie, który wyświetla grupy [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów zwróconych przez `Get-Service` polecenia cmdlet. Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Aby załadować ten plik formatowania

1. Skopiuj plik XML z sekcji przykład tego tematu do pliku tekstowego.

2. Zapisz plik tekstowy. Pamiętaj dodać `format.ps1xml` rozszerzenie pliku, aby zidentyfikować go jako plik formatowania.

3. Otwórz program Windows PowerShell i uruchom następujące polecenie, aby załadować plik formatowania do bieżącej sesji: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Ten plik formatowania definiuje wyświetlanie obiektu, który jest już zdefiniowany programu Windows PowerShell, formatowanie plików. Należy użyć `prependPath` parametru po uruchomieniu polecenia cmdlet, a nie można załadować to formatowanie pliku jako moduł.

## <a name="demonstrates"></a>Przedstawiono

Ten plik formatowania pokazuje następujące elementy XML:

- [Nazwa](./name-element-for-view-format.md) elementu widoku.

- [ViewSelectedBy](./viewselectedby-element-format.md) element, który definiuje, jakie obiekty są wyświetlane w widoku.

- [GroupBy](./groupby-element-for-view-format.md) element, który definiuje, gdy zostanie wyświetlona nowa grupa.

- [WideItem](./wideitem-element-for-widecontrol-format.md) element, który definiuje, jakie właściwości jest wyświetlany w widoku.

## <a name="example"></a>Przykład

Następujący kod XML definiuje szerokie, który wyświetla grupy obiektów. Każda nowa grupa została uruchomiona po wartości [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów po załadowaniu tego formatu pliku.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>Zobacz też

[Przykłady formatowania plików](./examples-of-formatting-files.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
