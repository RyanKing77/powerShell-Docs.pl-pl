---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
description: Udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.
title: Zasób GroupSet DSC
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a>Zasób GroupSet DSC

> Dotyczy: Windows środowiska Windows PowerShell 5.0

**GroupSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w docelowym węźle. Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołującym [grupy zasobów](groupResource.md) dla każdej grupy określonej w `GroupName` parametru.

Jeśli chcesz dodać i/lub Usuń tę samą listę elementów członkowskich do więcej niż jednej grupy, Usuń więcej niż jedną grupę lub Dodaj więcej niż jednej grupy z tej samej listy elementów członkowskich, należy użyć tego zasobu.

##<a name="syntax"></a>Składnia ##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa grupy| Nazwy grup, dla których chcesz zapewnić z określonym stanem.|
| MembersToExclude| Ta właściwość umożliwia usunięcie członków z istniejącego członkostwa w grupach. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości. W ten sposób spowoduje wystąpienie błędu.|
| Poświadczenie| Poświadczenia wymagane do dostępu do zasobów zdalnego. **Uwaga**: to konto musi mieć odpowiednich uprawnień usługi Active Directory, aby dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd.
| Upewnij się| Wskazuje, czy istnieją grupy. Ustaw tę właściwość na "Brak", aby upewnić się, że grupy nie istnieją. Ustawienie jej "Przedstawienie" (wartość domyślna) zapewnia, że istnieją grupy.|
| Elementy członkowskie| Ta właściwość służy do Zamień od bieżącego członkostwa grupy określone elementy członkowskie. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości. W ten sposób spowoduje wystąpienie błędu.|
| MembersToInclude| Ta właściwość służy do dodawania członków do istniejącego członkostwa grupy. Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości. W ten sposób spowoduje wystąpienie błędu.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".|

## <a name="example-1"></a>Przykład 1

Poniższy przykład przedstawia sposób upewnić się, że istnieją dwie grupy o nazwie "mojaGrupa" i "myOtherGroup".

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**Uwaga:** w tym przykładzie używane poświadczenia w postaci zwykłego tekstu, dla uproszczenia. Aby uzyskać informacje dotyczące do szyfrowania poświadczeń w pliku MOF konfiguracji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).