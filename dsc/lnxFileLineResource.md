---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxFileLine zasobów
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219637"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC dla systemu Linux nxFileLine zasobów

**NxFileLine** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania wierszy w pliku konfiguracji w węźle systemu Linux.

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
| Ścieżka pliku| Pełna ścieżka do pliku, aby zarządzać wierszy w docelowym węźle.|
| ContainsLine| Wiersz, aby upewnić się, istnieje w pliku. Ten wiersz zostanie dołączona do pliku, jeśli nie istnieje w pliku. **ContainsLine** jest wymagane, ale może być ustawiony na ciąg pusty ("ContainsLine =" "), jeśli nie jest wymagana.|
| DoesNotContainPattern| Wzorzec wyrażenia regularnego wierszy, które nie powinny istnieć w pliku. Dla wszystkich wierszy, które znajdują się w pliku pasuje do tego wyrażenia regularnego wiersz zostaną usunięte z pliku.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

W tym przykładzie pokazano, za pomocą **nxFileLine** zasobów, aby skonfigurować `/etc/sudoers` pliku, upewniając się, że użytkownik: requiretty nie skonfigurowano monuser.

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```