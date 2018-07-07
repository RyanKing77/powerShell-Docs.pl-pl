---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
description: Udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.
title: Zasób Groupset DSC
ms.openlocfilehash: 487a76ca7703b2c57b940b4c5bd176eada6c8019
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892430"
---
# <a name="dsc-groupset-resource"></a>Zasób Groupset DSC

> Dotyczy: Windows Windows PowerShell 5.0

**GroupSet** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle. Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołująca [grupy zasobów](groupResource.md) dla każdej grupy określony w `GroupName` parametru.

Korzystając z tego zasobu, jeśli chcesz dodać i/lub usunięcia tej samej listy elementów członkowskich do więcej niż jednej grupy, usunąć więcej niż jednej grupy lub Dodaj więcej niż jednej grupy o tej samej listy elementów członkowskich.

## <a name="syntax"></a>Składnia

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
| Nazwa grupy| Nazwy grup, dla których chcesz mieć pewność określonego stanu.|
| MembersToExclude| Ta właściwość służy do usuwania członków z istniejących członkostwa w grupach. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| Poświadczenie| Poświadczenia wymagane do dostępu do zasobów zdalnych. **Uwaga**: to konto musi mieć odpowiednie uprawnienia usługi Active Directory można dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd.
| Upewnij się| Wskazuje, czy istnieją grupy. Ustaw tę właściwość na "Brak", aby upewnić się, że nie istnieją grupy. Ustawienie "Przedstawia" (wartość domyślna) gwarantuje, że istnieją grupy.|
| Elementy członkowskie| Użyj tej właściwości, aby zamienić bieżącego członkostwa w grupie z tymi elementami. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| MembersToInclude| Aby dodać członków do istniejących członkostwa w grupie, należy używać tej właściwości. Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*. Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości. Ten sposób spowoduje wygenerowanie błędu.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".|

## <a name="example-1-ensuring-groups-are-present"></a>Przykład 1: Zapewnianie grupy są obecne

Poniższy przykład pokazuje, jak upewnić się, że istnieją dwie grupy o nazwie "mojaGrupa" i "myOtherGroup".

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

> [!NOTE] 
> W tym przykładzie przy użyciu poświadczeń w postaci zwykłego tekstu dla uproszczenia. Aby uzyskać informacje o tym, jak można zaszyfrować poświadczenia w pliku MOF konfiguracji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).
