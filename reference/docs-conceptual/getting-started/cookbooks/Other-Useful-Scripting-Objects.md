---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Inne przydatne obiekty skryptowe
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a>Inne przydatne obiekty skryptowe

Następujące obiekty oferowanie dodatkowych funkcji obsługi skryptów w środowisku Windows PowerShell ISE. Nie są częścią **$psISE** hierarchii.

## <a name="useful-scripting-objects"></a>Przydatne obiektów skryptów

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Istnieją pewne ograniczenia dotyczące współdziałania programu Windows PowerShell ISE z aplikacji konsoli. Polecenia lub skryptu automatyzacji, który wymaga interwencji użytkownika może nie działać jak działa z konsoli programu Windows PowerShell. Możesz zablokować tych poleceń lub skryptów z poziomu uruchomionej w okienku polecenia programu Windows PowerShell ISE. **$PsUnsupportedConsoleApplications** obiekt przechowuje listę tych poleceń. Jeśli zostanie podjęta próba uruchomienia polecenia na tej liście, możesz uzyskać komunikat, że nie są obsługiwane. Poniższy skrypt dodaje wpis do listy.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Jest to obiekt słownika, który mapuje kontekstowa między tematy pomocy i skojarzonych z nimi łączy w lokalnym skompilowany plik Pomocy HTML. Służy do zlokalizowania lokalnej pomocy dla określonego tematu. Można dodawać lub usuwać tematy z tej listy. Poniższy przykład kodu pokazuje przykładowe pary klucz wartość, które są zawarte w **$psLocalHelp**.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

|||
|-|-|
|Klucz: Komputer|Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Klucza: Zawartość|Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

Poniższy skrypt dodaje wpis do listy.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Jest to obiekt słownika, który mapuje kontekstowa między tytuły tematów tematów pomocy i ich skojarzonych zewnętrzne adresy URL. Służy do lokalizowania określonego tematu pomocy w sieci web. Można dodawać lub usuwać tematy z tej listy.

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

|||
|-|-|
|Klucz: Komputer|Wartość: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Klucza: Zawartość|Wartość: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Poniższy skrypt dodaje wpis do listy.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zobacz też

- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)