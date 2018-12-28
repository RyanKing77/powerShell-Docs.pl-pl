---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404981"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell

"Drugi problem przeskoku" odwołuje się do sytuacji, jak pokazano poniżej:

1. Użytkownik jest zalogowany do _Serwer_a_.
2. Z _Serwer_a_, rozpocząć zdalną sesję programu PowerShell, aby nawiązać połączenie _ServerB_.
3. Polecenie uruchamiane na _ServerB_ za pośrednictwem usługi komunikacji zdalnej programu PowerShell sesji próbuje uzyskać dostęp do zasobu na _ServerC_.
4. Dostęp do zasobu na _ServerC_ odmowa, ponieważ poświadczenia użyte do utworzenia sesji komunikacji zdalnej programu PowerShell nie są przekazywane z _ServerB_ do _ServerC_.

Istnieje kilka sposobów, aby rozwiązać ten problem. W tym temacie omówimy kilka najbardziej popularne rozwiązania do drugiego przeskoku problemu.

## <a name="credssp"></a>Protokół CredSSP

Możesz użyć [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) do uwierzytelniania. Protokół CredSSP buforuje poświadczeń na serwerze zdalnym (_ServerB_), więc za jego pomocą zostanie otwarty do ataków z kradzieżą poświadczeń. Jeśli komputer zdalny zostanie naruszony, osoba atakująca ma dostęp do poświadczeń użytkownika. Protokół CredSSP jest domyślnie wyłączona, na komputerach klienta i serwera. Tylko w środowiskach najbardziej zaufaną, należy włączyć uwierzytelnianie CredSSP. Na przykład administrator domeny połączeniem z kontrolerem domeny, ponieważ kontroler domeny jest wysoce zaufanym.

