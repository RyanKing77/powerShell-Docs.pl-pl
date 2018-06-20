---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189911"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Kryptograficznych składni wiadomości (CMS) polecenia cmdlet.

Polecenia cmdlet składni wiadomości kryptograficznych obsługuje szyfrowanie i odszyfrowywanie zawartości przy użyciu standardowego formatu IETF kryptograficznie ochrony wiadomości w [RFC5652](https://tools.ietf.org/html/rfc5652).

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

Standardowa szyfrowania CMS implementuje kryptografii klucza publicznego, w której klucze używany do szyfrowania zawartości ( *klucz publiczny*) i klucze używane do odszyfrowywania zawartości ( *klucza prywatnego*) są oddzielone.

Klucz publiczny można udostępniać powszechnie i nie jest poufnych danych. Jeśli zawartość jest zaszyfrowany przy użyciu tego klucza publicznego, może odszyfrować tylko klucz prywatny. Aby uzyskać więcej informacji, zobacz [kryptografii klucza publicznego](https://en.wikipedia.org/wiki/Public-key_cryptography).

Zostać rozpoznany w programie PowerShell, certyfikaty szyfrowania wymagają identyfikator unikatowy użycie klucza (EKU), aby zidentyfikować ich jako certyfikaty szyfrowania danych (np. identyfikatory "Podpisywanie kodu", "Szyfrowane poczty").

Poniżej przedstawiono przykład tworzenia certyfikatu, który wystarcza w przypadku szyfrowania dokumentu:

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

Następnie uruchom polecenie:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

I można teraz szyfrowania i odszyfrowywania zawartości:

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

Żadnego parametru typu **CMSMessageRecipient** obsługuje identyfikatory w następujących formatach:
- Rzeczywiste certyfikatu (jako pobrany od dostawcy certyfikatu)
- Ścieżka do pliku zawierającego certyfikat
- Ścieżka do katalogu zawierającego certyfikatu
- Odcisk palca certyfikatu (używane do wyszukiwania w magazynie certyfikatów)
- Nazwa podmiotu certyfikatu (używane do wyszukiwania w magazynie certyfikatów)

Aby wyświetlić certyfikaty szyfrowania dokumentu dostawcę certyfikatów, można użyć **- DocumentEncryptionCert** parametru dynamicznego:

```powershell
dir -DocumentEncryptionCert
```
