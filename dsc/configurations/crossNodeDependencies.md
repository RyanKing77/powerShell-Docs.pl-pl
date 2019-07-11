---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Określanie zależności między węzłami
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734673"
---
# <a name="specifying-cross-node-dependencies"></a>Określanie zależności między węzłami

> Dotyczy: Windows PowerShell 5.0

DSC udostępnia specjalne zasoby **WaitForAll**, **WaitForAny**, i **WaitForSome** który może służyć w konfiguracji do określania zależności w konfiguracji na innych węzły. Zachowanie tych zasobów jest następująca:

- **WaitForAll**: Powiedzie się, jeśli określony zasób jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.
- **WaitForAny**: Powiedzie się, jeśli określony zasób jest w żądanym stanie na co najmniej jednym z węzłów docelowych określonych w **NodeName** właściwości.
- **WaitForSome**: Określa **NodeCount** właściwość oprócz **NodeName** właściwości. Zasób zakończy się pomyślnie, jeśli zasób jest w żądanym stanie na minimalna liczba węzłów (określony przez **NodeCount**) zdefiniowane przez **NodeName** właściwości.

## <a name="syntax"></a>Składnia

**WaitForAll** i **WaitForAny** zasoby udostępnionej w tej samej składni. Zastąp \<ResourceType\> w poniższym przykładzie z oboma **WaitForAny** lub **WaitForAll**.
Podobnie jak **DependsOn** — słowo kluczowe, konieczne będzie format nazwy, jako "ResourceName [ResourceType]". Jeśli zasób należy do osobnego [konfiguracji](configurations.md), obejmują **ConfigurationName** w sformatowanym ciągu "ResourceName [ResourceType]:: [ConfigurationName]:: [ConfigurationName]". **NodeName** jest komputer lub węzła, w którym powinien zaczekać na bieżącego zasobu.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

**WaitForSome** zasobu ma składnię podobny do powyższego przykładu, ale dodaje **NodeCount** klucza. **NodeCount** wskazuje, ilu węzłów bieżącego zasobu ma oczekiwać na.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Wszystkie **WaitForXXXX** udostępnianie następujące klucze składni.

|Właściwość|  Opis   |
|---------|---------------------|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalny to 1.|
| RetryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn do łączenia z jednocześnie. Wartość domyślna to `New-CimSession` domyślne.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Aby uzyskać więcej informacji, zobacz [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | Zobacz [DSC przy użyciu poświadczeń użytkownika](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>Korzystanie z zasobów WaitForXXXX

Każdy **WaitForXXXX** zasobów czeka, aż określone zasoby zakończyć w określonym węźle.
Inne zasoby w tej samej konfiguracji można następnie *zależą od* **WaitForXXXX** zasobów przy użyciu **DependsOn** klucza.

Na przykład w następującej konfiguracji węzła docelowego oczekuje na **xADDomain** zasobów, aby zdążyć na **Kontroler_domeny** węzły maksymalną liczbą 30 ponawia próbę, w 15-sekundowych odstępach czasu, zanim węzeł docelowy mogą dołączyć do domeny.

Domyślnie **WaitForXXX** zasobów spróbuj jeden raz, a następnie zakończyć się niepowodzeniem. Chociaż nie jest wymagane, będzie zazwyczaj chcesz określić **RetryCount** i **RetryIntervalSec**.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Podczas kompilowania konfiguracji są generowane dwa pliki "MOF". Dotyczy zarówno pliki "MOF" węzłów docelowych przy użyciu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet

> [!NOTE]
> **WaitForXXX** zasobów Użyj Windows Remote Management, aby sprawdzić stan innych węzłów.
> Aby uzyskać więcej informacji na temat wymagania dotyczące portów i zabezpieczeń dla usługi WinRM, zobacz [zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Zobacz też

- [Konfiguracje DSC](configurations.md)
- [Użyj zależności zasobów](resource-depends-on.md)
- [Zasoby DSC](../resources/resources.md)
- [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md)
