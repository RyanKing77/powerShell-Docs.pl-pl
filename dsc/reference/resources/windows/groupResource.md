---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC grupy
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077351"
---
# <a name="dsc-group-resource"></a>Zasób DSC grupy

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Zasób grupy w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.

## <a name="syntax"></a>Składnia

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| GroupName| Nazwa grupy, dla którego chcesz zapewnić określonego stanu.|
| Poświadczenie| Poświadczenia wymagane do dostępu do zasobów zdalnych. **Uwaga**: To konto musi mieć odpowiednie uprawnienia usługi Active Directory, aby dodać wszystkie konta innego niż lokalne grupy; w przeciwnym razie wystąpi błąd, gdy konfiguracja jest wykonywana w docelowym węźle.
| Opis| Opis grupy.|
| Upewnij się| Wskazuje, czy grupa istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że grupa nie istnieje. Ustawienie "Przedstawia" (wartość domyślna) gwarantuje, czy grupa istnieje.|
| Elementy członkowskie| Użyj tej właściwości, aby zamienić bieżącego członkostwa w grupie z tymi elementami. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| MembersToExclude| Ta właściwość służy do usuwania członków z istniejących członkostwa w grupie. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| MembersToInclude| Aby dodać członków do istniejących członkostwa w grupie, należy używać tej właściwości. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".|

## <a name="example-1"></a>Przykład 1

Poniższy przykład przedstawia sposób upewnij się, że grupa o nazwie "Grupatestowa" nieobecny.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Przykład 2

Poniższy przykład pokazuje, jak dodać użytkowników usługi Active Directory do lokalnej grupy administratorów, jako część kompilacji laboratorium wielu maszyn, których już używasz obiektu PSCredential dla konta administratora lokalnego.
Ponieważ jest on również używany dla konta administratora domeny (po promocji domeny), następnie należy przekonwertować tej PSCredential istniejących poświadczeń domeny przyjazna.
Następnie możemy dodać użytkownika domeny do lokalnej grupy administratorów na serwerze członkowskim.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Przykład 3

Poniższy przykład pokazuje, jak upewnić się, to grupa lokalna TigerTeamAdmins, na serwerze TigerTeamSource.Contoso.Com nie zawiera konta domeny określonego Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSource {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```