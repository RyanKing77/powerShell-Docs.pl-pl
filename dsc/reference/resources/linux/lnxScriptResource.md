---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux nxScript zasobów
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048401"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC dla systemu Linux nxScript zasobów

**NxScript** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do uruchamiania skryptów systemu Linux w węźle systemu Linux.

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
| GetScript| Zawiera skrypt, który jest uruchamiany, gdy wywołujesz [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet. Skrypt musi zaczynać się od shebang, takich jak #! / bin/powłoki bash.|
| SetScript| Zawiera skrypt. Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** działa jako pierwszy. Jeśli **TestScript** bloku zwraca kod zakończenia różny od 0, **SetScript** blok zostanie uruchomiony. Jeśli **TestScript** zwraca kod zakończenia 0, **SetScript** nie będzie działać. Skrypt musi zaczynać się od shebang, takich jak `#!/bin/bash`.|
| TestScript| Zawiera skrypt. Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, ten skrypt jest uruchamiany. Jeśli zwróci ona kod zakończenia różny od 0, SetScript zostanie uruchomiony. Jeśli zwróci ona kod zakończenia 0, **SetScript** nie będzie działać. **TestScript** również jest uruchamiany, gdy wywołujesz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet. Jednak w tym przypadku **SetScript** nie będzie działać niezależnie od tego, jaki kod zakończenia jest zwracana z **TestScript**. **TestScript** musi zwracać kod zakończenia 0, jeśli rzeczywistą konfigurację odpowiada bieżącej konfiguracji żądanego stanu, a wyjście kodu inne niż 0, jeśli nie jest zgodny. (Ostatnia konfiguracja wdrożonymi na węzeł, który używa DSC jest bieżąca konfiguracja żądanego stanu). Skrypt musi zaczynać się od shebang, na przykład 1#!/bin/bash.1|
| Użytkownik| Użytkownik do uruchomienia skryptu jako.|
| Grupa| Grupa, aby uruchomić skrypt jako.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie **nxScript** zasobów do wykonania dodatkowych funkcji zarządzania konfiguracją.

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