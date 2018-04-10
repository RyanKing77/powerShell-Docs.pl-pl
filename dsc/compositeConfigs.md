---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zagnieżdżanie konfiguracji
ms.openlocfilehash: 9c6dbce462f7481e5714039a95ae85f85be0072e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="af6fe-103">Zagnieżdżania konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="af6fe-103">Nesting DSC configurations</span></span>

<span data-ttu-id="af6fe-104">Konfiguracja zagnieżdżonych (nazywanych również konfiguracji złożonej) jest konfigurację, która jest wywoływana w innej konfiguracji, tak jakby był on zasobu.</span><span class="sxs-lookup"><span data-stu-id="af6fe-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="af6fe-105">Obie konfiguracje muszą być zdefiniowane w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="af6fe-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="af6fe-106">Oto prosty przykład:</span><span class="sxs-lookup"><span data-stu-id="af6fe-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="af6fe-107">W tym przykładzie `FileConfig` przyjmuje dwa parametry obowiązkowe, **CopyFrom** i **CopyTo**, które są używane jako wartości **Ścieżka_źródłowa** i  **Ścieżka_docelowa** właściwości w `File` bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="af6fe-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="af6fe-108">`NestedConfig` Wywołania konfiguracji `FileConfig` tak, jakby była zasobu.</span><span class="sxs-lookup"><span data-stu-id="af6fe-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="af6fe-109">Właściwości w `NestedConfig` bloku zasobów (**CopyFrom** i **CopyTo**) są parametry `FileConfig` konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="af6fe-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="af6fe-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af6fe-110">See Also</span></span>

- [<span data-ttu-id="af6fe-111">Złożone zasobów — za pomocą konfiguracji DSC jako zasób</span><span class="sxs-lookup"><span data-stu-id="af6fe-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)