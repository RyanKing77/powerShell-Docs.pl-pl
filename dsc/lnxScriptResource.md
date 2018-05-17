---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxScript zasobów
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC dla systemu Linux nxScript zasobów

**NxScript** zasobów w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm na uruchamianie skryptów systemu Linux w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| GetScript| Udostępnia skryptu uruchamianego po wywołaniu [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet. Skrypt musi rozpoczynać się od shebang, takie jak #! / bin/bash.|
| SetScript| Zawiera skrypt. Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** jest uruchamiany pierwszy. Jeśli **TestScript** bloku zwraca kod zakończenia innego niż 0, **SetScript** bloku zostanie uruchomiony. Jeśli **TestScript** zwraca kod zakończenia 0, **SetScript** nie zostaną uruchomione. Skrypt musi rozpoczynać się od shebang, takich jak `#!/bin/bash`.|
| TestScript| Zawiera skrypt. Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, ten skrypt jest uruchamiany. Jeśli zwróci ona kod zakończenia innego niż 0, SetScript zostanie uruchomiony. Jeśli zwróci ona kod zakończenia 0, **SetScript** nie zostaną uruchomione. **TestScript** również uruchamiane przy wywołaniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet. Jednak w tym przypadku **SetScript** nie zostaną uruchomione, niezależnie od tego, jaki kod zakończenia jest zwracana z **TestScript**. **TestScript** musi zwracać kod zakończenia 0, jeśli rzeczywista konfiguracja pasuje bieżącej konfiguracji żądanego stanu, a wyjście kodu inne niż 0, jeśli nie jest zgodny. (W bieżącej konfiguracji żądanego stanu jest ostatniej konfiguracji wdrożonymi na węźle, który używa DSC). Skrypt musi rozpoczynać się od shebang, takich jak 1#!/bin/bash.1|
| Użytkownik| Użytkownik, który umożliwia uruchomienie skryptu jako.|
| Grupa| Grupa, aby uruchomić skrypt jako.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie **nxScript** zasobów do wykonania dodatkowych czynności konfiguracyjnych zarządzania.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```