Aby uzyskać więcej informacji na temat obawy związane z bezpieczeństwem w przypadku używania protokołu CredSSP dla komunikacji zdalnej programu PowerShell, zobacz [przypadkowym sabotażu: Uwaga, protokół CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Aby uzyskać więcej informacji dotyczących ataków z kradzieżą poświadczeń, zobacz [ataków Mitigating Pass--Hash (PtH) i inne kradzieży poświadczeń](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Na przykład sposobu włączania i protokół CredSSP na użytek komunikacji zdalnej programu PowerShell, zobacz [za pomocą protokołu CredSSP, aby rozwiązać problem drugiego przeskoku](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Zalety

- Działa na wszystkich serwerach z systemem Windows Server 2008 lub nowszym.

### <a name="cons"></a>Wady

- Ma luki w zabezpieczeniach.
- Wymaga konfiguracji klienta i serwera ról.

## <a name="kerberos-delegation-unconstrained"></a>Delegowanie protokołu Kerberos (nieograniczonego)

Delegowanie protokołu Kerberos, nieograniczone mogą być również używane się drugiego przeskoku. Jednak ta metoda zapewnia nie kontroli nad którym delegowane poświadczenia są używane.

>**Uwaga:** Konta usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Wymaga bez kodowania.

### <a name="cons"></a>Wady

- Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.
- Zapewnia kontrolę której są używane poświadczenia, tworząc luki w zabezpieczeniach.

## <a name="kerberos-constrained-delegation"></a>Ograniczone delegowanie protokołu Kerberos

Zapewnienie drugiego przeskoku, można użyć starszego ograniczonego delegowania (nie opartego na zasobach).

>**Uwaga:** Konta usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Wymaga bez kodowania

### <a name="cons"></a>Wady

- Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.
- Musi być skonfigurowany w obiekcie Active Directory serwera zdalnego (_ServerB_).
- Ograniczone do jednej domeny. Nie może przekraczać domen i lasów.
- Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Oparte na zasobach ograniczonego delegowania protokołu Kerberos

Przy użyciu protokołu Kerberos z opartego na zasobach ograniczonego delegowania (wprowadzona w systemie Windows Server 2012), skonfigurować delegowanie poświadczeń na obiekt serwera, gdzie znajdują się zasoby.
W drugim scenariuszu przeskoku opisanych powyżej, można skonfigurować _ServerC_ do określenia, z której będzie akceptować delegowane poświadczenia.

>**Uwaga:** Konta usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane. Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Zalety

- Poświadczenia nie są przechowywane.
- Stosunkowo łatwa do skonfigurowania za pomocą poleceń cmdlet programu PowerShell — nie specjalne jest wymagane tworzenie kodu.
- Brak dostępu specjalnego domeny jest wymagana.
- Działa na różnych domen i lasów.
- Kod programu PowerShell.

### <a name="cons"></a>Wady

- Wymaga systemu Windows Server 2012 lub nowszy.
- Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.
- Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).

### <a name="example"></a>Przykład

Przyjrzyjmy się programu PowerShell, na przykład, który umożliwia skonfigurowanie zasobów na podstawie ograniczonego delegowania _ServerC_ umożliwia delegowane poświadczenia z _ServerB_.
W tym przykładzie założono, że wszystkie serwery działają Windows Server 2012 lub nowszy, i że istnieje co najmniej jeden kontroler domeny systemu Windows Server 2012 każdej domeny, które dowolnego z serwerów należą.

Aby można było skonfigurować delegowanie ograniczone, należy dodać `RSAT-AD-PowerShell` funkcji do zainstalowania modułu środowiska PowerShell usługi Active Directory, a następnie zaimportuj ten moduł do sesji:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Teraz masz kilka dostępnych poleceń cmdlet **PrincipalsAllowedToDelegateToAccount** parametru:

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

**PrincipalsAllowedToDelegateToAccount** parametr ustawia atrybut obiektu usługi Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, który zawiera listy kontroli dostępu (ACL), Określa, które konta mają uprawnienia do delegowania poświadczeń do skojarzonego konta (w naszym przykładzie będzie konto komputera dla _serwera_).

Teraz Skonfigurujmy zmienne będą używane do reprezentowania serwerów:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

Usługa WinRM (i w związku z tym komunikacji zdalnej programu PowerShell) jest domyślnie uruchamiany jako konto komputera. Można to zobaczyć, analizując **StartName** właściwość `winrm` usługi:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Dla _ServerC_ aby umożliwić delegowanie sesji komunikacji zdalnej programu PowerShell na _ServerB_, firma Microsoft spowoduje przyznanie dostępu przez ustawienie **PrincipalsAllowedToDelegateToAccount** Parametr _ServerC_ do obiektu komputera _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [Centrum dystrybucji kluczy (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) pamięci podręcznych odmowa prób dostępu (negatywna pamięć podręczna) przez 15 minut. Jeśli _ServerB_ wcześniej próbowało uzyskać dostęp do _ServerC_, należy wyczyścić pamięć podręczną na _ServerB_ za pomocą następującego polecenia:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Można również ponowne uruchomienie komputera lub poczekaj co najmniej 15 minut, aby wyczyścić pamięć podręczną.

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

W tym przykładzie `$using` zmienna jest używane do obliczania `$ServerC` widoczne dla zmiennej _ServerB_. Aby uzyskać więcej informacji na temat `$using` zmiennych, zobacz [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Aby zezwolić na wiele serwerów delegować poświadczenia, aby _ServerC_, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru _ServerC_ do tablicy:

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

Jeśli chcesz utworzyć drugiego przeskoku w domenach, Dodaj w pełni kwalifikowana nazwa domeny (FQDN) kontrolera domeny, domeny, do którego _ServerB_ należy:

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

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informacji na temat opartego na zasobach ograniczonego delegowania protokołu Kerberos

- [What's New in uwierzytelnianie Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [W jaki sposób system Windows Server 2012 ułatwia ból Kerberos ograniczone delegowanie, część 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Jak system Windows Server 2012 ułatwia ból Kerberos ograniczone delegowanie, część 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Opis protokołu Kerberos ograniczone delegowanie dla wdrożenia serwera Proxy aplikacji usługi Azure Active Directory przy użyciu uwierzytelniania zintegrowanego Windows](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory schematu atrybutów M2.210 atrybutu msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Rozszerzenia protokołu Kerberos: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Zasób na podstawie protokołu Kerberos ograniczone delegowanie](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administracja zdalna bez ograniczone delegowanie przy użyciu PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration przy użyciu funkcji RunAs

Można utworzyć konfiguracji sesji na _ServerB_ i ustaw jego **RunAsCredential** parametru.

Aby dowiedzieć się, jak przy użyciu PSSessionConfiguration i Uruchom jako, aby rozwiązać drugi problem przeskoków, zobacz [kolejnego rozwiązania do komunikacji zdalnej programu PowerShell z wieloma przeskokami](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Zalety

- Działa z każdym serwerem przy użyciu programu WMF 3.0 lub nowszej.

### <a name="cons"></a>Wady

- Wymaga konfiguracji **PSSessionConfiguration** i **RunAs** na każdym serwerze pośredni (_ServerB_).
- Wymaga obsługi haseł, podczas korzystania z domeny **RunAs** konta

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA pozwala ograniczyć jakie polecenia, które administrator może być uruchomiony w sesji programu PowerShell. Może służyć do problemu drugiego przeskoku.

Aby uzyskać informacji na temat technologii JEA, zobacz [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Zalety

- Nie obsługi haseł podczas korzystania z wirtualnego konta.

### <a name="cons"></a>Wady

- Wymaga programu WMF 5.0 lub nowszy.
- Wymaga konfiguracji na każdym serwerze pośredni (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Przekazywania poświadczeń wewnątrz bloku skryptu Invoke-Command

Można przekazać poświadczenia wewnątrz **ScriptBlock** parametr wywołania [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) polecenia cmdlet.

### <a name="pros"></a>Zalety

- Nie wymaga specjalnego serwera konfiguracji.
- Działa na każdym serwerze z programem WMF 2.0 lub nowszej.

### <a name="cons"></a>Wady

- Wymaga technikę niewygodna kodu.
- Jeśli z programem WMF 2.0, wymaga innej składni dotyczących przekazywania argumentów do sesji zdalnej.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób przekazywania poświadczeń w **Invoke-Command** blok skryptu:

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