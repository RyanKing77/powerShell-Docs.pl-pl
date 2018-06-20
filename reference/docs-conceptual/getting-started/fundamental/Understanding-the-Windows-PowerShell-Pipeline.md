---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Opis potoku programu Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951073"
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Opis potoku programu Windows PowerShell
Przesyłanie potokowe działa praktycznie wszędzie w programie Windows PowerShell. Mimo że na ekranie zostanie wyświetlony tekst, programu Windows PowerShell nie potoku tekstu polecenia. Zamiast tego należy go powoduje przekazanie w potoku obiektów.

Przypomina notacji używane dla potoków używaną w innych powłoki, dlatego na pierwszy rzut oka może nie być oczywista, programu Windows PowerShell wprowadzono inną. Na przykład, jeśli używasz **wyjściowego hosta** wymusić wyświetlenie strony strona dane wyjściowe z innego polecenia, wygląda danych wyjściowych tylko zwykły tekst wyświetlany na ekranie, podzielić strony, takich jak:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

Out-Host — polecenie stronicowania jest elementem planowanej przydatna zawsze długich danych wyjściowych, który chcesz wyświetlić powoli. Jest szczególnie przydatne, jeśli operacja jest bardzo użycie Procesora CPU. Ponieważ przetwarzanie jest przenoszona do wyjściowego hosta polecenia cmdlet jest gotowy do wyświetlania kompletnej strony, poleceń cmdlet, które należy poprzedzić go w potoku zatrzymanie operacji do czasu następnej strony danych wyjściowych. Użytkownik może wystąpić, jeśli za pomocą Menedżera zadań systemu Windows do monitorowania użycia procesora CPU i pamięci przez środowisko Windows PowerShell.

Uruchom następujące polecenie: **C: Get-ChildItem\\Windows-Recurse**. Porównywanie użycia Procesora i pamięci do tego polecenia: **C: Get-ChildItem\\Windows-Recurse | Host wyjściowego-stronicowania**. Informacje wyświetlane na ekranie jest tekstem, ale jest to ponieważ jest on wymagany do reprezentowania obiektów jako tekst w oknie konsoli. Jest to po prostu reprezentację co naprawdę prowadzone wewnątrz środowiska Windows PowerShell. Rozważmy na przykład polecenia cmdlet Get-lokalizacji. W przypadku wpisania **lokalizacji Get** podczas bieżącej lokalizacji w katalogu głównym dysku C, zobaczysz następujące dane wyjściowe:

```
PS> Get-Location

Path
----
C:\
```

Jeśli środowisko Windows PowerShell potokowe tekstu, wydawania polecenia takie jak **Get-lokalizacji | Host wyjściowego**, przejdzie z **lokalizacji Get** do **wyjściowego hosta** zestaw znaków w kolejności, są wyświetlane na ekranie. Innymi słowy, gdyby Ignoruj informacji nagłówka **wyjściowego hosta** najpierw otrzyma znak "**C"**, następnie znak "**:"**, następnie znak " **\\'**. **Wyjściowego hosta** polecenie cmdlet nie może określić, jakie oznacza do skojarzenia z danych wyjściowych znaków przez **lokalizacji Get** polecenia cmdlet.

Zamiast przy użyciu tekstu, aby umożliwić poleceń w potoku komunikacji, środowiska Windows PowerShell korzysta z obiektów. Z punktu widzenia użytkownika obiekty pakietu powiązane informacje do formularza, który ułatwia manipulować informacjami jako jednostki i określone elementy, które należy wyodrębnić.

**Lokalizacji Get** nie zwróci tekst, który zawiera bieżącej ścieżki. Zwraca pakiet o nazwie informacji **PATHINFO zawiera** obiekt, który zawiera bieżącej ścieżki oraz inne informacje. **Wyjściowego hosta** polecenia cmdlet następnie wysyła tę **PATHINFO zawiera** obiekt do ekranu i środowiska Windows PowerShell, decyduje o informacje do wyświetlania i sposobu ich wyświetlania oparte na regułach jego formatowania.

W rzeczywistości informacji nagłówka danych wyjściowych przez **lokalizacji Get** polecenia cmdlet zostanie dodany tylko na końcu procesu jako część procesu formatowania danych do wyświetlenia na ekranie. Informacje wyświetlane na ekranie jest podsumowanie informacji o, a nie pełny reprezentację obiektu danych wyjściowych.

Biorąc pod uwagę, że może być więcej informacji na dane wyjściowe programu Windows PowerShell polecenia nie możemy wyświetlić wyświetlane w oknie konsoli, jak można pobrać są niewidoczne elementy? Jak wyświetlić dodatkowe dane? I co zrobić, jeśli chcesz wyświetlić dane w innym formacie niż jednego środowiska Windows PowerShell zwykle używa?

Pozostałej części w tym rozdziale opisano, jak można odnajdywać struktury obiektów programu Windows PowerShell, wybierając określone elementy i formatowanie je do wyświetlenia łatwiejsze i jak wysyłać tych informacji do lokalizacji alternatywnej danych wyjściowych, takich jak pliki i drukarki.