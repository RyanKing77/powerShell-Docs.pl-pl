---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190387"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.

## <a name="syntax"></a>Składnia

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>OPIS

**Add-PswaAuthorizationRule** polecenia cmdlet dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.

Należy określić użytkowników, komputerów i punkty końcowe programu Windows PowerShell dla tej reguły. Można określić użytkowników i komputerów indywidualne konta użytkowników i nazwy komputera lub za pośrednictwem grup.

Dla komputera, który jest przyłączony do domeny usługi Active Directory polecenie cmdlet używa identyfikator zabezpieczeń (SID) komputera, aby utworzyć regułę.
Dzięki temu można używać krótkiej nazwy, w pełni kwalifikowaną nazwą domeny (FQDN) lub adres IP **nazwy komputera** pola na stronie logowania.

Na komputerze, który nie jest przyłączony do domeny usługi Active Directory polecenie cmdlet tworzy regułę przy użyciu nazwy komputera dostarczonego przez administratora. Pomyślnie nawiązywać połączeń z tą maszyną, użytkownik końcowy Podaj nazwę komputera dokładnie w brzmieniu podanym w regule.

W przypadku wielu komputerów o takiej samej nazwie w sieci, krótką nazwę może prowadzić do więcej niż jednego komputera. Może to prowadzić do niejednoznaczności podczas nawiązywania połączenia. Na przykład, jeśli reguła istnieje na komputerze grupy roboczej o nazwie "*serwer1*" i nowy komputer o nazwie *server1.contoso.com* jest dołączony do sieci, powodzenia weryfikacji przy użyciu reguł autoryzacji i Windows PowerShell Web Access próbuje nawiązać połączenie z komputera o nazwie "*serwer1*". Nie gwarantuje, że połączenie jest nawiązywane z określonej grupy roboczej komputera; Próba może wprowadzone w grupie roboczej lub komputerów domeny o nazwie "*serwer1*". Aby zmniejszyć niejednoznaczności, zalecane jest, użyj nazwy FQDN dla komputera docelowego, jeśli to możliwe utworzyć regułę autoryzacji.

Reguły autoryzacji ocenić głównej poświadczenia logowania użytkowników programu Windows PowerShell Web Access, poświadczenia alternatywne (znaleziono drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** sekcji Strona logowania). Aby na przykład Zobacz przykład 6.

## <a name="parameters"></a>Parametry

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

Określa nazwę grupy komputerów usług domenowych w usłudze Active Directory (AD DS) lub grupy lokalne, na które ta reguła zezwala na dostęp.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;ciągu&gt;

Określa nazwę komputera, do którego ta reguła zezwala na dostęp.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;ciągu&gt;

Określa nazwę konfiguracji sesji programu Windows PowerShell, nazywane również obszaru działania, do którego ta reguła zezwala na dostęp.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz użyć, aby zmienić reguł autoryzacji programu Windows PowerShell Web Access. Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika. Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby dodać reguły autoryzacji zdalnie, uruchom [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) polecenia cmdlet.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-force"></a>-Force

Wymusza wykonanie polecenia bez monitowania o potwierdzenie przez użytkownika. \
Ponadto on również monituje o potwierdzenie po wprowadzeniu nazwy prostej lub krótkiej komputera (takie jak nazwa, która nie jest nazwą domeny lub nie jest w pełni kwalifikowana). Potwierdzenie żądania ze względów bezpieczeństwa, aby mogli używać prostą nazwą, aby dodać komputer tylko wtedy, gdy komputer znajduje się w grupie roboczej.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String&gt;

Określa przyjazną nazwę dla tej reguły.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;String\[\]&gt;

Określa nazwę jednego lub więcej grup użytkowników w usługach AD DS i grupy lokalne, na które ta reguła zezwala na dostęp.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;ciągu\[\]&gt;

Określa co najmniej jednego użytkownika, do których ta reguła zezwala na dostęp. Nazwa użytkownika może być kontem użytkownika lokalnego na komputerze z bramą lub użytkownika w usługach AD DS.
Format jest `domain\user` lub `computer\user`.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue, ByPropertyName)       |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;Parametry&gt;

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.
Aby uzyskać więcej informacji, zobacz [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>DANE WEJŚCIOWE

### <a name="string"></a>Ciąg

To polecenie cmdlet akceptuje ciągiem lub tablicą ciągów jako dane wejściowe.

### <a name="string"></a>Ciąg\[\]

To polecenie cmdlet akceptuje ciągiem lub tablicą ciągów jako dane wejściowe.

## <a name="outputs"></a>Dane wyjściowe

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

To polecenie cmdlet zwraca obiekt reguły autoryzacji.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie nieograniczony dostęp do konfiguracji sesji *Punktkoncowypswa*, ograniczonym obszarem działania, na *srv2* dla użytkowników w *SMAdmins* grupy. \
**Uwaga**: Nazwa komputera musi być w pełni kwalifikowaną nazwą domeny (FQDN). Administratorzy zdefiniować konfigurację sesji ograniczony lub obszaru działania, która jest ograniczonym zakresem poleceń cmdlet i zadań, które użytkownicy końcowi mogą uruchamiać. Zdefiniowanie ograniczonego obszaru działania może uniemożliwić użytkownikom dostęp do innych komputerów, które są nie w obszarze działania Windows PowerShell® dozwolone, a tym samym zapewnia bardziej bezpiecznego połączenia. Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) lub [instalacji i użyj Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>PRZYKŁAD 2

W tym przykładzie nieograniczony dostęp do domyślnej konfiguracji sesji środowiska Windows PowerShell, `Microsoft.PowerShell`na *srv2* dla użytkowników w użytkowników o nazwie contoso\\Użytkownik1, contoso\\Użytkownik2 i contoso\\UŻYTKOWNIK3. To polecenie cmdlet tworzy trzy reguły (1 na osobę).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>PRZYKŁAD 3

W tym przykładzie przedstawiono sposób wprowadzania wartości nazwy użytkownika za pośrednictwem potoku.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>PRZYKŁAD 4

W tym przykładzie przedstawiono sposób wszystkie parametry przyjmować wartości z potoku według nazwy właściwości.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>PRZYKŁAD 5

W tym przykładzie Dodaje regułę w celu zezwalania użytkownika lokalnego o nazwie *PswaServer\\ChrisLocal* dostęp do serwera o nazwie *srv1.contoso.com*.

W tym przykładzie przedstawiono scenariusz, w którym brama jest w grupie roboczej i komputer docelowy znajduje się w domenie. Reguła autoryzacji dotyczy użytkowników lokalnych w bramie. W witrynie Windows PowerShell Web Access logowania w celu pomyślnego uwierzytelnienia użytkownik musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru. Serwer bramy zastosuje ten dodatkowy zestaw poświadczeń do uwierzytelniania użytkownika na komputerze docelowym, a serwer o nazwie *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>PRZYKŁAD 6

Ten przykład zezwala wszystkim użytkownikom dostęp do wszystkich punktów końcowych na wszystkich komputerach.
To zasadniczo wyłączenie reguł autoryzacji. \
**Uwaga**: użycie `*` wieloznacznego nie jest zalecane w przypadku istotnych dla zabezpieczeń wdrożeń i tylko powinna być brana pod uwagę dla środowisk testowych lub używać w przypadku wdrożeń, w którym można rozluźnić zabezpieczeń.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Zobacz też

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Dodawanie elementu członkowskiego](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)