---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxSshAuthorizedKeys zasobów
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC dla systemu Linux nxSshAuthorizedKeys zasobów

**NxAuthorizedKeys** zasobów w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania autoryzowany ssh kluczy dla określonego użytkownika.

## <a name="syntax"></a>Składnia

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| KeyComment| Komentarz Unikatowy klucz. To jest używany do jednoznacznego identyfikowania kluczy.|
| Upewnij się| Określa, czy klucz jest zdefiniowany. Ustaw tę właściwość na "Brak", aby upewnić się, że klucz nie istnieje w pliku kluczy autoryzowanego użytkownika. Ustaw ją na "Brak", aby upewnić się, że klucz jest zdefiniowana w pliku klucza autoryzowanego użytkownika.|
| Nazwa użytkownika| Nazwa użytkownika do zarządzania ssh uprawnień klucze. Jeśli nie jest zdefiniowany, użytkownik domyślną jest "root".|
| Klawisz| Zawartość klucza. Jest to wymagane, jeśli **upewnij się, że** ma ustawioną wartość "Brak".|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano autoryzowany ssh publicznego klucza dla użytkownika "monuser".

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```