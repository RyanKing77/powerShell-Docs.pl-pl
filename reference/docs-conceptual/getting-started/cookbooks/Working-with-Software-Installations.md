---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-software-installations"></a>Praca z instalacjami oprogramowania

Aplikacje, które są przeznaczone do użycia Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie, używając Instalatora Windows. Ponieważ Instalator systemu Windows zapewnia szeroką gamą standardowych technik do pracy z aplikacjami można zainstalować, możemy koncentruje się przede wszystkim na te aplikacje. Aplikacje używające Instalatora alternatywnego procedury zazwyczaj nie będą zarządzane przez Instalatora Windows. Określone techniki pracy z tymi aplikacjami zależy od Instalatora oprogramowania i decyzje podjęte przez dewelopera aplikacji.

> [!NOTE]
> Aplikacje zainstalowane przez kopiowanie plików aplikacji na komputerze, zwykle nie można zarządzać za pomocą techniki opisane w tym miejscu. Te aplikacje, jak pliki i foldery można zarządzać za pomocą techniki opisane w sekcji "Praca z pliki i foldery".

### <a name="listing-windows-installer-applications"></a>Wyświetlanie listy aplikacji Instalatora systemu Windows

Aby wyświetlić listę aplikacji zainstalowanych przy użyciu Instalatora Windows na komputerze lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Aby wyświetlić wszystkie właściwości obiektu klasy Win32_Product do wyświetlenia, użyj parametru właściwości formatowania poleceń cmdlet, takich jak polecenia cmdlet Format listy o wartości \* (wszystkie).

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

Można użyć **filtru Get-WmiObject** parametr, aby wybrać tylko Microsoft .NET Framework 2.0. Ponieważ filtr używane w tym poleceniu jest filtr WMI, używa składni języka zapytań usługi WMI (WQL), nie składnię Windows PowerShell. Zamiast tego należy:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Należy pamiętać, że kwerendy WQL często Użyj znaków, takich jak spacji lub znaku równości, które mają specjalne znaczenie w programie Windows PowerShell. Z tego powodu rozsądne jest zawsze wartość parametru filtru należy ująć w cudzysłów. Można również użyć znak ucieczki środowiska Windows PowerShell, backtick (\`), ale nie może to poprawić czytelność. Polecenie jest odpowiednikiem poprzedniego polecenia i zwraca wyniki, ale używa backtick ucieczki znaków specjalnych, zamiast zamykający ciąg filtru całego.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Aby wyświetlić listę tylko właściwości, które są potrzebne, użyj parametru właściwości formatowania poleceń cmdlet do żądanej właściwości listy.

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

Na koniec, aby znaleźć tylko nazwy zainstalowanych aplikacji, prosty **całej Format** instrukcji upraszcza dane wyjściowe:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Teraz mamy kilka sposobów, aby przyjrzeć się aplikacji, które są używane do instalacji Instalatora Windows, firma Microsoft ma być nie omówiono inne aplikacje. Ponieważ większość standardowych aplikacji zarejestrować ich dezinstalatora z systemem Windows, firma Microsoft może współpracować z tymi lokalnie, znajdowanie je w rejestrze systemu Windows.

### <a name="listing-all-uninstallable-applications"></a>Wyświetlanie listy wszystkich do odinstalowania aplikacji

Nie ma gwarantowane można znaleźć każdej aplikacji w systemie, ale istnieje możliwość znaleźć wszystkie programy z listy wyświetlanych w oknie dialogowym Dodaj lub usuń programy. Dodaj lub usuń programy znajduje tych aplikacji w następującym kluczu rejestru:

**HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\odinstalować**.

Omówione można również ten klucz, aby znaleźć aplikacji. Aby ułatwić wyświetlić klucz Odinstaluj, możemy Mapuj dysk programu Windows PowerShell do tej lokalizacji w rejestrze:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** stacja jest mapowana do katalogu głównego **HKEY_LOCAL_MACHINE**, przez co możemy użyć ścieżki do klucza Odinstaluj tego dysku. Zamiast **HKLM:** można została określona ścieżka rejestru za pomocą **HKLM** lub **HKEY_LOCAL_MACHINE**. Zaletą korzystania z istniejącym dyskiem rejestru jest wypełnianie nazw kluczy, dlatego firma Microsoft nie trzeba wpisywać ich używanie uzupełniania po naciśnięciu tabulatora.

Mamy teraz dysk o nazwie "Odinstaluj", który może służyć do wyszukiwania szybko i wygodnie instalacje aplikacji. Znaleźliśmy liczba zainstalowanych aplikacji liczbą kluczy rejestru dezinstalacji: dysk programu Windows PowerShell:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Firma Microsoft można wyszukiwać tej listy dodatkowe aplikacje za pomocą różnych technik, począwszy od **Get-ChildItem**. Aby uzyskać listę aplikacji i zapisać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Użyto długich nazwę zmiennej tutaj dla uzyskania przejrzystości. W rzeczywistości nie ma ma powodu do użycia długie nazwy. Do nazwy zmiennych mogą używać uzupełniania po naciśnięciu tabulatora, również można użyć nazwy znaków 1 i 2 dla danej szybkości. Nazwy dłuższe, opisowe są najbardziej przydatne podczas tworzenia kodu do ponownego użycia.

Aby wyświetlić wartości wpisów rejestru w kluczach rejestru, w obszarze dezinstalacji, należy użyć metody GetValue kluczy rejestru. Wartość metody jest nazwą wpisu rejestru.

Na przykład aby znaleźć nazwy wyświetlanej aplikacji w kluczu Odinstaluj, użyj następującego polecenia:

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

### <a name="installing-applications"></a>Instalowanie aplikacji

Można użyć **klasy Win32_Product** klasy instalowania pakietów Instalatora Windows lokalnie i zdalnie.

> [!NOTE]
> W systemie Windows Vista, Windows Server 2008 i nowszych wersjach systemu Windows Aby zainstalować aplikację, należy uruchomić środowiska Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) należy określić ścieżkę do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu Windows PowerShell. Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym \\ \\AppServ\\dsp na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu Windows PowerShell:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Aplikacje, które nie korzystają z technologii Instalatora systemu Windows mogą mieć specyficzne dla aplikacji dostępne metody automatycznego wdrażania. Aby ustalić, czy jest to metoda automatyzacji wdrażania, zajrzyj do dokumentacji aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej. W niektórych przypadkach nawet wtedy, gdy z dostawcą aplikacji nie specjalnie projektowania aplikacji do automatyzacji instalacji Instalator producenta oprogramowania może mieć niektóre metody automatyzacji.

### <a name="removing-applications"></a>Usuwanie aplikacji

Usuwanie pakietu Instalatora Windows za pomocą środowiska Windows PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu. Oto przykład, który wybiera pakietu do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiejsze do filtrowania z **numerowi**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Usunięcie inne aplikacje nie jest dość tak proste, nawet wtedy, gdy wykonywane lokalnie. Firma Microsoft można znaleźć ciągi dezinstalacji wiersza polecenia dla tych aplikacji, wyodrębniając **UninstallString** właściwości. Ta metoda działa w aplikacji Instalatora systemu Windows i starszych programów znajdujących się w kluczu dezinstalacji:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Jednak te ciągi nie może być bezpośrednio można używać z wierszu polecenia programu Windows PowerShell bez modyfikacji niektórych.

### <a name="upgrading-windows-installer-applications"></a>Uaktualnianie aplikacji Instalatora systemu Windows

Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji. Z tych informacji można uaktualnić aplikację za pomocą jednego polecenia programu Windows PowerShell:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```