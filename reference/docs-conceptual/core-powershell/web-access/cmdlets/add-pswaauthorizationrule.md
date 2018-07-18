---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094232"
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

**Add-PswaAuthorizationRule** polecenie cmdlet dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.

Należy określić użytkowników, komputerów i punkty końcowe programu Windows PowerShell, dla tej reguły. Można określić użytkowników i komputerów indywidualne konta użytkowników i nazwy komputerów lub za pomocą określania grup.

Na komputerze, który jest przyłączony do domeny usługi Active Directory polecenie cmdlet używa identyfikator zabezpieczeń (SID) komputera, aby utworzyć regułę.
Dzięki temu można używać krótką nazwę, w pełni kwalifikowaną nazwę domeny (FQDN) lub adres IP dla **nazwy komputera** pola na stronie logowania.

Na komputerze, który nie jest przyłączony do domeny usługi Active Directory polecenie cmdlet tworzy regułę przy użyciu nazwy komputera, dostarczone przez administratora. Do pomyślnego połączenia z tą maszyną, użytkownik końcowy należy podać nazwę komputera, dokładnie tak, jak wygląda na to, w regule.

W przypadku wielu komputerów w ramach tej samej nazwie w sieci krótką nazwę może prowadzić do więcej niż jednym komputerze. Może to prowadzić do niejednoznaczności podczas nawiązywania połączenia. Na przykład, jeśli istnieje reguła komputera grupy roboczej, o nazwie "*serwer1*" i nowy komputer o nazwie *server1.contoso.com* jest dołączony do sieci, zakończy się pomyślnie weryfikacji przy użyciu reguł autoryzacji i Windows PowerShell Web Access próbuje nawiązać połączenie z komputera o nazwie "*serwer1*". Nie ma żadnej gwarancji, połączenie jest nawiązywane z określonej grupy roboczej komputera; Nie można ustanowić w grupie roboczej lub na komputerze domeny o nazwie "*serwer1*". Aby ograniczyć niejednoznaczność, zalecane jest, użyj nazwy FQDN dla komputera docelowego, jeśli to możliwe utworzyć regułę autoryzacji.

Reguły autoryzacji oceny podstawowego poświadczenia logowania użytkowników programu Windows PowerShell Web Access, a nie poświadczeń alternatywnych (drugi zestaw poświadczeń znaleziony w **opcjonalne ustawienia połączenia** sekcji Strona logowania). Aby na przykład Zobacz przykład 6.

## <a name="parameters"></a>Parametry

### <a name="-computergroupname-string"></a>-ComputerGroupName \<ciągu\>

Określa nazwę grupy komputerów w Active Directory Domain Services (AD DS) lub grupy lokalne, do których ta reguła udziela dostępu.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-computername-string"></a>-ComputerName \<ciągu\>

Określa nazwę komputera, do której ta reguła udziela dostępu.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-configurationname-string"></a>ConfigurationName — \<ciągu\>

Określa nazwę konfiguracji sesji programu Windows PowerShell, nazywane również obszar działania, do której ta reguła udziela dostępu.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Określa **PSCredential** obiektu dla konta użytkownika, który chcesz użyć, aby zmienić reguły autoryzacji programu Windows PowerShell Web Access. Jeśli ten parametr nie zostanie dodany, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika. Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby dodać reguły autoryzacji zdalnie, uruchom [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) polecenia cmdlet.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-force"></a>-Force

Wymusza polecenia do uruchomienia bez monitowania o potwierdzenie przez użytkownika. \
Ponadto on również monituje o potwierdzenie po wprowadzeniu nazwy komputera prostej lub krótki (takie jak nazwa, która nie jest nazwą domeny lub nie jest w pełni kwalifikowana). Potwierdzenie jest wymagany ze względów bezpieczeństwa, dzięki czemu można użyć prostą nazwę, aby dodać komputer tylko wtedy, gdy komputer znajduje się w grupie roboczej.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | false                                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-rulename-string"></a>-RuleName \<ciągu\>

Określa przyjazną nazwę dla tej reguły.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | false                                |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<ciągu\[\]\>

