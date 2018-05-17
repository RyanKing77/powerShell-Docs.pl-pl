---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Odinstaluj PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a>Odinstaluj PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Odinstalowuje Windows PowerShell® aplikacji sieci web.

## <a name="syntax"></a>SKŁADNIA

### <a name="default"></a>Wartość domyślna
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Uninstall-PswaWebApplication** polecenia cmdlet powoduje odinstalowanie aplikacji sieci web programu Windows PowerShell i usuwa witryny sieci Web usług IIS. Polecenie cmdlet nie powoduje odinstalowania usług IIS lub innych funkcji zainstalowane, ponieważ są wymagane dla środowiska Windows PowerShell do uruchamiania.

## <a name="parameters"></a>PARAMETRY

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Wskazuje, że certyfikaty testowe utworzone przez **zainstalować\_PswaWebApplication** polecenia cmdlet (z **UseTestCertificate** parametru) zostaną usunięte.
Tylko certyfikatu testowego z taką samą nazwę jak utworzony przez **Install-PswaWebApplication** polecenia cmdlet zostanie usunięta.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | true                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;ciągu&gt;

Określa nazwę aplikacji sieci web do odinstalowania.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | pswa                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-websitename-ltstringgt"></a>-Podaną &lt;ciągu&gt;

Określa nazwę witryny sieci web, w którym zainstalowano aplikację sieci web.

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

To polecenie cmdlet nie zwraca żadnych danych wyjściowych.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

To polecenie spowoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell.
To polecenie cmdlet służy do odinstalowania aplikacji sieci Web programu Windows PowerShell, jeśli został zainstalowany przy użyciu wartości domyślnych.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>PRZYKŁAD 2

To polecenie powoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell i usuwa certyfikatu testowego skojarzone z aplikacją.
To polecenie cmdlet służy do odinstalowania aplikacji sieci Web programu Windows PowerShell, jeśli po zainstalowaniu go przy użyciu wartości domyślnych utworzony certyfikat testowy.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>PRZYKŁAD 3 {.subHeading #example-3}

To polecenie spowoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell po niestandardowej witryny sieci Web i aplikacji, które zostały określone podczas instalacji.
Polecenie usuwa witryny sieci Web o nazwie *witryna* i aplikację o nazwie *kategorii Aplikacja_testowa* i Określa certyfikaty testu skojarzone z aplikacją również zostaną usunięte.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Tematy pokrewne

- [Polecenia Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)