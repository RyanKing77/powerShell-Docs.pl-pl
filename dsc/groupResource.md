---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób grupy DSC"
ms.openlocfilehash: 8a2087455a72ec1f368f890b62228b31cf4ec95a
ms.sourcegitcommit: c72c76f6ed77b3e6f26fef3e8784b157bfc19355
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2018
---
# <a name="dsc-group-resource"></a>Zasób grupy DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Grupy zasobów w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w docelowym węźle.

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
| Nazwa grupy| Nazwa grupy, dla którego chcesz zapewnić z określonym stanem.|
| Poświadczenie| Poświadczenia wymagane do dostępu do zasobów zdalnego. **Uwaga**: to konto musi mieć odpowiednich uprawnień usługi Active Directory, aby dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd, gdy konfiguracja jest wykonywana w docelowym węźle.
| Opis| Opis grupy.|
| Upewnij się| Wskazuje, czy dana grupa istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że grupa nie istnieje. Ustawienie jej "Przedstawienie" (wartość domyślna) zapewnia, że grupa istnieje.|
| Elementy członkowskie| Ta właściwość służy do Zamień od bieżącego członkostwa grupy określone elementy członkowskie. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości. Dzięki temu generuje błąd.|
| MembersToExclude| Ta właściwość służy do usunięcia członków z istniejącego członkostwa grupy. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości. Dzięki temu generuje błąd.|
| MembersToInclude| Ta właściwość służy do dodawania członków do istniejącego członkostwa grupy. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości. W ten sposób spowoduje wystąpienie błędu.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".|

## <a name="example-1"></a>Przykład 1

Poniższy przykład przedstawia sposób upewnić się, że istnieje grupa o nazwie "TestGroup".

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

Poniższy przykład przedstawia sposób dodawania użytkownika usługi Active Directory do lokalnej grupy administratorów jako część kompilacji laboratorium wielu maszyny, której korzystasz już z PSCredential dla konta administratora lokalnego.
Jest to również używana do konta administratora domeny (po podwyższenie poziomu domeny), następnie należy przekonwertować tej PSCredential istniejących poświadczeń domeny przyjazną.
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

Poniższy przykład przedstawia sposób zapewnienia grupą lokalną, TigerTeamAdmins, na serwerze TigerTeamSource.Contoso.Com nie zawiera konta domeny określonego Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSrouce {
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
