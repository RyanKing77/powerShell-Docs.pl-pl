---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Co drugi przeskok w komunikacji zdalnej programu PowerShell
ms.openlocfilehash: 1d24473178bc50321a81ebf1115a20f17078844f
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Co drugi przeskok w komunikacji zdalnej programu PowerShell

"Drugi problem przeskoku" odwołuje się do sytuacji podobne do poniższych:

1. Użytkownik jest zalogowany do _Serwer_a_.
2. Z _Serwer_a_, Uruchom sesję zdalną programu PowerShell do nawiązania połączenia _ServerB_.
3. Polecenie jest uruchamiane na _ServerB_ za pośrednictwem komunikacji zdalnej programu PowerShell sesji podejmie próbę uzyskania dostępu do zasobu na _ServerC_.
4. Dostęp do zasobu na _ServerC_ odmowa, ponieważ poświadczenia użyte do utworzenia sesji komunikacji zdalnej programu PowerShell nie są przekazywane z _ServerB_ do _ServerC_.

Istnieje kilka sposobów, aby rozwiązać ten problem. W tym temacie wyjaśniono, kilka najbardziej popularnych rozwiązań problemu drugiego przeskoku.

## <a name="credssp"></a>Protokół CredSSP

Można użyć [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) do uwierzytelniania. CredSSP buforuje poświadczeń na serwerze zdalnym (_ServerB_), aby za jej pomocą otwiera do ataków kradzieży poświadczeń. W przypadku naruszenia zabezpieczeń komputera zdalnego atakujący ma dostęp do poświadczeń użytkownika. Domyślnie na komputerach klienta i serwera jest wyłączone uwierzytelnianie CredSSP. Tylko w środowiskach najbardziej zaufany, należy włączyć uwierzytelnianie CredSSP. Na przykład administrator domeny połączeniem z kontrolerem domeny, ponieważ kontroler domeny jest wysoce zaufanych.

