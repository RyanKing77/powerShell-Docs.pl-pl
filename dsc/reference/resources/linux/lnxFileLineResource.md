---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC for Linux nxFileLine Resource
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077964"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC for Linux nxFileLine Resource

**NxFileLine** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania wierszy w pliku konfiguracji w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| FilePath| Pełna ścieżka do pliku, aby zarządzać linie w docelowym węźle.|
| ContainsLine| Aby upewnić się, istnieje wiersz w pliku. Ten wiersz zostaną dołączone do pliku, jeśli nie istnieje w pliku. **ContainsLine** jest wymagane, ale można ustawić na ciąg pusty (`ContainsLine = ""`) Jeśli nie jest wymagana.|
| DoesNotContainPattern| Wzorzec wyrażenia regularnego dla wierszy, które nie powinny istnieć w pliku. Dla wszystkich wierszy, które istnieją w pliku, które pasują do tego wyrażenia regularnego wiersz zostaną usunięte z pliku.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

Ten przykład demonstruje użycie **nxFileLine** zasobów, aby skonfigurować `/etc/sudoers` pliku, upewniając się, że użytkownik: requiretty nie skonfigurowano monuser.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```