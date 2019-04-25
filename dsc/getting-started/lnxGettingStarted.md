---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079697"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux

W tym temacie wyjaśniono, jak rozpocząć pracę, przy użyciu programu PowerShell Desired State Configuration (DSC) dla systemu Linux. Aby uzyskać ogólne informacje o DSC, zobacz [Rozpoczynanie pracy z usługą Windows PowerShell Desired State Configuration](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>Obsługiwane wersje systemu operacji systemu Linux

Następujące wersje systemu operacyjnego Linux są obsługiwane dla DSC dla systemu Linux.

- CentOS 5, 6 i 7 — x86/x64 64
- Debian GNU/Linux 6, 7 i 8 — x86/x64 64
- Oracle Linux 5, 6 i 7 — x86/x64 64
- Red Hat Enterprise Linux Server 5, 6 i 7 — x86/x64 64
- SUSE Linux Enterprise Server 10, 11 i 12 — x86/x64 64
- Serwer Ubuntu 12.04 LTS, 14.04 LTS i 16.04 LTS — x86/x64 64

W poniższej tabeli opisano zależności pakietów wymaganych do DSC dla systemu Linux.

|  Wymagany pakiet |  Opis |  Minimalna wersja |
|---|---|---|
| glibc| Biblioteka GNU| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Infrastruktura zarządzania otwartego| 1.0.8.1|
| openssl| Biblioteki OpenSSL| 0.9.8 lub 1.0|
| ctypes| Biblioteka CTypes języka Python| Musi odpowiadać wersji języka Python|
| libcurl| biblioteki klienta http programu cURL| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Instalowanie DSC dla systemu Linux

Należy zainstalować [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) przed zainstalowaniem DSC dla systemu Linux.

### <a name="installing-omi"></a>Instalowanie OMI

Desired State Configuration for Linux wymaga, aby serwer modelu CIM Open Management Infrastructure (OMI), wersja 1.0.8.1 lub nowszej. OMI można pobrać z Open Group: [Otwórz Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Aby zainstalować OMI, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86). Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux. DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server. Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.

> [!NOTE]
> Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie `openssl version`.

Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 OMI.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Instalowanie DSC

DSC dla systemu Linux jest dostępna do pobrania [tutaj](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

Aby zainstalować DSC, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86). Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux. DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server. Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.

> [!NOTE]
> Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie wersją biblioteki openssl.

Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 DSC.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Za pomocą DSC dla systemu Linux

W poniższych sekcjach opisano sposób tworzenia i uruchomionych konfiguracjach DSC na komputerach z systemem Linux.

### <a name="creating-a-configuration-mof-document"></a>Tworzenie dokumentów w pliku MOF konfiguracji

Konfiguracja programu Windows PowerShell — słowo kluczowe jest używany do utworzenia konfiguracji dla komputerów z systemem Linux, podobnie jak na komputerach Windows. W poniższych krokach opisano tworzenie dokumentu konfiguracji dla komputera z systemem Linux przy użyciu programu Windows PowerShell.

1. Zaimportuj moduł nx. Moduł programu Windows PowerShell nx zawiera schemat wbudowane zasoby DSC dla systemu Linux i musi być zainstalowane na komputerze lokalnym i zaimportowane w konfiguracji.

   - Aby zainstalować moduł nx, skopiuj katalog modułu nx do jednej `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` lub `$PSHOME\Modules`. Moduł nx znajduje się w DSC pakietu instalacyjnego systemu Linux. Aby zaimportować moduł nx w konfiguracji, należy użyć `Import-DSCResource` polecenia:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Definiowanie konfiguracji i generowania dokumentu konfiguracji:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Wypychanie konfiguracji na komputerze z systemem Linux

Konfiguracja dokumentów (pliki MOF) może być przyczyną do komputera systemu Linux przy użyciu [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet. Aby można było użyć tego polecenia cmdlet, wraz z [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), lub [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) poleceń cmdlet, zdalnie do komputera z systemem Linux, należy użyć CIMSession. [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) polecenie cmdlet służy do tworzenia CIMSession na komputerze z systemem Linux.

Poniższy kod przedstawia sposób tworzenia CIMSession DSC dla systemu Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> W trybie "Push" poświadczenia użytkownika musi być zalogowany jako użytkownik root na komputerze z systemem Linux.
> Tylko połączeń SSL/TLS są obsługiwane w przypadku DSC dla systemu Linux, `New-CimSession` musi być używana z parametrem – UseSSL ustawionym na $true.
> Certyfikat SSL używany przez OMI (w przypadku DSC) jest określona w pliku: `/opt/omi/etc/omiserver.conf` z właściwościami: pemfile i keyfile.
> Jeśli ten certyfikat nie jest zaufany przez komputer Windows, które są uruchomione [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) polecenia cmdlet na możesz zignorować weryfikację certyfikatu przy użyciu opcji CIMSession: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`

Uruchom następujące polecenie, aby wypchnąć konfiguracji DSC do węzłów systemu Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Dystrybucja konfiguracji z serwera ściągania

Konfiguracje mogą być dystrybuowane do komputera z systemem Linux z serwera ściągania, podobnie jak dla komputerów Windows. Aby uzyskać wskazówki na temat korzystania z serwera ściągania, zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](../pull-server/pullServer.md). Ograniczenia, powiązane z użyciem komputerów z systemem Linux z serwera ściągania i dodatkowe informacje Zobacz informacje o wersji dla Desired State Configuration dla systemu Linux.

### <a name="working-with-configurations-locally"></a>Praca z konfiguracjami lokalnie

DSC dla systemu Linux zawiera skrypty do pracy z konfiguracją z lokalnym komputerze z systemem Linux. Te skrypty są zlokalizuj w `/opt/microsoft/dsc/Scripts` i obejmują następujące elementy:

- GetDscConfiguration.py

Zwraca bieżącą konfigurację, które są stosowane do komputera. Podobne do polecenia cmdlet programu Windows PowerShell `Get-DscConfiguration` polecenia cmdlet.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Zwraca bieżącą meta konfigurację zastosowane do komputera. Podobne do polecenia cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) polecenia cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Instaluje niestandardowego modułu zasobów DSC. Wymaga ścieżkę do pliku zip zawierającego biblioteki udostępnionej obiektów modułu i pliki MOF schematu.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Usuwa niestandardowego modułu zasobów DSC. Wymaga nazwy modułu do usunięcia.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Zastosowanie pliku MOF konfiguracji na komputerze. Podobnie jak [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet. Wymaga ścieżkę do pliku MOF, aby zastosować konfigurację.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Zastosowanie pliku MOF konfiguracji Meta na komputerze. Podobnie jak [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) polecenia cmdlet. Wymaga ścieżkę do pliku MOF konfiguracji Meta do zastosowania.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Program PowerShell Desired State Configuration dla plików dziennika systemu Linux

Następujące pliki dziennika są generowane dla DSC dla systemu Linux wiadomości.

|Plik dziennika|Katalog|Opis|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Komunikaty dotyczące operacji serwer modelu CIM OMI.|
|**dsc.log**|`/var/opt/omi/log`|Komunikaty dotyczące operacji operacje zasobów lokalnych Configuration Manager (LCM) i DSC.|
