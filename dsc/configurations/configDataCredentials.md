---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Opcje poświadczeń w danych konfiguracji
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686376"
---
# <a name="credentials-options-in-configuration-data"></a>Opcje poświadczeń w danych konfiguracji

>Dotyczy: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Haseł w postaci zwykłego tekstu, a użytkownicy domeny

Konfiguracji DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczący haseł w postaci zwykłego tekstu.
Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.
Aby pominąć tych błędów i ostrzeżeń, użyj słowa kluczowe dane konfiguracji DSC:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Przechowywanie/przesyła niezaszyfrowane hasła w postaci zwykłego tekstu zwykle nie jest bezpieczne. Zaleca się zabezpieczenie poświadczeń przy użyciu techniki omówione w dalszej części tego tematu.
> Usługi Konfiguracja DSC automatyzacji Azure umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.
> Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń zasoby](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Obsługa poświadczeń w konfiguracji DSC

Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.
Jednak niektóre zasoby potrzebne poświadczenia, na przykład gdy `Package` zasobów, należy zainstalować oprogramowanie w ramach określonego konta użytkownika.

Używane wcześniej zasoby ustalony `Credential` nazwę właściwości, aby rozwiązać.
Automatyczne dodany WMF 5.0 `PsDscRunAsCredential` właściwości dla wszystkich zasobów.
Aby uzyskać informacje o korzystaniu z `PsDscRunAsCredential`, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).
Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzenia własnych właściwości dla poświadczenia.

> [!NOTE]
> Projekt niektórych zasobów są używają wielu poświadczeń z określonego powodu i mają one właściwości własne poświadczenia.

Aby odnaleźć dostępne poświadczeń właściwości w zasobie użyj jednej `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

W tym przykładzie użyto [grupy](../resources/resources.md) zasób z `PSDesiredStateConfiguration` wbudowany moduł zasobów usługi Konfiguracja DSC.
Możesz tworzyć grupy lokalne i dodać lub usunąć członków.
Akceptuje zarówno `Credential` właściwości i automatyczne `PsDscRunAsCredential` właściwości.
Jednak używa tylko zasób `Credential` właściwości.

Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Przykład: Zasób grupy właściwości poświadczeń

DSC jest uruchamiana `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.
Jeśli dodano element członkowski jest kontem lokalnym, niezbędne jest nie ma poświadczeń.
Jeśli `Group` zasobów dodaje konto domeny do lokalnej grupy, a następnie konieczne jest podanie poświadczeń.

Nie są dozwolone anonimowe zapytania do usługi Active Directory.
`Credential` Właściwość `Group` zasób jest konto domeny używane do zapytania usługi Active Directory.
W większości przypadków może to być konto użytkownika ogólnego, ponieważ domyślnie użytkownicy mogą *odczytu* większość obiektów w usłudze Active Directory.

## <a name="example-configuration"></a>Przykładowa konfiguracja

Poniższy przykład kodu wykorzystuje DSC do wypełniania grupy lokalnej z użytkownikiem domeny:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Ten kod generuje zarówno błędu i ostrzeżenia:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

W tym przykładzie występują dwa problemy:

1. Wystąpił błąd wyjaśniono, że haseł w postaci zwykłego tekstu nie są zalecane
2. Ostrzeżenia z informacją o tym przed przy użyciu poświadczeń domeny

Flagi **PSDSCAllowPlainTextPassword** i **PSDSCAllowDomainUser** pomija błąd i ostrzeżenie informujące użytkownika zagrożenia.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.
To łącze wyjaśniono, jak do szyfrowania haseł przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.
Aby uzyskać więcej informacji o certyfikatach i DSC [odczytać ten wpis](http://aka.ms/certs4dsc).

Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

**PSDSCAllowPlainTextPassword** Flaga wymaga, aby użytkownik potwierdzić ryzyka przechowywania haseł w postaci zwykłego tekstu w pliku MOF. W wygenerowanym pliku MOF nawet jeśli **PSCredential** obiekt zawierający **SecureString** użyto hasła nadal wyświetlane jako zwykły tekst. Jest to czas tylko poświadczenia są widoczne. Aby uzyskać dostęp do tego zapewnia pliku MOF każdy dostęp do konta administratora.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Poświadczenia przesyłanych i przechowywanych

- **PSDscAllowPlainTextPassword** Flaga umożliwia kompilacji pliki MOF zawierające hasła w postaci zwykłego tekstu.
  Doszło przechowywanie plików MOF zawierający haseł w postaci zwykłego tekstu.
- Dostarczenia pliku MOF do węzła w **Push** trybie WinRM szyfruje komunikacji chronić hasła zwykłego tekstu, chyba że zastąpić domyślną z **AllowUnencrypted** parametru.
  - MOF przy użyciu certyfikatu szyfrowania chroni plik MOF magazynowane przed zastosowano do węzła.
- W **ściągania** tryb, można skonfigurować systemu Windows server ściągnięcia do używania protokołu HTTPS do szyfrowania ruchu przy użyciu protokołu określonego w polu serwera Internet Information Server. Aby uzyskać więcej informacji, zobacz artykuły [konfigurowania klienta ściągania usługi Konfiguracja DSC](../pull-server/pullclient.md) i [pliki MOF zabezpieczanie z certyfikatami](../pull-server/secureMOF.md).
  - W [konfiguracji stanu usługi Automatyzacja Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) usługi ściągania ruchu są zawsze szyfrowane.
- W węźle pliki MOF są szyfrowane, gdy w programie PowerShell 5.0.
  - W programie PowerShell MOF 4.0 pliki są magazynowane niezaszyfrowane, chyba że są szyfrowane przy użyciu certyfikatu podczas naciśnięty, czy pobierane do węzła.

**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym z powodu znaczące zagrożenie bezpieczeństwa.**

## <a name="domain-credentials"></a>Poświadczenia domeny

Nadal uruchomiona ponownie skryptu konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, że, przy użyciu domeny konto dla poświadczeń nie jest zalecane.
Za pomocą konta lokalnego eliminuje ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.

**Korzystając z poświadczeń z usługi Konfiguracja DSC zasobów, preferowane jest kontem lokalnym za pośrednictwem konta domeny, jeśli to możliwe.**

W przypadku "\\"lub"\@" w `Username` właściwość credential, a następnie DSC będzie je traktować jako konto domeny.
Brak wyjątek dla "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

W konfiguracji DSC `Group` zasobów przykładzie przedstawionym powyżej zapytań domeny usługi Active Directory *wymaga* konta domeny.
W takim przypadku Dodaj `PSDscAllowDomainUser` właściwości `ConfigurationData` zablokować w następujący sposób:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów lub ostrzeżeń.
