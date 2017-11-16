---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Inne przydatne obiekty skryptów"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a>Inne przydatne obiekty skryptów
  Następujące obiekty oferowanie dodatkowych funkcji obsługi skryptów w środowisku Windows PowerShell ISE. Nie są częścią **$psISE** hierarchii.

## <a name="useful-scripting-objects"></a>Przydatne obiektów skryptów

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Istnieją pewne ograniczenia dotyczące współdziałania programu Windows PowerShell ISE z aplikacji konsoli. Polecenia lub skryptu automatyzacji, który wymaga interwencji użytkownika może nie działać jak działa z konsoli programu Windows PowerShell. Możesz zablokować tych poleceń lub skryptów z poziomu uruchomionej w okienku polecenia programu Windows PowerShell ISE. **$PsUnsupportedConsoleApplications** obiekt przechowuje listę tych poleceń. Jeśli zostanie podjęta próba uruchomienia polecenia na tej liście, możesz uzyskać komunikat, że nie są obsługiwane. Poniższy skrypt dodaje wpis do listy.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Jest to obiekt słownika, który mapuje kontekstowa między tematy pomocy i skojarzonych z nimi łączy w lokalnym skompilowany plik Pomocy HTML. Służy do zlokalizowania lokalnej pomocy dla określonego tematu. Można dodawać lub usuwać tematy z tej listy. Poniższy przykład kodu pokazuje przykładowe pary klucz wartość, które są zawarte w **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

|||
|-|-|
|Klucz: Komputer|Wartość: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Klucza: Zawartość|Wartość: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 Poniższy skrypt dodaje wpis do listy.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Jest to obiekt słownika, który mapuje kontekstowa między tytuły tematów tematów pomocy i ich skojarzonych zewnętrzne adresy URL. Służy do lokalizowania określonego tematu pomocy w sieci web. Można dodawać lub usuwać tematy z tej listy.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

|||
|-|-|
|Klucz: Komputer|Wartość: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Klucza: Zawartość|Wartość: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Poniższy skrypt dodaje wpis do listy.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zobacz też
- [Windows PowerShell ISE skryptów modelu obiektów](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