Określa nazwę co najmniej jednej grupy użytkowników w usługach AD DS i grupy lokalne, do których ta reguła udziela dostępu.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | o nazwie                                |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByPropertyName)                |
| Akceptowanie symboli wieloznacznych?          | false                                |

### <a name="-username-string"></a>-UserName \<ciągu\[\]\>

Określa co najmniej jednego użytkownika, do których ta reguła udziela dostępu. Nazwa użytkownika może mieć konto użytkownika lokalnego na komputerze bramy lub użytkownika w usługach AD DS.
Format jest `domain\user` lub `computer\user`.

|||
|-|-|
| Aliasy                              | brak                                 |
| Wymagane?                            | true                                 |
| Pozycja?                            | 1                                    |
| Wartość domyślna                        | brak                                 |
| Akceptowanie danych wejściowych potoku?               | Wartość true (ByValue, ByPropertyName)       |
| Akceptowanie symboli wieloznacznych?          | false                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer oraz - OutVariable.
Aby uzyskać więcej informacji, zobacz [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>DANE WEJŚCIOWE

### <a name="string"></a>Ciąg

To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.

### <a name="string"></a>Ciąg\[\]

To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.

## <a name="outputs"></a>Dane wyjściowe

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

To polecenie cmdlet zwraca obiekt reguły autoryzacji.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1"></a>PRZYKŁAD 1

W tym przykładzie daje dostęp do konfiguracji sesji _Punktkoncowypswa_, ograniczonym obszarem działania, na _srv2_ dla użytkowników w _SMAdmins_ grupy.

> [!NOTE]
> Nazwa komputera musi być w pełni kwalifikowaną nazwę domeny (FQDN). Administratorzy zdefiniować konfigurację sesji z ograniczonym lub obszaru działania, czyli ograniczonym zakresem poleceń cmdlet i zadań, które użytkownicy końcowi mogą być uruchamiane. Definiowanie ograniczonym obszarem działania można uniemożliwić użytkownikom uzyskanie dostępu do innych komputerów, które są nie w obszarze dozwolone działania Windows PowerShell® związku z tym oferują bardziej bezpiecznego połączenia. Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) lub [instalacji i użyj Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>PRZYKŁAD 2

W tym przykładzie daje dostęp do domyślnej konfiguracji sesji programu Windows PowerShell, `Microsoft.PowerShell`na *srv2* dla użytkowników w użytkowników o nazwie `contoso\user1`, `contoso\user2`, i `contoso\user3`. To polecenie cmdlet tworzy trzy reguły (1 na osobę).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>PRZYKŁAD 3

W tym przykładzie pokazano, jak wprowadzanie wartości nazwy użytkownika przy użyciu potoku.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>PRZYKŁAD 4

Ten przykład ilustruje jak wszystkie parametry pobierają wartości z potoku, według nazwy właściwości.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>PRZYKŁAD 5

Ten przykład dodaje regułę zezwalającą na użytkownika lokalnego o nazwie `PswaServer\ChrisLocal` dostęp do serwera o nazwie **srv1.contoso.com**.

W tym przykładzie przedstawiono scenariusz, w którym brama znajduje się w grupie roboczej i komputer docelowy znajduje się w domenie. Reguła autoryzacji ma zastosowanie do użytkowników lokalnych skonfigurowanych na bramie. W witrynie programu Windows PowerShell Web Access logowania w celu pomyślnego uwierzytelnienia użytkownik musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru. Serwer bramy zastosuje ten dodatkowy zestaw poświadczeń do uwierzytelniania użytkownika na komputerze docelowym, a serwer o nazwie *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>PRZYKŁAD 6

Ten przykład umożliwia wszystkim użytkownikom dostęp do wszystkich punktów końcowych na wszystkich komputerach.
Wyłącza to zasadniczo reguły autoryzacji.

> [!NOTE]
> Korzystanie z `*` znak symbolu wieloznacznego nie jest zalecane w przypadku wdrożeń z istotnymi dla zabezpieczeń i tylko powinny być traktowane jako dla środowisk testowych lub używane we wdrożeniach, których bezpieczeństwo może zostać złagodzone.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Zobacz też

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Dodawanie elementu członkowskiego](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)