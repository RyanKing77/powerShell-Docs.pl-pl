---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Inne przydatne obiekty skryptowe
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086208"
---
# <a name="other-useful-scripting-objects"></a>Inne przydatne obiekty skryptowe

Następujące obiekty zapewniają dodatkowe funkcje obsługi skryptów w środowisku Windows PowerShell ISE. Nie są one częścią **$psISE** hierarchii.

## <a name="useful-scripting-objects"></a>Przydatne obiekty skryptów

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Istnieją pewne ograniczenia dotyczące współdziałania programu Windows PowerShell ISE z aplikacji konsoli. Polecenia lub skryptów automatyzacji, który wymaga interwencji użytkownika mogą nie działać w sposób, w jaki działa z poziomu konsoli programu Windows PowerShell. Można zablokować tych poleceń lub skryptów działających w okienku polecenia programu Windows PowerShell ISE. **$PsUnsupportedConsoleApplications** obiekt przechowuje listę tych poleceń. Jeśli zostanie podjęta próba uruchomienia polecenia na tej liście, otrzymasz komunikat, że nie są obsługiwane. Poniższy skrypt dodaje wpis do listy.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Jest to obiekt słownika, który przechowuje kontekstową mapowanie między tematy pomocy i skojarzonych z nimi łączy w lokalnym pliku Pomocy HTML skompilowany. Jest ona używana do lokalizowania pomocy lokalnej do określonego tematu. Można dodać lub usunąć tematy z tej listy. Poniższy przykład kodu przedstawia przykładowe pary klucz wartość, które są zawarte w `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Poniższy skrypt dodaje wpis do listy.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Jest to obiekt słownika, który przechowuje kontekstową mapowanie między tytuły tematów tematów pomocy i ich skojarzone zewnętrzne adresy URL. Jest ona używana do lokalizowania pomoc dotyczącą określonego tematu w sieci web. Można dodać lub usunąć tematy z tej listy.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

Poniższy skrypt dodaje wpis do listy.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zobacz też

[Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)