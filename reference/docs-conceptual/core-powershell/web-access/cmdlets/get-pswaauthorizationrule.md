---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Zwraca zestaw reguł autoryzacji programu Windows PowerShell® Web Access.

## <a name="syntax"></a>Składnia

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Nazwa
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Get-PswaAuthorizationRule** polecenie cmdlet zwraca zestaw reguł autoryzacji programu Windows PowerShell® Web Access.
Jeśli żadna **identyfikator** parametru ani **RuleName** określony parametr, a następnie to polecenie cmdlet wyświetla listę wszystkich reguł. **Identyfikator** parametru może służyć do filtrowania wyników.

## <a name="parameters"></a>PARAMETRY

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Określa identyfikatory (ID) reguł, które należy uzyskać tego polecenia cmdlet. Jeżeli nie określono żadnych identyfikatorów, to polecenie cmdlet zwraca wszystkie reguły autoryzacji.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue, ByPropertyName)       |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;ciągu\[\]&gt;

Określa nazwy reguł autoryzacji do pobrania. Ten parametr zwraca wszystkie reguły odpowiadające dokładnie nazwy reguł w tej tablicy ciągów.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue, ByPropertyName)       |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;Parametry&gt;

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.
Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>DANE WEJŚCIOWE

### <a name="int"></a>int\[\]

To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablica wartości typu string jako dane wejściowe.

### <a name="string"></a>Ciąg\[\]

To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablica wartości typu string jako dane wejściowe.

## <a name="outputs"></a>DANE WYJŚCIOWE

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

To polecenie cmdlet tworzy obiekt PswaAuthorizationRule jako dane wyjściowe.


## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie pobiera wszystkie reguły.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>PRZYKŁAD 2

W tym przykładzie pobiera reguła o identyfikatorze *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>PRZYKŁAD 3 {.subHeading #example-3}

W tym przykładzie pokazano, jak polecenie cmdlet przyjmuje wartość z potoku.
Identyfikator reguły i nazwę reguły są przekazywane w tym poleceniu cmdlet.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Tematy pokrewne

- [Polecenia Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)