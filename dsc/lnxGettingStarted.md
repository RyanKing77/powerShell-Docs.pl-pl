---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Rozpoczynanie pracy z konfiguracji żądanego stanu (DSC) dla systemu Linux"
ms.openlocfilehash: fd4820d27de5958a325032ca3fc202a521c131b4
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Rozpoczynanie pracy z konfiguracji żądanego stanu (DSC) dla systemu Linux

W tym temacie wyjaśniono, jak rozpocząć korzystanie z konfiguracji żądanego stanu środowiska PowerShell (DSC) dla systemu Linux. Aby uzyskać ogólne informacje o konfiguracji DSC, zobacz [wprowadzenie do konfiguracji żądanego stanu programu Windows PowerShell](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Obsługiwane wersje systemu operacji systemu Linux

Następujące wersje systemu operacyjnego Linux są obsługiwane dla konfiguracji DSC dla systemu Linux.
- CentOS 5, 6 i 7 (x86/x64)
- Debian GNU/Linux 6, 7 i 8 (x86/x64)
- Oracle Linux 5, 6 i 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 i 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 i 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS i 16.04 LTS (x86/x64)

W poniższej tabeli opisano zależności wymagany pakiet dla konfiguracji DSC dla systemu Linux.

|  Wymagany pakiet |  Opis |  Minimalna wersja | 
|---|---|---|
| Glibc| Biblioteka GNU| 2…4 – 31.30| 
| Python| Python| 2.4 – 3.4| 
| omiserver| Infrastruktura zarządzania otwartego| 1.0.8.1| 
| Biblioteki Openssl| Biblioteki OpenSSL| 0.9.8 lub 1.0| 
| ctypes| Biblioteka języka Python CTypes| Musi odpowiadać wersji języka Python| 
| libcurl| Biblioteka klienta http cURL| 7.15.1| 

## <a name="installing-dsc-for-linux"></a>Instalowanie usługi Konfiguracja DSC dla systemu Linux

Musisz zainstalować [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) przed zainstalowaniem usługi Konfiguracja DSC dla systemu Linux.

### <a name="installing-omi"></a>Instalowanie OMI

Żądany stan konfiguracji dla systemu Linux wymaga serwera modelu wspólnych informacji Open Management Infrastructure (OMI), wersja 1.0.8.1 lub nowszym. OMI można pobrać z Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Aby zainstalować OMI, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersji biblioteki OpenSSL (ssl_098 lub ssl_100) i architektury (x64/x86). Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux SUSE Linux Enterprise Server i Oracle Linux. Pakiety DEB są odpowiednie dla Debian GNU/Linux i Ubuntu Server. Pakiety ssl_098 są odpowiednie dla komputerów z biblioteki OpenSSL 0.9.8 zainstalowane pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.

> **Uwaga**: Aby ustalić, z zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie `openssl version`.

Uruchom następujące polecenie, aby zainstalować OMI w systemie CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Instalowanie usługi Konfiguracja DSC

DSC dla systemu Linux jest dostępna do pobrania [tutaj](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest). 

Aby zainstalować usługi Konfiguracja DSC, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersji biblioteki OpenSSL (ssl_098 lub ssl_100) i architektury (x64/x86). Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux SUSE Linux Enterprise Server i Oracle Linux. Pakiety DEB są odpowiednie dla Debian GNU/Linux i Ubuntu Server. Pakiety ssl_098 są odpowiednie dla komputerów z biblioteki OpenSSL 0.9.8 zainstalowane pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.

> **Uwaga**: Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie wersji biblioteki openssl.
 
Uruchom następujące polecenie, aby zainstalować usługi Konfiguracja DSC w systemie CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Dla systemu Linux przy użyciu usługi Konfiguracja DSC

W poniższych sekcjach opisano sposób tworzenia i uruchamiania na komputerach z systemem Linux konfiguracji DSC.

### <a name="creating-a-configuration-mof-document"></a>Tworzenie dokumentu MOF konfiguracji

Konfiguracja programu Windows PowerShell — słowo kluczowe jest używany do utworzenia konfiguracji dla komputerów z systemem Linux, podobnie jak na komputerach z systemem Windows. W poniższych krokach opisano tworzenie dokumentu konfiguracji dla komputera z systemem Linux przy użyciu programu Windows PowerShell.

1. Zaimportuj moduł nx. Moduł programu Windows PowerShell nx zawiera schemat wbudowany zasobów dla konfiguracji DSC dla systemu Linux i musi być zainstalowana na komputerze lokalnym i zaimportować w konfiguracji.

    — Aby zainstalować moduł nx, skopiuj katalog modułu nx jednej `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` lub `$PSHOME\Modules`. Moduł nx znajduje się w konfiguracji DSC pakietu instalacyjnego systemu Linux (MSI). Aby zaimportować moduł nx w konfiguracji, należy użyć __DSCResource importu__ polecenia:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definiowanie konfiguracji i generowania dokumentu konfiguracji:

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a>Wypychana konfiguracji na komputerze z systemem Linux

Konfiguracja dokumentów (pliki MOF) może zostać umieszczony na komputerze systemu Linux za pomocą [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet. Aby można było używać tego polecenia cmdlet, wraz z [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), lub [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) poleceń cmdlet, zdalnie do komputera z systemem Linux, musi użyć CIMSession. [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenia cmdlet służy do tworzenia CIMSession na komputerze z systemem Linux.

Poniższy kod przedstawia sposób tworzenia CIMSession dla konfiguracji DSC dla systemu Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Uwaga**:
* W trybie "Push" poświadczeń użytkownika musi być użytkownika głównego na komputerze z systemem Linux.
* Dla systemu Linux, New-CimSession musi używać z parametrem – UseSSL wartość $true, dla DSC obsługiwane są tylko połączenia SSL/TLS.
* Certyfikat SSL używany przez OMI (dla DSC) jest określona w pliku: `/opt/omi/etc/omiserver.conf` z właściwościami: pemfile i keyfile.
Jeśli ten certyfikat nie jest zaufany przez komputer z systemem Windows, które są uruchomione [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenia cmdlet na, możesz zignorować weryfikacji certyfikatu przy użyciu opcji CIMSession:`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Uruchom następujące polecenie, aby wypchnąć konfiguracji DSC do węzła systemu Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Przekazują konfigurację z serwerem ściągania

Konfiguracje mogą być dystrybuowane do komputera z systemem Linux na serwerze ściągania, podobnie jak na komputerach z systemem Windows. Aby uzyskać wskazówki dotyczące korzystania z serwera ściągania, zobacz [Windows PowerShell żądanego stanu ściągania serwery konfiguracji](pullServer.md). Dodatkowe informacje i ograniczenia dotyczące korzystania z serwera ściągania komputery z systemem Linux zobacz informacje o wersji dla konfiguracji żądanego stanu dla systemu Linux.

### <a name="working-with-configurations-locally"></a>Praca z konfiguracjami lokalnie

DSC Linux obejmuje skrypty do pracy z konfiguracji z komputera lokalnego systemu Linux. Skrypty te są zlokalizować w `/opt/microsoft/dsc/Scripts` i są następujące:
* GetDscConfiguration.py

 Zwraca bieżącą konfigurację, które są stosowane do komputera. Podobne do polecenia cmdlet programu Windows PowerShell polecenia cmdlet Get-DscConfiguration.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Zwraca bieżącą meta konfigurację zastosowane do komputera. Podobne do polecenia cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) polecenia cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Instaluje niestandardowego modułu zasobów usługi Konfiguracja DSC. Wymaga ścieżkę do pliku zip zawierającego biblioteki udostępnionej modułu i pliki MOF schematu.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Usuwa niestandardowego modułu zasobów usługi Konfiguracja DSC. Wymaga Nazwa modułu do usunięcia.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 Zastosowanie pliku MOF konfiguracji na komputerze. Podobnie jak [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet. Wymaga ścieżka do konfiguracji MOF do zastosowania.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Zastosowanie pliku MOF konfiguracji Meta na komputerze. Podobnie jak [DSCLocalConfigurationManager zestaw](https://technet.microsoft.com/en-us/library/dn521621.aspx) polecenia cmdlet. Wymaga ścieżki do MOF konfiguracji Meta do zastosowania.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Konfiguracja żądanego stanu dla plików dziennika systemu Linux

Następujące pliki dziennika są generowane dla DSC komunikatów systemu Linux.

|Plik dziennika|Katalog|Opis|
|---|---|---|
|omiserver.log|/var/OPT/OMI/log|Komunikaty dotyczące operacji serwera modelu wspólnych informacji OMI.|
|DSC.log|/var/OPT/OMI/log|Komunikaty dotyczące operacji operacji zasobu lokalnego Configuration Manager (LCM) i usługi Konfiguracja DSC.|

