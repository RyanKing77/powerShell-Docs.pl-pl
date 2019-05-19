---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Nowe i zaktualizowane polecenia cmdlet
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856245"
---
# <a name="new-and-updated-cmdlets"></a>Nowe i zaktualizowane polecenia cmdlet

Dodaliśmy nowe i zaktualizowane istniejące polecenia cmdlet na podstawie opinii społeczności.

## <a name="archive-cmdlets"></a>Polecenia cmdlet archiwum

Dwa nowe polecenia cmdlet `Compress-Archive` i `Expand-Archive`systemowi Kompresuj i rozwiń plików ZIP.

Aby uzyskać więcej informacji, zobacz [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) dokumentacji modułu.

## <a name="catalog-cmdlets"></a>Polecenia cmdlet wykazu

Dodano dwa nowe polecenia cmdlet w Microsoft.PowerShell.Security module.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Te Generowanie i zweryfikować pliki w katalogu Windows.

## <a name="clipboard-cmdlets"></a>Polecenia cmdlet schowka

`Get-Clipboard` i `Set-Clipboard` ułatwić transferu zawartości do i z sesji środowiska Windows PowerShell. Polecenia cmdlet Schowka obsługuje obrazy, pliki audio, listy plików i tekst.

Aby uzyskać więcej informacji, zobacz:

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Zestaw Schowka](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Kryptograficznych polecenia cmdlet składni wiadomości (CMS)

Polecenia cmdlet składnię komunikatów kryptograficznych obsługują szyfrowanie i odszyfrowywanie zawartości przy użyciu formatu standardowego IETF kryptograficznie ochrony wiadomości, zgodnie z opisem przez [RFC5652](https://tools.ietf.org/html/rfc5652).

Standardowa szyfrowania CMS implementuje kryptografii klucza publicznego, w którym klucz używany do szyfrowania zawartości ( *klucza publicznego*) i klucz używany do odszyfrowywania zawartości ( *klucza prywatnego*) są oddzielone.

Klucz publiczny może być powszechnie udostępniony i nie jest poufnych danych. Żadnej zawartości, szyfrowane przy użyciu klucza publicznego odszyfrować je mogą tylko przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz [kryptografii klucza publicznego](https://en.wikipedia.org/wiki/Public-key_cryptography).

Aby uzyskać więcej informacji, zobacz:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Ochrona CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

Certyfikaty wymagają identyfikator unikatowy użycia klucza (EKU), takie jak "Podpisywanie kodu" lub "Zaszyfrowanych wiadomości E-mail", aby je zidentyfikować jako certyfikaty szyfrowania danych w programie PowerShell. Aby wyświetlić certyfikaty szyfrowania dokumentu dostawcę certyfikatów, można użyć **DocumentEncryptionCert** parametru dynamicznego `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Wyodrębnianie i analizowanie obiektów ze strukturą z zawartości ciągu

### <a name="convertfrom-string"></a>ConvertFrom-String

Nowy `ConvertFrom-String` polecenie cmdlet obsługuje dwa tryby:

- Basic rozdzielonych analizy
- Wygenerowany automatycznie oparte na przykładzie analizy

Rozdzielany podczas analizowania, domyślnie dzieli dane wejściowe na biały znak, a następnie przypisuje nazwy właściwości do wynikowego grup.

**UpdateTemplate** parametr zapisuje wyniki algorytmu uczenia na komentarz w pliku szablonu. Dzięki temu learning przetwarzania kosztu jednorazowe (etap najwolniejsze). Uruchamianie `ConvertFrom-String` przy użyciu szablonu, który zawiera algorytmu uczenia zakodowany jest teraz prawie natychmiastowe.

Aby uzyskać więcej informacji, zobacz [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` Umożliwia podanie przed i po przykłady sposobu tekstu do wyszukiwania. Polecenia cmdlet, które automatycznie formatowania tekstu.

Aby uzyskać więcej informacji, zobacz [przekonwertować ciągu](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Aktualizacje obiektu FileInfo

Informacje o wersji pliku mogą mylące, zwłaszcza w przypadkach, w której plik został poprawek. Program WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** skryptu właściwości **FileInfo** obiektów.
Oto właściwości wyświetlane powershell.exe (przy założeniu, że $pid jest identyfikator procesu programu PowerShell):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` Umożliwia wyświetlanie danych tekstowych lub binarnych w formacie szesnastkowym.

Aby uzyskać więcej informacji, zobacz [Format szesnastkowy](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Polecenie GET-ChildItem ma parametr - Depth

`Get-ChildItem` ma teraz **głębokość** parametr do użycia z usługą **Recurse** ograniczyć rekursji:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Obsługa modułów na potrzeby deklarowania zakresów wersji (1.* itp.)

Teraz można połączyć **MinimumVersion** i **MaximumVersion** można zaimportować modułu w obrębie określonego zakresu. Parametry obsługują także symboli wieloznacznych.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Istnieje wiele scenariuszy, w którym youneed Unikatowy identyfikator. `New-GUID` Polecenie cmdlet zapewnia prosty sposób utworzyć nowego identyfikatora GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Parametr NoNewLine

`Out-File`, `Add-Content`, i `Set-Content` powstał nowy **NoNewline** przełącznika, który umożliwia pominięcie znakiem nowego wiersza po danych wyjściowych. Przykład:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

Bez **NoNewline** określony, poszczególne fragmenty powinna znajdować się w osobnym wierszu:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interakcja z symboliczne linki korzystające z poleceń cmdlet elementów ulepszone

Polecenie cmdlet elementu i kilka powiązane polecenia cmdlet zostały rozszerzone do obsługi łącza symbolicznego.

### <a name="symbolic-link-files"></a>Łącza symbolicznego, pliki

W tym przykładzie utworzymy nowy plik łącze symboliczne o nazwie MySymLinkFile.txt w C:\Temp, który stanowi łącze do $pshome\profile.ps1. Wszystkie trzy przykłady generuje ten sam wynik.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Łącze symboliczne katalogów

W tym przykładzie utworzymy nowego katalogu łącze symboliczne o nazwie MySymLinkDir w C:\Temp, który stanowi łącze do folderu $pshome. Wszystkie trzy przykłady generuje ten sam wynik.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Twarde linki

Tej samej kombinacji **ścieżki** i **nazwa** dozwolone zgodnie z powyższym opisem.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Katalog w punktach transferu

Tej samej kombinacji **ścieżki** i **nazwa** dozwolone zgodnie z powyższym opisem.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` teraz wyświetla "l" w **tryb** właściwości do wskazania łącze symboliczne pliku lub katalogu.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

Usuwanie łącza symbolicznego działa jak usuwanie dowolny inny typ elementu.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Użyj **życie** parametru, aby usunąć pliki w katalogu docelowego i łącza symbolicznego.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Czasami w skryptach, można utworzyć pliku tymczasowego. Teraz możesz zrobić to za pomocą `New-TemporaryFile` polecenia cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell

Przełącznika sieci poleceń cmdlet, wprowadzone w programie WMF 5.0 umożliwiają zastosowanie przełącznika, wirtualnej sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych z certyfikatem logo systemu Windows Server 2012 R2. Za pomocą tych poleceń cmdlet można wykonywać:

- Globalne przełącznika konfiguracji, takich jak:
  - Ustaw nazwę hosta
  - Transparent przełącznik set
  - Zachowaj konfigurację
  - Włącza lub wyłącza funkcję

- Konfiguracja sieci VLAN:
  - Tworzenie lub usuwanie sieci VLAN
  - Włączanie lub wyłączanie sieci VLAN
  - Wyliczanie sieci VLAN
  - Przyjazna nazwa zestawu do sieci VLAN

- Konfiguracja portu warstwy 2:
  - Wyliczanie portów
  - Włączać lub wyłączać porty
  - Tryby portu zestawu i właściwości
  - Dodawanie lub kojarzenie sieci VLAN na magistrali lub dostęp przy użyciu portu

Aby uzyskać więcej informacji, zobacz [NetworkSwitchManager](/powershell/module/networkswitchmanager/) dokumentacji.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generowanie poleceń cmdlet programu PowerShell w oparciu o punkt końcowy OData z ODataUtils

Moduł ODataUtils umożliwia generowanie poleceń cmdlet programu PowerShell z punkty końcowe REST, które obsługują OData. Moduł Microsoft.PowerShell.ODataUtils obejmuje następujące funkcje:

- Kanał dodatkowe informacje z punktu końcowego po stronie serwera po stronie klienta.
- Obsługa stronicowania po stronie klienta
- Filtrowanie po stronie serwera, za pomocą wybierz parametr -
- Obsługa nagłówków żądań sieci web

Polecenia cmdlet serwera proxy generowany przez `Export-ODataEndPointProxy` polecenia cmdlet zawierają dodatkowe informacje z punktu końcowego OData po stronie serwera, o **informacji** strumienia.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

W poniższym przykładzie jesteśmy podczas pobierania produktu i przechwytywania danych wyjściowych w `$infoStream` zmiennej.

Określając **IncludeTotalResponseCount** parametru, uzyskujemy łącznej liczby wszystkich **produktu** rekordów dostępne na serwerze.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Rekordy można uzyskać z serwera w gałęziach, używając obsługę stronicowania po stronie klienta. Jest to przydatne, jeśli musi pobrać dużą ilość danych z serwera za pośrednictwem sieci.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Polecenia cmdlet wygenerowany serwer proxy obsługuje **wybierz** parametr, który jest używany jako filtr do odbierania właściwości rekordu, wymaganych przez klienta. Filtrowanie odbywa się na serwerze, co zmniejsza ilość danych przesyłanych przez sieć.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

`Export-ODataEndpointProxy` Polecenia cmdlet i polecenia cmdlet serwera proxy, generowane przez nią, obsługują teraz **nagłówki** parametru. Nagłówek może służyć do kanału dodatkowe informacje, oczekiwany przez punkt końcowy OData.

W poniższym przykładzie, tabelę mieszania, zawierający klucz subskrypcji znajduje się na **nagłówki** parametru. Jest to typowy przykład dla usług, które są oczekiwane klucz subskrypcji na potrzeby uwierzytelniania.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
