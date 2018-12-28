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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="46576-103">Zagnieżdżanie konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="46576-103">Nesting DSC configurations</span></span>

<span data-ttu-id="46576-104">Konfiguracja zagnieżdżonych (nazywane również konfiguracji złożonej) jest konfiguracji, która jest wywoływana w innej konfiguracji, tak jakby zasobu.</span><span class="sxs-lookup"><span data-stu-id="46576-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="46576-105">Obie konfiguracje musi być zdefiniowany w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="46576-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="46576-106">Spójrzmy na przykład:</span><span class="sxs-lookup"><span data-stu-id="46576-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="46576-107">W tym przykładzie `FileConfig` przyjmuje dwa parametry obowiązkowe, **copyfrom —** i **CopyTo**, które są używane jako wartości **Ścieżka_źródłowa** i  **Ścieżka_docelowa** właściwości `File` bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="46576-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="46576-108">`NestedConfig` Wywołania konfiguracji `FileConfig` tak, jakby był to zasób.</span><span class="sxs-lookup"><span data-stu-id="46576-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="46576-109">Właściwości w `NestedConfig` bloku zasobów (**copyfrom —** i **CopyTo**) są parametrami `FileConfig` konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="46576-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="46576-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46576-110">See Also</span></span>

- [<span data-ttu-id="46576-111">Zasoby złożone — przy użyciu konfiguracji DSC jako zasób</span><span class="sxs-lookup"><span data-stu-id="46576-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)