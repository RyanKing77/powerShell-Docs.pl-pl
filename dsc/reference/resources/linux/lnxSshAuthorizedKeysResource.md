---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxSshAuthorizedKeys
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077708"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC dla systemu Linux zasób nxSshAuthorizedKeys

**NxAuthorizedKeys** zasobów w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania autoryzacji ssh klucze dla określonego użytkownika.

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
| KeyComment| Komentarz Unikatowy klucz. Służy do jednoznacznego identyfikowania kluczy.|
| Upewnij się| Określa, czy klucz jest zdefiniowana. Ustaw tę właściwość na "Brak", aby upewnić się, że klucz nie istnieje w pliku autoryzowanych kluczy użytkownika. Ustaw ją na "Obecny", aby upewnić się, że klucz jest zdefiniowana w pliku autoryzowanych kluczy użytkownika.|
| Nazwa użytkownika| Nazwa użytkownika do zarządzania ssh autoryzacji kluczy. Jeśli nie zdefiniowana, użytkownik domyślny jest "root".|
| Klucz| Zawartość klucza. Jest to wymagane, jeśli **upewnij się, że** jest ustawiona na "Istnieje".|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano publiczny autoryzacji ssh klucza dla użytkownika "monuser".

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