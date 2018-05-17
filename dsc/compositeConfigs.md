---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zagnieżdżanie konfiguracji
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="nesting-dsc-configurations"></a>Zagnieżdżania konfiguracji DSC

Konfiguracja zagnieżdżonych (nazywanych również konfiguracji złożonej) jest konfigurację, która jest wywoływana w innej konfiguracji, tak jakby był on zasobu.
Obie konfiguracje muszą być zdefiniowane w tym samym pliku.

Oto prosty przykład:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

W tym przykładzie `FileConfig` przyjmuje dwa parametry obowiązkowe, **CopyFrom** i **CopyTo**, które są używane jako wartości **Ścieżka_źródłowa** i  **Ścieżka_docelowa** właściwości w `File` bloku zasobów.
`NestedConfig` Wywołania konfiguracji `FileConfig` tak, jakby była zasobu.
Właściwości w `NestedConfig` bloku zasobów (**CopyFrom** i **CopyTo**) są parametry `FileConfig` konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Złożone zasobów — za pomocą konfiguracji DSC jako zasób](authoringResourceComposite.md)