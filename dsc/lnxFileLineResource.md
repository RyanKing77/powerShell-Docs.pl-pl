---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxFileLine
ms.openlocfilehash: f2a989dd3a6746948e09ba94e279c02be8ebe2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893301"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC dla systemu Linux zasób nxFileLine

**NxFileLine** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm do zarządzania wierszy w pliku konfiguracji w węźle systemu Linux.

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
| Ścieżka pliku| Pełna ścieżka do pliku, aby zarządzać linie w docelowym węźle.|
| ContainsLine| Aby upewnić się, istnieje wiersz w pliku. Ten wiersz zostaną dołączone do pliku, jeśli nie istnieje w pliku. **ContainsLine** jest wymagane, ale można ustawić na ciąg pusty (`ContainsLine = ""`) Jeśli nie jest wymagana.|
| DoesNotContainPattern| Wzorzec wyrażenia regularnego dla wierszy, które nie powinny istnieć w pliku. Dla wszystkich wierszy, które istnieją w pliku, które pasują do tego wyrażenia regularnego wiersz zostaną usunięte z pliku.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

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