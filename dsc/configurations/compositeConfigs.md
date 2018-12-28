---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zagnieżdżanie konfiguracji
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404742"
---
# <a name="nesting-dsc-configurations"></a>Zagnieżdżanie konfiguracji DSC

Konfiguracja zagnieżdżonych (nazywane również konfiguracji złożonej) jest konfiguracji, która jest wywoływana w innej konfiguracji, tak jakby zasobu.
Obie konfiguracje musi być zdefiniowany w tym samym pliku.

Spójrzmy na przykład:

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

W tym przykładzie `FileConfig` przyjmuje dwa parametry obowiązkowe, **copyfrom —** i **CopyTo**, które są używane jako wartości **Ścieżka_źródłowa** i  **Ścieżka_docelowa** właściwości `File` bloku zasobów.
`NestedConfig` Wywołania konfiguracji `FileConfig` tak, jakby był to zasób.
Właściwości w `NestedConfig` bloku zasobów (**copyfrom —** i **CopyTo**) są parametrami `FileConfig` konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Zasoby złożone — przy użyciu konfiguracji DSC jako zasób](../resources/authoringResourceComposite.md)