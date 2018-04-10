---
description: ''
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Usuń pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell® Web Access.

## <a name="syntax"></a>SYNTAX

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Reguły
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell Web Access.

## <a name="parameters"></a>PARAMETRY

### <a name="-force"></a>-Force

Uruchamia polecenie cmdlet bez monitowania o potwierdzenie. Domyślnie polecenia cmdlet wyświetlona prośba o potwierdzenie przed kontynuowaniem.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Określa identyfikatory (ID) jeden lub więcej reguł do usunięcia.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue, ByPropertyName)       |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Reguły &lt;PswaAuthorizationRule\[\]&gt;

Określa reguły do usunięcia.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue)                       |
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

Pokazuje, co się stanie po uruchomieniu polecenia cmdlet. Polecenie cmdlet nie zostało uruchomione.

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

### <a name="int"></a>int\[\]

To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.

## <a name="outputs"></a>DANE WYJŚCIOWE

To polecenie cmdlet nie generuje żadnych danych wyjściowych.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie usuwa regułę autoryzacji z Identyfikatorem *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>PRZYKŁAD 2 {.subHeading #example-2}

W tym przykładzie powoduje usunięcie wszystkich reguł autoryzacji i wymaga także potwierdzenia przez użytkownika.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Tematy pokrewne

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)