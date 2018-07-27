---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxService
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267783"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC dla systemu Linux zasób nxService

**NxService** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania usługami w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Właściwości

| Właściwość | Opis |
|---|---|
| Nazwa| Nazwa usługi/demona do skonfigurowania.|
| Kontroler| Typ kontrolera usługi do użycia podczas konfigurowania usługi.|
| Włącz| Wskazuje, czy usługa jest uruchamiana podczas rozruchu.|
| Stan| Wskazuje, czy usługa jest uruchomiona. Ustaw wartość "Stopped", aby upewnić się, że usługa nie jest uruchomiony. Ustaw ją na "Uruchomiona", aby upewnić się, że usługa nie jest uruchomiony.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Dodatkowe informacje

**NxService** zasobu nie utworzy definicji usługi lub skryptu dla usługi, gdy nie istnieje. Możesz użyć programu PowerShell Desired State Configuration **nxFile** zasobów zasobów do zarządzania istnienie lub zawartości pliku definicji usługi lub skryptu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano konfigurację usługi "host z wieloma adresami" (w przypadku Apache HTTP Server), zarejestrowane w usłudze **SystemD** kontrolera usług.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```