---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984344"
---
# <a name="working-with-software-installations"></a>Praca z instalacjami oprogramowania

Aplikacje, które są przeznaczone do przy użyciu Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie za pomocą Instalatora Windows. Ponieważ Instalator Windows zapewnia najszerszą gamę standardowych technik do pracy z aplikacjami do zainstalowania, skupimy się przede wszystkim nad tymi aplikacjami. Aplikacje korzystające z Instalatora alternatywnego procedury ogólnie nie będzie zarządzany przez Instalatora Windows. Określone techniki pracy z tymi aplikacjami zależy od Instalatora oprogramowania i decyzje podjęte przez dewelopera aplikacji.

> [!NOTE]
> Aplikacje, które są instalowane przez skopiowanie plików aplikacji na komputerze, zwykle nie można zarządzać za pomocą techniki opisane poniżej. Te aplikacje jako plików i folderów można zarządzać przy użyciu technik opisanych w sekcji "Praca z pliki i foldery".

## <a name="listing-windows-installer-applications"></a>Wyświetlanie listy aplikacji Instalatora Windows

Aby wyświetlić listę aplikacji, instalowane przy użyciu Instalatora Windows w systemie lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Aby wyświetlić wszystkie właściwości obiektu klasy Win32_Product do wyświetlenia, za pomocą parametru właściwości formatowania poleceń cmdlet, takich jak polecenia cmdlet Format-Lista wartości \* (wszystkie).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Alternatywnie można użyć **filtr Get-WmiObject** parametru, aby wybrać tylko Microsoft .NET Framework 2.0. Ponieważ filtr używany w tym poleceniu jest filtr WMI, używa składni języka zapytań usługi WMI (WQL), nie składni programu Windows PowerShell. Zamiast tego należy:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Należy zauważyć, że często znaki, takie jak spacje lub znaki równości, które mają specjalne znaczenie w programie Windows PowerShell kwerendy WQL. Z tego powodu rozsądne jest zawsze wartość parametru filtru należy ująć w cudzysłów. Można również użyć znaku ucieczki programu Windows PowerShell, początkowych (\`), chociaż nie może to poprawić czytelność. Następujące polecenie jest odpowiednikiem poprzedniego polecenia i zwraca te same wyniki, ale używa początkowych jako znak ucieczki dla znaków specjalnych, zamiast cytowanie ciąg całej filtru.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Aby wyświetlić listę właściwości, które Cię interesują, należy użyć parametru właściwości formatowania poleceń cmdlet programu, aby wyświetlić listę odpowiednich właściwości.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Na koniec można znaleźć tylko nazwy zainstalowanych aplikacji, prostą **całej Format** instrukcji upraszcza dane wyjściowe:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Mimo, że mamy kilka sposobów Przyjrzyj się aplikacji, które są używane Instalatora Windows podczas instalacji, firma Microsoft nie ma uwzględniane innych aplikacji. Większość standardowych aplikacji zarejestrowanie ich dezinstalatora Windows, firma Microsoft może pracować z tymi znajdując je lokalnie w rejestrze systemu Windows.

## <a name="listing-all-uninstallable-applications"></a>Wyświetlanie listy wszystkich do odinstalowania aplikacji

Mimo że nie ma gwarancji możliwości można znaleźć każdej aplikacji w systemie, istnieje możliwość znaleźć wszystkie programy z ofert wyświetlane w oknie dialogowym Dodaj lub usuń programy. Dodaj lub usuń programy znajdzie te aplikacje w następującym kluczu rejestru:

**HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\odinstalować**.

Firma Microsoft można także sprawdzić ten klucz, aby znaleźć aplikacje. Aby ułatwić wyświetlanie klucza Odinstaluj, firma Microsoft zamapuj dysk programu Windows PowerShell do tej lokalizacji rejestru:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** dysk jest mapowany do katalogu głównego **HKEY_LOCAL_MACHINE**, więc użyliśmy tego dysku w ścieżce klucza dezinstalacji. Zamiast **HKLM:** można została określona ścieżka rejestru przy użyciu **HKLM** lub **HKEY_LOCAL_MACHINE**. Zaletą używania istniejącego dysku rejestru to, czy możemy użyć uzupełniania po naciśnięciu tabulatora do wypełnienia w nazwach kluczy, dzięki czemu firma Microsoft nie trzeba wpisywać ich.

W efekcie powstał dysk o nazwie "Odinstaluj", który może służyć do wyszukiwania szybki i wygodny sposób instalacji aplikacji. Możemy znaleźć liczba aplikacji zainstalowanych przez liczenie klucze rejestru w dezinstalacji: Dysk programu Windows PowerShell:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Firma Microsoft można wyszukiwać tej listy dalsze aplikacji za pomocą różnych technik, począwszy od **Get-ChildItem**. Aby uzyskać listę aplikacji i zapisywać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Używamy długiej nazwy zmiennej tutaj dla przejrzystości. W rzeczywistości nie ma powodu używania długich nazwach. Do nazwy zmiennych można używać uzupełniania po naciśnięciu tabulatora, można również użyć nazwy znaków 1 i 2 dla danej szybkości. Dłużej, opisowe nazwy są najbardziej przydatne podczas tworzenia kodu do ponownego wykorzystania.

Aby wyświetlić wartości wpisów rejestru w kluczach rejestru w ramach odinstalowywania, należy użyć metody GetValue kluczy rejestru. Wartość metody jest nazwę wpisu rejestru.

Na przykład można znaleźć nazwy wyświetlane aplikacje w kluczu dezinstalacji, należy użyć następującego polecenia:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Nie ma żadnej gwarancji, że te wartości są unikatowe. W poniższym przykładzie dwa elementy zainstalowane są wyświetlane jako "Windows Media Encoder Seria 9":

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a>Instalowanie aplikacji

Możesz użyć **klasy Win32_Product** klasy w celu zainstalowania pakietów Instalatora Windows, lokalnie i zdalnie.

> [!NOTE]
> W Windows Vista, Windows Server 2008 i nowszych wersjach systemu Windows do zainstalowania aplikacji, należy uruchomić program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) do określenia ścieżki do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu Windows PowerShell. Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym \\ \\AppServ\\dsp na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu Windows PowerShell:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Aplikacje, które nie korzystają z technologii Instalatora Windows może mieć metody specyficzne dla aplikacji dostępnych dla automatycznego wdrażania. Aby ustalić, czy jest to metoda wdrażania automatyzacji, zapoznaj się z dokumentacją dla aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej. W niektórych przypadkach nawet wtedy, gdy dostawca aplikacji nie specjalnie projektowania aplikacji do automatyzacji instalacji Instalator producenta oprogramowania może mieć kilka technik związane z automatyzacją.

## <a name="removing-applications"></a>Usuwanie aplikacji

Usuwanie pakietu Instalatora Windows za pomocą programu Windows PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu. Oto przykład, który wybiera pakiet do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiej filtrować za pomocą **Numer_identyfikacyjny**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Usunięcie innych aplikacji nie jest to jednak takie proste, nawet wtedy, gdy jest wykonywane lokalnie. Znaleziono ciągi dezinstalacji wiersza polecenia dla tych aplikacji, dzięki możliwości wyodrębniania **UninstallString** właściwości. Ta metoda działa w dla aplikacji Instalatora Windows i starszych programów znajdujących się w kluczu dezinstalacji:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Jednak te ciągi nie może być bezpośrednio można używać w wierszu polecenia programu Windows PowerShell bez wprowadzając pewne modyfikacje.

## <a name="upgrading-windows-installer-applications"></a>Uaktualnianie aplikacji Instalatora Windows

Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji. Dzięki tym informacjom można uaktualnić aplikacji za pomocą jednego polecenia programu Windows PowerShell:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```