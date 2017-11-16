---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>STRESZCZENIE

Sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.

## <a name="syntax"></a>SKŁADNIA

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Test-PswaAuthorizationRule** polecenia cmdlet sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.
To polecenie cmdlet może również służyć do testowania reguł autoryzacji, aby sprawdzić, czy z określonym żądaniem dostępu użytkowników, komputerów lub punkt końcowy jest autoryzowany.
Domyślnie to polecenie cmdlet ocenia wszystkie reguły w pliku autoryzacji.
Można jednak określić podzbiór reguł do przetestowania.

To polecenie cmdlet służy do rozwiązywania problemów niepowodzenia uwierzytelniania.

Parametrami tego polecenia cmdlet odpowiadają polom na stronie logowania programu Windows PowerShell® Web Access.

## <a name="parameters"></a>PARAMETRY

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;ciągu&gt;

Określa nazwę komputera, aby przetestować.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | Wartość true                                 |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;ciągu&gt;

Określa nazwę konfiguracji sesji programu Windows PowerShell, znana także jako punktu końcowego lub obszaru działania, aby przetestować.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | 3                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;identyfikatora Uri&gt;

Określa identyfikator URI, aby przetestować połączenie.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | Wartość true                                 |
| Pozycja?                            | 2                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz używać do testowania reguł autoryzacji programu Windows PowerShell Web Access. Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika. Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby zdalnie testowanie reguł autoryzacji, uruchom [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) polecenia cmdlet.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Reguły &lt;PswaAuthorizationRule\[\]&gt;

Określa podzbiór reguł do przetestowania. Jeśli ten parametr nie jest określony, to polecenie cmdlet testy względem wszystkich reguł autoryzacji.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue)                       |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;ciągu&gt;

Określa nazwę użytkownika do testowania.

|||  
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | Wartość true                                 |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;Parametry&gt;

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.
Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>DANE WEJŚCIOWE

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

To polecenie cmdlet akceptuje tablicę obiektów PswaAuthorizationRule jako dane wejściowe.

## <a name="outputs"></a>DANE WYJŚCIOWE

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

To polecenie cmdlet tworzy tablicę obiektów PswaAuthorizationRule jako dane wyjściowe.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie testów wszystkich reguł autoryzacji, aby wyświetlić wszystkie reguły, które umożliwiają użytkownikowi *contoso\\mhanson* do łączenia się z komputerem *srv2* i użyj sesji programu Windows PowerShell konfigurację o nazwie *testu*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>PRZYKŁAD 2

Ten testy przykład dotyczą wszystkich reguł autoryzacji, aby sprawdzić, jakie reguły autoryzacji użytkownika *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Tematy pokrewne

- [Polecenia Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Polecenia cmdlet Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