Aby uzyskać więcej informacji na temat problemy z zabezpieczeniami w przypadku używania protokołu CredSSP dla komunikacji zdalnej programu PowerShell, zobacz [przypadkowemu sabotażu: należy wziąć pod CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Aby uzyskać więcej informacji dotyczących ataków kradzieży poświadczeń, zobacz [ataków Podręcznik Mitigating Pass--Hash (PtH) i inne kradzieży poświadczeń](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Na przykład sposobu włączania i użyć protokołu CredSSP do komunikacji zdalnej programu PowerShell, zobacz [przy użyciu protokołu CredSSP, aby rozwiązać problem drugiego przeskoku](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Zalety

- Działa dla wszystkich serwerów z systemem Windows Server 2008 lub nowszym.

### <a name="cons"></a>Wady

- Ma luki w zabezpieczeniach.
- Wymaga konfiguracji ról klienta i serwera.

## <a name="kerberos-delegation-unconstrained"></a>Delegowanie protokołu Kerberos (nieograniczonego)

Delegowanie protokołu Kerberos nieograniczonego można również używać do utworzyć drugi przeskok. Jednak ta metoda sterowanie nie jest dostępne, z którym delegowane poświadczenia są używane.

>**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Wymaga nie kodowania.

### <a name="cons"></a>Wady

- Nie obsługuje drugi przeskok usługi WinRM.
- Umożliwia sterowanie gdy używane są poświadczenia, tworząc luki w zabezpieczeniach.

## <a name="kerberos-constrained-delegation"></a>Ograniczone delegowanie protokołu Kerberos

Starsze ograniczonego delegowania (nie opartych na zasobach) umożliwia utworzyć drugi przeskok.

>**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Wymaga nie kodowania

### <a name="cons"></a>Wady

- Nie obsługuje drugi przeskok usługi WinRM.
- Musi być skonfigurowany w obiekcie Active Directory serwera zdalnego (_ServerB_).
- Ograniczone do jednej domeny. Nie można dla wielu domen i lasów.
- Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Oparte na zasobach ograniczonego delegowania protokołu Kerberos

Przy użyciu Kerberos oparte na zasobach ograniczonego delegowania (wprowadzona w systemie Windows Server 2012), należy skonfigurować delegowanie poświadczeń na obiekt serwera, gdzie znajdują się zasoby.
W drugi przeskok opisane powyżej, należy skonfigurować _ServerC_ Aby określić, z której będzie akceptować delegowane poświadczenia.

>**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Poświadczenia nie są przechowywane.
- Stosunkowo łatwa do skonfigurowania za pomocą poleceń cmdlet programu PowerShell — nie kodowania specjalne wymagane.
- Brak dostępu specjalnego domeny jest wymagany.
- Sprawdza się w domenach i lasach.
- Kod programu PowerShell.

### <a name="cons"></a>Wady

- Wymaga systemu Windows Server 2012 lub nowszym.
- Nie obsługuje drugi przeskok usługi WinRM.
- Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).

### <a name="example"></a>Przykład

Przyjrzyjmy się PowerShell, na przykład, który konfiguruje zasobów na podstawie delegowania ograniczonego _ServerC_ umożliwia delegowane poświadczenia z _ServerB_.
W tym przykładzie założono, że wszystkie serwery działają systemu Windows Server 2012 lub nowszym, i że istnieje co najmniej jeden kontroler domeny systemu Windows Server 2012 każdej domeny, do których serwerów należą.

Aby można było skonfigurować delegowanie ograniczone, należy dodać `RSAT-AD-PowerShell` funkcji do zainstalowania modułu środowiska PowerShell usługi Active Directory, a następnie zaimportuj ten moduł do sesji:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Kilka poleceń cmdlet dostępnych już **PrincipalsAllowedToDelegateToAccount** parametru:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** parametr ustawia atrybut obiektu usługi Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, który zawiera listy kontroli dostępu (ACL) który Określa konta, które ma uprawnienia do delegowania poświadczeń do skojarzonego konta (w tym przykładzie będzie konto komputera dla _serwera_).

Teraz Skonfigurujmy zmienne będą używane do reprezentowania serwerów:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

Usługa WinRM (i w związku z tym obsługę zdalną środowiska PowerShell) domyślnie działa jako konto komputera. Zobacz ten analizując **StartName** właściwość `winrm` usługi:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Aby uzyskać _ServerC_ aby umożliwić delegowanie w sesji komunikacji zdalnej programu PowerShell na _ServerB_, firma Microsoft będzie zezwalał na dostęp przez ustawienie **PrincipalsAllowedToDelegateToAccount** Parametr _ServerC_ do obiektu komputera z _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [Centrum dystrybucji kluczy (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) pamięci podręcznych odmowa prób dostępu (negatywną pamięć podręczną) przez 15 minut. Jeśli _ServerB_ wcześniej próbowało uzyskać dostęp do _ServerC_, należy wyczyścić pamięć podręczną na _ServerB_ za pomocą następującego polecenia:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Można także ponownie uruchom komputer lub zaczekaj co najmniej 15 minut, aby wyczyścić pamięć podręczną.

Po wyczyszczeniu pamięci podręcznej, można pomyślnie uruchomić kod z _Serwer_a_ za pośrednictwem _ServerB_ do _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

W tym przykładzie `$using` zmiennej jest używane do obliczania `$ServerC` widoczne dla zmiennej _ServerB_. Aby uzyskać więcej informacji na temat `$using` zmiennych, zobacz [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Aby umożliwić delegowanie poświadczeń w celu na wielu serwerach _ServerC_, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru na _ServerC_ do tablicy:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Jeśli chcesz utworzyć drugi przeskok między domenami, Dodaj pełni kwalifikowaną nazwę domeny (FQDN) z kontrolerem domeny w domenie do której _ServerB_ należy:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Aby usunąć możliwość delegowania poświadczeń do ServerC, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru _ServerC_ do `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informacje o oparte na zasobach ograniczonego delegowania protokołu Kerberos

- [Nowości w uwierzytelnianiu Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [Jak Windows Server 2012 ułatwia słabe z protokołu Kerberos ograniczonego delegowania, część 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Jak Windows Server 2012 ułatwia słabe z protokołu Kerberos ograniczonego delegowania, część 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Opis protokołu Kerberos ograniczonego delegowania dla wdrożenia serwera Proxy aplikacji usługi Azure Active Directory przy użyciu zintegrowanego uwierzytelniania systemu Windows](http://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory schematu atrybutów M2.210 atrybutu msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: rozszerzenia protokołu Kerberos: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Zasobów na podstawie protokołu Kerberos ograniczonego delegowania](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administracja zdalna bez delegowania ograniczonego przy użyciu PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration przy użyciu funkcji RunAs

Możesz utworzyć konfigurację sesji na _ServerB_ i ustawić jej **RunAsCredential** parametru.

Aby dowiedzieć się, jak za pomocą PSSessionConfiguration i RunAs rozwiązać drugi przeskok, zobacz [innego rozwiązania do komunikacji zdalnej programu PowerShell z wieloma przeskokami](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Zalety

- Działa z dowolnym serwerem z WMF 3.0 lub nowszej.

### <a name="cons"></a>Wady

- Wymaga konfiguracji **PSSessionConfiguration** i **RunAs** na każdym serwerze pośredniego (_ServerB_).
- Wymaga obsługi haseł, korzystając z domeny **RunAs** konta

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA pozwala ograniczyć poleceń, jakie administrator można uruchomić sesji programu PowerShell. Można go rozwiązać drugi przeskok.

Aby uzyskać informacje o JEA, zobacz [tylko tyle administracji](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Zalety

- Nie obsługi hasła korzystając z konta wirtualnego.

### <a name="cons"></a>Wady

- Wymaga WMF 5.0 lub nowszej.
- Wymaga konfiguracji na każdym serwerze pośredniego (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Przekazywanie poświadczeń wewnątrz bloku skryptu Invoke-Command

Można przekazać poświadczenia wewnątrz **ScriptBlock** parametru wywołania [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) polecenia cmdlet.

### <a name="pros"></a>Zalety

- Nie wymaga specjalnego serwera konfiguracji.
- Działa na każdym serwerze z programem WMF 2.0 lub nowszej.

### <a name="cons"></a>Wady

- Wymaga technikę nieodpowiednich kodu.
- Jeśli uruchomiona WMF 2.0, wymaga innej składni przekazywanie argumentów do sesji zdalnej.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób przekazywania poświadczeń w **Invoke-Command** bloku skryptu:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Zobacz też

[Zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](WinRMSecurity.md)