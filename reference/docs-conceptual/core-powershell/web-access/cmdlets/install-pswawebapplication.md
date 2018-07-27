---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268303"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Umożliwia skonfigurowanie aplikacji sieci web programu Windows PowerShell Web Access w usługach IIS.

## <a name="syntax"></a>SKŁADNIA

### <a name="default"></a>Wartość domyślna
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Install-PswaWebApplication** polecenie cmdlet umożliwia skonfigurowanie aplikacji sieci web programu Windows PowerShell Web Access.
To polecenie cmdlet instaluje aplikację sieci web, kojarzy ją z witryny sieci web i opcjonalnie tworzy test SSL certyfikatu przy użyciu **useTestCertificate** parametru. Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego w środowiskach produkcyjnych.

## <a name="parameters"></a>PARAMETRY

### <a name="-usetestcertificate"></a>-UseTestCertificate

Określa, czy certyfikat testowy został utworzony. Jeśli ten parametr ma wartość true, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access, aby użyć certyfikatu dla żądania HTTPS. Jeśli ten parametr ma wartość false, następnie nie powiązania lub certyfikat zostanie utworzony. Wartość tę należy ustawić na wartość false, jeśli jest używany inny certyfikat, programu Windows PowerShell Web Access.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | true                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Określa nazwę aplikacji sieci web. Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | pswa                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-websitename"></a>-Podaną nazwą

Określa nazwę witryny sieci Web serwer sieci Web (IIS), na którym chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | Domyślna witryna sieci Web                     |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-confirm"></a>-Confirm

Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.

|||
|-|-|
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | false                                |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-whatif"></a>-WhatIf

Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.
Polecenie cmdlet nie zostało uruchomione.

|||
|-|-|
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | false                                |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer oraz - OutVariable. Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>DANE WEJŚCIOWE

To polecenie cmdlet nie wymaga danych wejściowych.

## <a name="outputs"></a>DANE WYJŚCIOWE

To polecenie cmdlet nie generuje żadnych danych wyjściowych.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie instaluje przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną nazwą** (*domyślna witryna sieci Web* ) parametry.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>PRZYKŁAD 2

W tym przykładzie instaluje PSWA aplikacji sieci web przy użyciu certyfikatu testowego i przy użyciu wartości domyślnych dla **WebApplicationName** i **podaną nazwą** parametrów.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Tematy pokrewne

- [Polecenia Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)