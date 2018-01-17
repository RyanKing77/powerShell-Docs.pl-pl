---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxService zasobów"
ms.openlocfilehash: 4273ad59f15eedd08b07888ebb6ee51d039b72b3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC dla systemu Linux nxService zasobów

**NxService** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości
|  Właściwość |  Opis | 
|---|---|
| Nazwa| Nazwa usługi/demona do skonfigurowania.| 
| Kontrolera| Typ kontrolera usługi do użycia podczas konfigurowania usługi.| 
| Włącz| Wskazuje, czy usługa jest uruchamiana podczas rozruchu.| 
| Stan| Wskazuje, czy usługa jest uruchomiona. Ustaw tę właściwość na "Zatrzymane", aby upewnić się, że usługa nie jest uruchomiona. Ustaw ją na "Uruchomiona", aby upewnić się, że usługa nie jest uruchomiona.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Dodatkowe informacje

**NxService** zasobów nie utworzy definicji usługi lub skryptu usługi, gdy nie istnieje. Można użyć konfiguracji żądanego stanu środowiska PowerShell **nxFile** zasób zasobów do zarządzania istnienie lub zawartość skryptu lub pliku definicji usługi.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono konfigurację usługi "host z wieloma adresami" (dla Apache HTTP Server), zarejestrowany **SystemD** kontrolera usług.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

