---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Zasób DSC dla nxScript systemu Linux
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372163"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Zasób DSC dla nxScript systemu Linux

Zasób **nxScript** w konfiguracji żądanego stanu (DSC) programu PowerShell zapewnia mechanizm uruchamiania skryptów systemu Linux w węźle z systemem Linux.

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
| GetScript| Zapewnia skrypt do zwrócenia bieżącego stanu maszyny.  Ten skrypt jest uruchamiany po wywołaniu skryptu [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) . Skrypt musi rozpoczynać się od Shebang, na przykład #!/bin/bash.|
| Setscript| Zapewnia skrypt, który umieszcza maszynę w poprawnym stanie. Po wywołaniu skryptu [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , **TestScript** działa najpierw. Jeśli blok **TestScript** zwraca kod zakończenia inny niż 0, zostanie uruchomiony blok **setscript** . Jeśli **TestScript** zwraca kod zakończenia 0, setscript nie zostanie  uruchomiony. Skrypt musi rozpoczynać się od Shebang, `#!/bin/bash`na przykład.|
| TestScript| Zawiera skrypt, który sprawdza, czy węzeł jest aktualnie w odpowiednim stanie. Po wywołaniu skryptu [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) ten skrypt jest uruchamiany. Jeśli zwraca kod zakończenia inny niż 0, zostanie uruchomiony setscript. Jeśli zwraca kod zakończenia 0, setscript nie zostanie  uruchomiony. **TestScript** jest również uruchamiany po wywołaniu skryptu [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) . Jednak w tym przypadku setscript nie  zostanie uruchomiony, niezależnie od tego, jaki kod zakończenia jest zwracany z **TestScript**. **TestScript** musi zawierać zawartość i musi zwracać kod zakończenia 0, jeśli rzeczywista konfiguracja jest zgodna z bieżącą konfiguracją żądanego stanu, a kod zakończenia inny niż 0, jeśli jest niezgodny. (Bieżąca Konfiguracja żądanego stanu to Ostatnia konfiguracja wdrożona w węźle, który korzysta z DSC). Skrypt musi rozpoczynać się od elementu Shebang, takiego jak 1 #!/bin/bash.1|
| Użytkownik| Użytkownik uruchamiający skrypt jako.|
| Grupa| Grupa, w której ma zostać uruchomiony skrypt.|
| DependsOn | Wskazuje, że konfiguracja innego zasobu musi być uruchomiona przed skonfigurowaniem tego zasobu. Na przykład, jeśli **Identyfikator** bloku skryptu konfiguracji zasobu, który ma zostać uruchomiony jako pierwszy jest resourceName, a jego typ to ResourceType, Składnia służąca do użycia tej `DependsOn = "[ResourceType]ResourceName"`właściwości to.|

## <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie zasobu **nxScript** do wykonania dodatkowego zarządzania konfiguracją.

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
