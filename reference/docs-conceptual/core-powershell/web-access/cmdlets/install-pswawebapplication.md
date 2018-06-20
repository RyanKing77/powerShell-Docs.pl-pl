---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189605"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Konfiguruje aplikację sieci web programu Windows PowerShell® Web Access w usługach IIS.

## <a name="syntax"></a>SKŁADNIA

### <a name="default"></a>Wartość domyślna
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Install-PswaWebApplication** polecenia cmdlet konfiguruje aplikację sieci web programu Windows PowerShell Web Access. To polecenie cmdlet instaluje aplikację sieci web, kojarzy go z witryny sieci web i opcjonalnie tworzy, używając certyfikatu SSL testu **useTestCertificate** parametru. Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego dla środowisk produkcyjnych.

## <a name="parameters"></a>PARAMETRY

### <a name="-usetestcertificate"></a>-UseTestCertificate

Określa, czy certyfikat testowy został utworzony. Jeśli ten parametr ma ustawioną wartość PRAWDA, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access do używania certyfikatu dla żądania HTTPS. Jeśli ten parametr ma wartość false, następnie nie certyfikatu powiązania jest utworzone lub. Wartość tę należy ustawić na wartość false, jeśli inny certyfikat jest używany dla programu Windows PowerShell Web Access.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | true                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;ciągu&gt;

Określa nazwę aplikacji sieci web. Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | pswa                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-websitenameltstringgt"></a>-Podaną&lt;ciągu&gt;

Określa nazwę witryny sieci Web serwer sieci Web (IIS), na których chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.

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

### <a name="ltcommonparametersgt"></a>&lt;Parametry&gt;

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.
Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>DANE WEJŚCIOWE

To polecenie cmdlet nie wymaga danych wejściowych.

## <a name="outputs"></a>DANE WYJŚCIOWE

To polecenie cmdlet nie generuje żadnych danych wyjściowych.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

Instalacja przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną** (*domyślnej witryny sieci Web* ) parametrów.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>PRZYKŁAD 2

Instalacja aplikacji sieci web PSWA z certyfikatu testowego i przy użyciu wartości domyślnych **WebApplicationName** i **podaną** parametrów.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Tematy pokrewne

- [Polecenia Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)